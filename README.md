<!-- Snippet from post.html -->
<button onclick="insertImage()">Insert Image</button>
<button onclick="insertPoll()">Insert Poll</button>
<textarea id="post-content" rows="10" cols="50"></textarea>

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
        const pollBuilder = document.createElement('div');
        const pollQuestion = prompt('Enter your poll question:');
        if (!pollQuestion) return;
        
        let options = "";
        for (let i = 1; i <= 4; i++) {
            const option = prompt(`Enter option ${i} (leave empty to stop):`);
            if (!option) break;
            options += `${option}\n`;
        }
        
        if (options.split('\n').filter(Boolean).length < 2) {
            alert('Poll needs at least 2 options');
            return;
        }

        const pollMarkup = `\n\n**Poll: ${pollQuestion}**\n${options}\n\n`;
        insertAtCursor(document.getElementById('post-content'), pollMarkup);
    }

    function insertAtCursor(myField, myValue) {
        const start = myField.selectionStart;
        const end = myField.selectionEnd;
        myField.value = myField.value.substring(0, start) + myValue + myField.value.substring(end);
    }
</script>
