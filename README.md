
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
from flask import Flask, jsonify
from flask_cors import CORS

app = Flask(__name__)
CORS(app)  # Enable Cross-Origin Resource Sharing for local testing

@app.route('/message')
def get_message():
    return jsonify(message="Hello from the Python backend!")

if __name__ == '__main__':
    app.run(debug=True)
    pip install Flask
    python app.py
    
