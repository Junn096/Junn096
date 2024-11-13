- 👋 Hi, I’m @Junn096
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Junn096/Junn096 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Flask and JavaScript App</title>
</head>
<body>
    <h1>Welcome to My Website</h1>
    <button onclick="fetchMessage()">Get Message from Python Backend</button>
    <p id="message"></p>

    <script>
        async function fetchMessage() {
            try {
                const response = await fetch('http://127.0.0.1:5000/message');
                const data = await response.json();
                document.getElementById('message').textContent = data.message;
            } catch (error) {
                console.error('Error fetching data:', error);
            }
        }
    </script>
</body>
</html>