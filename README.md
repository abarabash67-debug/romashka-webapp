cat > /root/bot/webapp/index.html << 'EOF'
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ромашка — Анкеты</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: var(--tg-theme-bg-color, #ffffff);
            color: var(--tg-theme-text-color, #000000);
            padding: 16px;
            margin: 0;
        }
        .card {
            background: var(--tg-theme-secondary-bg-color, #f0f0f0);
            border-radius: 16px;
            padding: 16px;
            margin-bottom: 16px;
            cursor: pointer;
            transition: opacity 0.2s;
        }
        .card:active {
            opacity: 0.7;
        }
        .price {
            color: var(--tg-theme-button-color, #2481cc);
            font-weight: bold;
            font-size: 18px;
            margin-top: 8px;
        }
        button {
            background: var(--tg-theme-button-color, #2481cc);
            color: var(--tg-theme-button-text-color, #ffffff);
            border: none;
            padding: 12px 24px;
            border-radius: 12px;
            font-size: 16px;
            width: 100%;
            margin-top: 12px;
        }
    </style>
</head>
<body>
    <h1>🌸 Анкеты девушек</h1>
    <div id="rooms"></div>

    <script>
        const tg = window.Telegram.WebApp;
        tg.ready();
        tg.expand();

        function buyRoom(id) {
            tg.openTelegramLink("https://t.me_" + id);
            tg.close();
        }

        // ВРЕМЕННЫЕ ДЕМО-ДАННЫЕ (заменишь на реальные из БД позже)
        const demoRooms = [
            { id: 123, name: "Мария, 23 года", city: "Москва", price: 100 },
            { id: 456, name: "Анна, 25 лет", city: "СПб", price: 150 },
            { id: 789, name: "Елена, 22 года", city: "Казань", price: 80 }
        ];

        function render() {
            const html = demoRooms.map(room => `
                <div class="card" onclick="buyRoom(${room.id})">
                    <h3>📸 ${room.name}</h3>
                    <p>${room.city}</p>
                    <div class="price">⭐ ${room.price}</div>
                    <button>🔥 Снять блюр и познакомиться</button>
                </div>
            `).join('');
            document.getElementById('rooms').innerHTML = html;
        }

        render();
    </script>
</body>
</html>
EOF
