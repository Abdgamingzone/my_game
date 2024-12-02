<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FlyJet Login</title>
    <style>
        /* General Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Poppins', sans-serif;
            height: 100vh;
            background: url('C:/Users/DELL/OneDrive/Desktop/My Game/Assets/Images/login bg pic.jpg') no-repeat center center/cover;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }
        /* Overlay for Contrast */
        body::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            z-index: 1;
        }
        .container {
            position: relative;
            z-index: 2;
            text-align: center;
        }
        /* Game Title */
        h1 {
            font-size: 3.5rem;
            font-family: 'Orbitron', sans-serif;
            color: #00c8ff;
            text-shadow: 0 0 15px #00c8ff, 0 0 30px #0077aa;
            animation: glow 1.5s infinite alternate;
        }
        @keyframes glow {
            from {
                text-shadow: 0 0 10px #00c8ff, 0 0 20px #0077aa;
            }
            to {
                text-shadow: 0 0 20px #00c8ff, 0 0 40px #0077aa;
            }
        }
        p {
            font-size: 1.2rem;
            color: #ddd;
            margin-bottom: 20px;
        }
        /* Login Box */
        .login-box {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(10px);
            width: 300px;
            margin: auto;
        }
        .login-box input {
            width: 100%;
            padding: 10px;
            margin: 15px 0;
            border: none;
            border-radius: 5px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            font-size: 1rem;
            outline: none;
        }
        .login-box input::placeholder {
            color: #aaa;
        }
        /* Buttons */
        .login-box button {
            width: 100%;
            padding: 10px;
            background: linear-gradient(90deg, #00c8ff, #0077aa);
            border: none;
            border-radius: 5px;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .login-box button:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px #00c8ff;
        }
        .login-box a {
            color: #00c8ff;
            text-decoration: none;
            font-size: 0.9rem;
        }
        .login-box a:hover {
            text-decoration: underline;
        }

        /* Media Queries for Responsiveness */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            .login-box {
                width: 80%;
                padding: 20px;
            }
            .login-box input, .login-box button {
                font-size: 1rem;
            }
        }

        @media (max-width: 480px) {
            h1 {
                font-size: 2rem;
            }
            .login-box {
                width: 90%;
                padding: 15px;
            }
            .login-box input, .login-box button {
                font-size: 0.9rem;
            }
        }


    </style>
</head>
<body>

    <div class="container">
        <h1>FlyJet</h1>
        
        <div class="login-box">
            <form id="loginForm">
                <input type="text" id="userID" placeholder="Enter your Player ID" required>
                <input type="password" id="userPassword" placeholder="Enter your Password" required>
                <button type="submit">Sign in</button>
                <p id="errorMessage" style="color: red; margin-top: 10px; display: none;">Invalid Player ID or Password.</p>
            </form>
        </div>
    </div>

    <!-- <a href="game.html"></a> -->




    <!-- Optional Audio -->
     <audio id="backgroundMusic" loop>
        <source src="C:/Users/DELL/OneDrive/Desktop/My Game/Assets/Music/login_bg_music.mp3" type="audio/mpeg">
    </audio> 




   <script>
    // Hardcoded valid user database
    const validUsers = [
        { userID: "Player12", password: "445566" },
        { userID: "Player14", password: "445566" },
    ];

    const backgroundMusic = document.getElementById('backgroundMusic');

    // Start the background music after user interaction
    document.body.addEventListener('click', function () {
        if (backgroundMusic && backgroundMusic.paused) {
            backgroundMusic.play().catch((error) => {
                console.error('Error playing audio:', error);
            });
        }
    });

    // Handle the login form submission
    document.getElementById('loginForm').addEventListener('submit', function (event) {
        event.preventDefault();

        // Get user input values
        const userID = document.getElementById('userID').value.trim();
        const userPassword = document.getElementById('userPassword').value.trim();
        const errorMessage = document.getElementById('errorMessage');

        // Validate the credentials
        const isValidUser = validUsers.some(user => user.userID === userID && user.password === userPassword);

        if (isValidUser) {
            // Redirect to the game page if credentials are valid
            errorMessage.style.display = "none"; // Hide error message
            window.location.href = "C:/Users/DELL/OneDrive/Desktop/flyjet 2/game 1.html";
        } else {
            // Show the error message if credentials are invalid
            errorMessage.style.display = "block";
        }
    });

   

</script>

</body>
</html>





