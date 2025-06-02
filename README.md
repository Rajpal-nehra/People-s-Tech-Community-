<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Create Post</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav class="navbar">
        <div class="nav-container">
            <div class="nav-logo">
                <h2>Community Hub</h2>
            </div>
            <ul class="nav-menu">
                <li><a href="index.html" class="nav-link">Home</a></li>
                <li><a href="post.html" class="nav-link active">Create Post</a></li>
                <li><a href="chat.html" class="nav-link">Chat</a></li>
                <li><a href="login.html" class="nav-link">Login</a></li>
                <li><a href="admin.html" class="nav-link">Admin</a></li>
            </ul>
        </div>
    </nav>

    <main class="post-container">
        <h1>Create a New Post</h1>
        <button onclick="insertImage()">Insert Image</button>
        <button onclick="insertPoll()">Insert Poll</button>
        <textarea id="post-content" rows="10" cols="50"></textarea>
    </main>

    <script>
        function insertImage() {
            const imageInput = document.createElement('input');
            imageInput.type = 'file';
            imageInput.accept = 'image/*';
            imageInput.style.display = 'none';
            
            imageInput.addEventListener('change', function(e) {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        const imageMarkup = `\n![${file.name}](${e.target.result})\n`;
                        insertAtCursor(document.getElementById('post-content'), imageMarkup);
                    };
                    reader.readAsDataURL(file);
                }
            });
            
            document.body.appendChild(imageInput);
            imageInput.click();
            document.body.removeChild(imageInput);
        }

        function insertPoll() {
            const pollQuestion = prompt('Enter your poll question:');
            if (!pollQuestion) return;

            const options = [];
            for (let i = 1; i <= 4; i++) {
                const option = prompt(`Enter option ${i} (leave empty to stop):`);
                if (!option) break;
                options.push(option);
            }

            if (options.length < 2) {
                alert('Poll needs at least 2 options');
                return;
            }

            const pollMarkup = `\n\n**Poll: ${pollQuestion}**\n${options.map((opt, idx) => `${idx + 1}. ${opt}`).join('\n')}\n\n`;
            insertAtCursor(document.getElementById('post-content'), pollMarkup);
        }

        function insertAtCursor(myField, myValue) {
            const start = myField.selectionStart;
            const end = myField.selectionEnd;
            myField.value = myField.value.substring(0, start) + myValue + myField.value.substring(end);
        }
    </script>
</body>
</html>
