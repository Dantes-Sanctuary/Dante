<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dante Vazey</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            background: #f5f5f5;
            color: #333;
        }
        header {
            background: #333;
            color: #fff;
            padding: 1em 0;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        header h1 {
            margin: 0;
            font-size: 2em;
        }
        nav {
            display: flex;
            justify-content: center;
            gap: 1em;
        }
        nav a {
            color: #fff;
            text-decoration: none;
            padding: 0.5em 1em;
            transition: background 0.3s;
        }
        nav a:hover {
            background: #575757;
            border-radius: 5px;
        }
        main {
            padding: 2em;
            max-width: 800px;
            margin: auto;
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        section {
            margin-bottom: 2em;
        }
        footer {
            text-align: center;
            padding: 1em 0;
            background: #333;
            color: #fff;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
        .hidden {
            display: none;
        }
        .fade-in {
            animation: fadeIn 1s;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .blog {
            max-width: 800px;
            margin: auto;
        }
        .blog h2 {
            text-align: center;
        }
        .blog form {
            display: flex;
            flex-direction: column;
            gap: 1em;
        }
        .blog form textarea {
            resize: vertical;
            min-height: 100px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Dante Vazey</h1>
        <nav>
            <a href="#" onclick="showSection('main')">Home</a>
            <a href="#" onclick="showSection('blog')">Blog</a>
        </nav>
    </header>
    <main id="main" class="fade-in">
        <section>
            <h2>About Me</h2>
            <p>I am Dante Vazey, a musician, philosopher, writer, and horror actor. I thrive on creativity and intellectual pursuits, blending my passions to create unique and engaging experiences. Welcome to my personal webpage!</p>
        </section>
    </main>
    <main id="blog" class="hidden">
        <section class="blog">
            <h2>Blog</h2>
            <form id="blog-form" onsubmit="return addBlogPost()">
                <input type="text" id="title" placeholder="Title" required>
                <textarea id="content" placeholder="Your content here..." required></textarea>
                <button type="submit">Add Post</button>
            </form>
            <div id="posts"></div>
        </section>
    </main>
    <footer>
        &copy; 2024 Dante Vazey
    </footer>
    <script>
        function showSection(sectionId) {
            document.querySelectorAll('main').forEach(section => {
                section.classList.add('hidden');
                section.classList.remove('fade-in');
            });
            const section = document.getElementById(sectionId);
            section.classList.remove('hidden');
            section.classList.add('fade-in');
        }

        function addBlogPost() {
            const title = document.getElementById('title').value;
            const content = document.getElementById('content').value;

            const post = document.createElement('div');
            post.innerHTML = `<h3>${title}</h3><p>${content}</p>`;
            document.getElementById('posts').appendChild(post);

            document.getElementById('blog-form').reset();
            return false;
        }
    </script>
</body>
</html>