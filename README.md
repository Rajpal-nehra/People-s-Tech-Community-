<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>People's Tech Community</title>
  <link rel="stylesheet" href="styles.css"/>
</head>
<body>

  <!-- Hero Banner -->
  <header class="hero-banner">
    <img src="images/banner.jpg" alt="Banner" />
    <div class="search-bar">
      <input type="text" placeholder="Search...">
      <button>📅</button>
    </div>
  </header>

  <!-- Feature Icons -->
  <section class="features">
    <div class="feature"><img src="images/gtclub.png" alt=""><p>GT Club</p></div>
    <div class="feature"><img src="images/snapzone.png" alt=""><p>Snapzone</p></div>
    <div class="feature"><img src="images/ui.png" alt=""><p>realme UI</p></div>
    <div class="feature"><img src="images/checkin.png" alt=""><p>Check in</p></div>
  </section>

  <!-- Posts Section -->
  <section class="posts">
    <div class="post">
      <img src="images/post1.jpg" alt="Post 1">
      <h3>Silence Redefined: realme Buds Air 7 Pro</h3>
      <p>1241 Views</p>
    </div>
    <div class="post">
      <img src="images/post2.jpg" alt="Post 2">
      <h3>realme GT 7 Hands-On: Flagship Experience</h3>
      <p>2034 Views</p>
    </div>
  </section>

</body>
</html>
body {
  font-family: sans-serif;
  margin: 0;
  padding: 0;
  background: #f9f9f9;
}

.hero-banner {
  position: relative;
  text-align: center;
  background: #fff;
  padding-bottom: 10px;
}

.hero-banner img {
  width: 100%;
  max-height: 200px;
  object-fit: cover;
}

.search-bar {
  display: flex;
  justify-content: center;
  margin-top: 10px;
  gap: 5px;
}

.search-bar input {
  padding: 10px;
  width: 60%;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.search-bar button {
  padding: 10px;
  border: none;
  background: #007bff;
  color: white;
  border-radius: 4px;
  cursor: pointer;
}

.features {
  display: flex;
  justify-content: space-around;
  background: #fff;
  padding: 20px 10px;
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
}

.feature {
  text-align: center;
}

.feature img {
  width: 50px;
  height: 50px;
  margin-bottom: 5px;
}

.posts {
  padding: 15px;
}

.post {
  background: white;
  margin-bottom: 20px;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}

.post img {
  width: 100%;
  height: auto;
  display: block;
}

.post h3 {
  padding: 10px;
  margin: 0;
  font-size: 18px;
}

.post p {
  padding: 0 10px 10px;
  color: gray;
  font-size: 14px;
}
