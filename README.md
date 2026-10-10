<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kalkulator Miłości</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@400;600&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 99%, #fecfef 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            text-shadow: 2px 2px 4px rgba(255, 255, 255, 0.5);
        }

        .heart-container {
            position: relative;
            width: 250px;
            height: 250px;
            display: flex;
            justify-content: center;
            align-items: center;
            animation: heartbeat 1.5s infinite;
            filter: drop-shadow(0 15px 25px rgba(220, 38, 38, 0.4));
        }

        .heart-svg {
            width: 100%;
            height: 100%;
            fill: #ef4444; /* Tailwind red-500 */
        }

        .percentage-text {
            position: absolute;
            font-size: 4rem;
            font-weight: bold;
            color: white;
            z-index: 10;
            text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.3);
            margin-top: -15px; /* Slight adjustment to center visually in the heart */
        }

        @keyframes heartbeat {
            0% { transform: scale(1); }
            15% { transform: scale(1.1); }
            30% { transform: scale(1); }
            45% { transform: scale(1.1); }
            60% { transform: scale(1); }
            100% { transform: scale(1); }
        }

        .input-group input {
            transition: all 0.3s ease;
        }
        
        .input-group input:focus {
            transform: scale(1.05);
            outline: none;
            box-shadow: 0 0 15px rgba(239, 68, 68, 0.4);
        }

        /* Floating background hearts */
        .bg-heart {
            position: absolute;
            fill: rgba(255, 255, 255, 0.3);
            animation: floatup 6s infinite linear;
            z-index: -1;
        }

        @keyframes floatup {
            0% { transform: translateY(100vh) scale(0.5) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-20vh) scale(1.2) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body class="relative">

    <!-- Floating background hearts for romantic effect -->
    <svg class="bg-heart" style="left: 10%; animation-duration: 7s; animation-delay: 1s;" width="50" viewBox="0 0 24 24"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>
    <svg class="bg-heart" style="left: 80%; animation-duration: 5s; animation-delay: 0s;" width="40" viewBox="0 0 24 24"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>
    <svg class="bg-heart" style="left: 40%; animation-duration: 8s; animation-delay: 3s;" width="60" viewBox="0 0 24 24"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>

    <div class="z-10 bg-white/40 backdrop-blur-md p-8 md:p-12 rounded-3xl shadow-2xl max-w-4xl w-full mx-4 border border-white/50">
        
        <h1 class="text-5xl md:text-6xl text-red-600 text-center mb-10">Kalkulator Miłości</h1>

        <div class="flex flex-col md:flex-row items-center justify-between gap-8 mb-12">
            
            <!-- Left Input: Female Name -->
            <div class="input-group w-full md:w-1/3 flex flex-col items-center">
                <label for="femaleName" class="text-pink-600 font-semibold mb-2 text-lg">Imię partnerki</label>
                <input type="text" id="femaleName" class="w-full text-center px-4 py-3 rounded-full border-2 border-pink-300 focus:border-red-500 text-gray-700 text-xl font-medium shadow-inner" placeholder="Wpisz imię">
            </div>

            <!-- Center: Big Heart -->
            <div class="heart-container mx-auto">
                <svg viewBox="0 0 24 24" class="heart-svg">
                    <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
                </svg>
                <span id="counterText" class="percentage-text">0%</span>
            </div>

            <!-- Right Input: Male Name -->
            <div class="input-group w-full md:w-1/3 flex flex-col items-center">
                <label for="maleName" class="text-blue-600 font-semibold mb-2 text-lg">Imię partnera</label>
                <input type="text" id="maleName" class="w-full text-center px-4 py-3 rounded-full border-2 border-blue-300 focus:border-blue-500 text-gray-700 text-xl font-medium shadow-inner" placeholder="Wpisz imię">
            </div>
        </div>

        <div class="text-center">
            <button id="calculateBtn" class="bg-gradient-to-r from-red-500 to-pink-500 hover:from-red-600 hover:to-pink-600 text-white text-xl font-bold py-4 px-10 rounded-full shadow-lg transform transition hover:scale-105 active:scale-95 focus:outline-none focus:ring-4 focus:ring-red-300">
                Oblicz miłość
            </button>
        </div>
        
        <p id="message" class="text-center mt-6 text-xl font-semibold text-gray-800 h-8 opacity-0 transition-opacity duration-500"></p>
    </div>

    <script>
        const calculateBtn = document.getElementById('calculateBtn');
        const femaleInput = document.getElementById('femaleName');
        const maleInput = document.getElementById('maleName');
        const counterText = document.getElementById('counterText');
        const messageBox = document.getElementById('message');
        
        let isAnimating = false;

        calculateBtn.addEventListener('click', () => {
            if (isAnimating) return;
            
            const femaleName = femaleInput.value.trim().toLowerCase();
            const maleName = maleInput.value.trim().toLowerCase();

            if (!femaleName || !maleName) {
                showMessage("Proszę wpisać oba imiona! 💕", "text-red-500");
                return;
            }

            let targetPercentage = 0;
            let resultMessage = "";

            // Specjalny warunek dla Eweliny i Michała
            if (femaleName === 'ewelina' && maleName === 'michał' || femaleName === 'ewelina' && maleName === 'michal') {
                targetPercentage = 100;
                resultMessage = "Przeznaczeni dla siebie! Idealne dopasowanie! Ale cacyyyy 💖";
            } else {
                // Dla innych imion losowy procent od 10 do 99
                targetPercentage = Math.floor(Math.random() * 90) + 10;
                
                if(targetPercentage > 85) resultMessage = "Wspaniała para! Gorące uczucie! 🔥";
                else if(targetPercentage > 50) resultMessage = "Macie duży potencjał! Warto pielęgnować tę relację. 😊";
                else resultMessage = "Może warto się lepiej poznać? 😉";
            }

            animateCounter(targetPercentage, resultMessage);
        });

        function animateCounter(target, finalMessage) {
            isAnimating = true;
            let current = 0;
            messageBox.style.opacity = '0';
            
            const duration = 2000; // 2 seconds animation
            const interval = 20; 
            const steps = duration / interval;
            const increment = target / steps;

            const timer = setInterval(() => {
                current += increment;
                if (current >= target) {
                    current = target;
                    clearInterval(timer);
                    isAnimating = false;
                    showMessage(finalMessage, "text-gray-800");
                }
                counterText.innerText = Math.floor(current) + '%';
            }, interval);
        }

        function showMessage(msg, colorClass) {
            messageBox.innerText = msg;
            messageBox.className = `text-center mt-6 text-xl font-semibold h-8 transition-opacity duration-500 ${colorClass}`;
            messageBox.style.opacity = '1';
        }
    </script>
</body>
</html>
