<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kod Üretme ve Listeleme</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 40px;
        }
        input, button {
            padding: 10px;
            font-size: 16px;
            margin: 5px;
        }
        #codeSection {
            display: none;
        }
        #codeList {
            margin-top: 20px;
            list-style-type: none;
        }
    </style>
</head>
<body>
    <h2>Şifreyi Girin</h2>
    <input type="text" id="password" placeholder="Şifrenizi girin" />
    <button onclick="verifyPassword()">Doğrula</button>

    <div id="codeSection">
        <h3>Kod Üretme ve Listeleme</h3>
        <button onclick="generateCode()">Kod Üret</button>
        <ul id="codeList"></ul>
    </div>

    <script>
        const validPassword = "263826Ayt";  // Şifreyi burada belirliyoruz
        const codes = [];

        function verifyPassword() {
            const enteredPassword = document.getElementById('password').value;
            if (enteredPassword === validPassword) {
                document.getElementById('codeSection').style.display = "block";
                alert("Şifre doğrulandı! Artık kodları üretebilirsiniz.");
            } else {
                alert("Geçersiz şifre! Lütfen tekrar deneyin.");
            }
        }

        function generateCode() {
            const code = generateRandomCode();
            codes.push(code);
            displayCodes();
        }

        function generateRandomCode() {
            const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            let result = '';
            const length = 10;
            for (let i = 0; i < length; i++) {
                const randomIndex = Math.floor(Math.random() * characters.length);
                result += characters[randomIndex];
            }
            return result;
        }

        function displayCodes() {
            const codeListElement = document.getElementById('codeList');
            codeListElement.innerHTML = '';  // Önceki kodları temizle
            codes.forEach(code => {
                const li = document.createElement('li');
                li.textContent = code;
                codeListElement.appendChild(li);
            });
        }
    </script>
</body>
</html>
