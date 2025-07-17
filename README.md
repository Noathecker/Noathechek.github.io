Khi nhập đúng key sẽ không cần nhập lại key trong 24h(nếu chx cs key thì ấn nút lấy key thì sẽ hiện một đường links bạn chỉ cần sao chép link và thoát ra dán vào Chrome hoặc bất cứ trình duyệt nào cx đc để get key).
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nhập và Nhận Key</title>
    <style>
        /* Reset default styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-color: #f1f1f1;
            text-align: center;
            padding: 20px;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            color: #333;
        }

        .section {
            margin-bottom: 30px;
        }

        input[type="text"] {
            width: 80%;
            padding: 10px;
            font-size: 16px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            padding: 12px 20px;
            font-size: 16px;
            color: white;
            background-color: #4CAF50;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 80%;
        }

        button:hover {
            background-color: #45a049;
        }

        #generatedKey {
            margin-top: 20px;
            font-size: 18px;
            color: #333;
            display: none;
        }

        #message {
            margin-top: 20px;
            color: red;
        }

        @media (max-width: 600px) {
            input[type="text"] {
                width: 100%;
            }
            button {
                width: 100%;
            }
        }
    </style>
</head>
<body>

<div class="container">
    <!-- Phần Nhập Key -->
    <div class="section">
        <h1>Nhập Key Bên Dưới</h1>
        <input type="text" id="keyInput" placeholder="Nhập key của bạn...">
        <button onclick="checkKey()">Kiểm Tra Key</button>
        <div id="message"></div>
    </div>

    <!-- Phần Nhận Key -->
    <div class="section">
        <h1>Lấy Key</h1>
        <button onclick="generateKey()">Lấy Key</button>
        <div id="generatedKey">
            <p>Link Key: <a href="https://link4m.com/R8AmPZ" target="_blank">https://link4m.com/R8AmPZ</a></p>
        </div>
    </div>
</div>

<script>
    const correctKey = 'Key_129087';  // Thay đổi key đúng ở đây
    const redirectUrl = 'https://sites.google.com/view/cloudgamefree';
    const keyStorage = 'userKey';
    const expirationTime = 24 * 60 * 60 * 1000;  // 24 giờ tính bằng milliseconds

    // Kiểm tra key nhập vào
    function checkKey() {
        const userKey = document.getElementById('keyInput').value;
        const messageElement = document.getElementById('message');

        if (userKey === correctKey) {
            messageElement.textContent = '';
            localStorage.setItem(keyStorage, correctKey);
            localStorage.setItem('keyTimestamp', Date.now()); // Lưu thời gian khi nhập key đúng
            window.location.href = redirectUrl;  // Chuyển hướng nếu key đúng
        } else {
            messageElement.textContent = 'Key không đúng! Hãy thử lại.';
        }
    }

    // Lấy key
    function generateKey() {
        const generatedKey = document.getElementById('generatedKey');
        generatedKey.style.display = 'block';  // Hiển thị link key
    }

    // Kiểm tra xem key có còn hợp lệ trong localStorage hay không
    window.onload = function() {
        const savedKey = localStorage.getItem(keyStorage);
        const savedTime = localStorage.getItem('keyTimestamp');

        if (savedKey && Date.now() - savedTime < expirationTime) {
            // Nếu key còn hạn, chuyển hướng luôn
            window.location.href = redirectUrl;
        }
    };
</script>

</body>
</html>
