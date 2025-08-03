<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Jean's Study Hub - Admin Panel</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background-color: #f4f4f4;
    }

    header {
      background-color: #007bff;
      color: white;
      padding: 15px;
      text-align: center;
    }

    .container {
      max-width: 900px;
      margin: 20px auto;
      background: white;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 0 8px rgba(0, 0, 0, 0.1);
    }

    #admin-section {
      display: none;
    }

    input, textarea {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
    }

    button {
      padding: 10px 20px;
      background-color: #007bff;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }

    .ebook {
      background: #eee;
      padding: 15px;
      margin: 10px 0;
      border-radius: 5px;
    }

    .ebook a {
      color: #007bff;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <header>
    <h1>Jean's Study Hub</h1>
    <p>Admin Control Panel</p>
  </header>

  <div class="container" id="login-section">
    <h2>Admin Login</h2>
    <input type="password" id="admin-password" placeholder="Enter Admin Password">
    <button onclick="login()">Login</button>
  </div>

  <div class="container" id="admin-section">
    <h2>Upload New eBook</h2>
    <input type="text" id="ebook-title" placeholder="Enter Book Title">
    <input type="url" id="ebook-link" placeholder="Enter Book Download Link">
    <button onclick="addEbook()">Add eBook</button>

    <h3>Uploaded Books</h3>
    <div id="ebook-list"></div>
  </div>

  <script>
    const PASSWORD = "12345"; // You can change this admin password
    const ebookList = [];

    function login() {
      const entered = document.getElementById("admin-password").value;
      if (entered === PASSWORD) {
        document.getElementById("login-section").style.display = "none";
        document.getElementById("admin-section").style.display = "block";
      } else {
        alert("Incorrect password!");
      }
    }

    function addEbook() {
      const title = document.getElementById("ebook-title").value;
      const link = document.getElementById("ebook-link").value;

      if (title && link) {
        const ebookHTML = `<div class="ebook"><strong>${title}</strong><br><a href="${link}" target="_blank">📘 Download</a></div>`;
        document.getElementById("ebook-list").innerHTML += ebookHTML;
        document.getElementById("ebook-title").value = "";
        document.getElementById("ebook-link").value = "";
      } else {
        alert("Please enter both title and link.");
      }
    }
  </script>
</body>
</html>
