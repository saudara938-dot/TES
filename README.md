<!DOCTYPE html>
<html lang="id">
<head>
    <title>Latihan Login (Simulasi)</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&display=swap" rel="stylesheet">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <style>
        /* CSS Lengkap untuk Tema Hacker */
        @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=VT323&display=swap');

        :root {
            --primary-color: #00ff6a;
            --dark-bg: #0a0a10;
            --dark-glass: rgba(0, 40, 10, 0.4);
            --border-color: rgba(0, 255, 106, 0.5);
            --error-color: #ff3232;
            --success-color: #00ff6a; /* Warna sukses, sama dgn primary */
        }

        body {
            font-family: 'Share Tech Mono', monospace;
            background-color: var(--dark-bg);
            color: var(--primary-color);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }

        body::before {
            content: "";
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: repeating-linear-gradient(
                0deg,
                rgba(0, 0, 0, 0.2) 0px,
                rgba(0, 0, 0, 0.2) 1px,
                transparent 1px,
                transparent 3px
            );
            pointer-events: none;
            z-index: 1;
        }

        .login-container {
            background: var(--dark-glass);
            border: 1px solid var(--border-color);
            padding: 2.5rem;
            border-radius: 8px;
            box-shadow: 0 0 35px rgba(0, 255, 106, 0.15);
            width: 350px;
            max-width: 90%;
            text-align: center;
            position: relative;
            z-index: 2;
        }

        .login-container h2 {
            font-family: 'VT323', monospace;
            font-size: 2.5rem;
            margin: 0 0 20px 0;
            text-shadow: 0 0 8px var(--primary-color);
        }

        .login-container h2::after {
            content: '_';
            animation: blink-caret 1.1s step-end infinite;
            margin-left: 5px;
        }

        @keyframes blink-caret {
            from, to { opacity: 1; }
            50% { opacity: 0; }
        }

        .input-group {
            position: relative;
            margin-bottom: 1.5rem;
        }

        .input-group i {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--primary-color);
            opacity: 0.7;
        }

        input[type="text"],
        input[type="password"] {
            width: calc(100% - 40px);
            padding: 12px 15px 12px 45px;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid var(--border-color);
            border-radius: 5px;
            color: var(--primary-color);
            font-family: 'Share Tech Mono', monospace;
            font-size: 1rem;
        }

        input[type="text"]:focus,
        input[type="password"]:focus {
            outline: none;
            box-shadow: 0 0 10px var(--primary-color);
            border-color: var(--primary-color);
        }

        ::placeholder {
            color: var(--primary-color);
            opacity: 0.5;
        }

        button {
            width: 100%;
            padding: 12px;
            background: var(--primary-color);
            color: var(--dark-bg);
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1.1rem;
            font-family: 'Share Tech Mono', monospace;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        button:hover {
            background: #fff;
            color: #000;
            box-shadow: 0 0 15px var(--primary-color);
        }

        /* INI PENTING: Untuk menampilkan pesan error/sukses */
        .message-box {
            padding: 10px;
            margin-top: 20px;
            border-radius: 5px;
            font-size: 0.9em;
            text-align: left;
            display: none; /* Sembunyi secara default */
        }
        
        .message-box.error {
            background: rgba(255, 50, 50, 0.1);
            border: 1px solid var(--error-color);
            color: var(--error-color);
            display: block; /* Tampilkan jika error */
        }
        
        .message-box.success {
            background: rgba(0, 255, 106, 0.1);
            border: 1px solid var(--success-color);
            color: var(--success-color);
            display: block; /* Tampilkan jika sukses */
        }

    </style>
</head>
<body>

    <form name="loginForm" onsubmit="return handleLogin()">
        
        <div class="login-container">
            <h2>//_LOGIN_PORTAL_</h2>

            <div class="input-group">
                <i class="fas fa-user-secret"></i>
                <input name="username" id="username" type="text" placeholder="USER_ID">
            </div>

            <div class="input-group">
                <i class="fas fa-key"></i>
                <input name="password" id="password" type="password" placeholder="PASSCODE">
            </div>

            <button type="submit">> INITIATE_ACCESS_</button>

            <div id="message-container"></div>
            
        </div>
    </form>

    <script>
        function handleLogin() {
            // 1. Ambil nilai dari input
            var usernameInput = document.getElementById("username").value;
            var passwordInput = document.getElementById("password").value;
            
            // 2. Ambil elemen kotak pesan
            var messageContainer = document.getElementById("message-container");

            // 3. Cek apakah username dan password BENAR
            if (usernameInput === "zaky" && passwordInput === "1234") {
                
                // JIKA BENAR: Tampilkan pesan sukses
                messageContainer.className = "message-box success"; // Terapkan CSS .success
                messageContainer.innerHTML = 
                    '<i class="fas fa-check-circle"></i> <strong>Akses Diberikan!</strong> <br>Anda akan terhubung selama 12 jam.';
                
            } else {
                
                // JIKA SALAH: Tampilkan pesan error
                messageContainer.className = "message-box error"; // Terapkan CSS .error
                messageContainer.innerHTML = 
                    '<i class="fas fa-exclamation-triangle"></i> <strong>Akses Ditolak!</strong> <br>USER_ID atau PASSCODE salah.';
            }

            // 4. Mencegah halaman me-refresh (penting untuk simulasi)
            return false;
        }
    </script>

</body>
</html>
