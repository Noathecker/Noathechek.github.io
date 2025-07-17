<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nhập Key và Lấy Link</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 50px;
        }
        .container {
            max-width: 500px;
            margin: auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background-color: #f9f9f9;
        }
        .input-group {
            margin-bottom: 20px;
        }
        input[type="text"] {
            padding: 10px;
            width: 200px;
            margin-right: 10px;
            font-size: 16px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
        }
        button:hover {
            background-color: #45a049;
        }
        #link {
            display: none;
            margin-top: 20px;
        }
        #message {
            color: red;
            margin-top: 10px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Nhập Key</h1>
    <div class="input-group">
        <input type="text" id="key" placeholder="Nhập key của bạn...">
        <button onclick="checkKey()">Kiểm Tra Key</button>
    </div>
    <div id="link">
        <p>Link để sao chép: <a href="https://link4m.com/4CEYEBa" target="_blank" id="generatedLink">https://link4m.com/4CEYEBa</a></p>
    </div>
    <div id="message"></div>
</div>

<script>
    const correctKey = 'your-correct-key'Key_1234;  // Thay đổi key đúng ở đây
    const redirectUrl = 'https://sites.google.com/view/cloudgamefree';
    const keyStorage = 'userKey';
    const expirationTime = 24 * 60 * 60 * 1000;  // 24 giờ tính bằng milliseconds

    function checkKey() {
        const userKey = document.getElementById('key').value;
        const messageElement = document.getElementById('message');
        const linkElement = document.getElementById('link');

        if (userKey === correctKey) {
            messageElement.textContent = '';
            linkElement.style.display = 'none';

            // Kiểm tra xem key có tồn tại trong storage và có hết hạn chưa
            const savedKey = localStorage.getItem(keyStorage);
            const savedTime = localStorage.getItem('keyTimestamp');

            if (savedKey && Date.now() - savedTime < expirationTime) {
                // Nếu key còn hạn, chuyển hướng luôn
                window.location.href = redirectUrl;
            } else {
                // Nếu key hết hạn hoặc chưa lưu, lưu lại và chuyển hướng
                localStorage.setItem(keyStorage, correctKey);
                localStorage.setItem('keyTimestamp', Date.now());
                window.location.href = redirectUrl;
            }
        } else {
            messageElement.textContent = 'Key không đúng! Hãy thử lại.';
            linkElement.style.display = 'block';
        }
    }
</script>

</body>
</html>
