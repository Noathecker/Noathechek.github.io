Khi nhập key thành công bạn sẽ không cần nhập lại trong 24h( nếu vẫn hiện menu nhập key chỉ cần ấn nút xác nhận key lần nx sẽ vào được cloud)
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </title> Nhập Key để vào cloud</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
        }
        .container {
            text-align: center;
            padding: 20px;
            background-color: white;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }
        input[type="text"] {
            padding: 10px;
            font-size: 16px;
            border-radius: 4px;
            border: 1px solid #ddd;
            margin-bottom: 10px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            border: none;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
            border-radius: 4px;
        }
        button:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Vui lòng nhập key để vào cloud</h2>
    <input type="text" id="keyInput" placeholder="Nhập key ở đây" />
    <br>
    <button onclick="checkKey()">Xác Nhận</button>
    <p id="error" style="color: red; display: none;">Key Sai Rồi Níi!</p>
</div>

<script>
    const correctKey = "Key_869"; // Đổi key ở đây
    const validKeyStorageKey = "validKey";
    const expirationTimeKey = "expirationTime";

    function checkKey() {
        const enteredKey = document.getElementById("keyInput").value.trim();
        const errorMessage = document.getElementById("error");

        // Lấy thời gian hết hạn của key từ localStorage
        const expirationTime = localStorage.getItem(expirationTimeKey);
        const currentTime = new Date().getTime();

        // Kiểm tra xem key có hợp lệ hay không và nếu hết hạn thì yêu cầu nhập lại
        if (enteredKey === correctKey && (!expirationTime || currentTime > expirationTime)) {
            // Lưu trạng thái key hợp lệ và thời gian hết hạn
            localStorage.setItem(validKeyStorageKey, "true");
            localStorage.setItem(expirationTimeKey, currentTime + 24 * 60 * 60 * 1000); // 24 giờ = 24*60*60*1000

            // Chuyển hướng đến trang đích
            window.location.href = "https://sites.google.com/view/cloudgamefree";
        } else {
            // Hiển thị thông báo lỗi nếu key không hợp lệ hoặc hết hạn
            errorMessage.style.display = "block";
        }
    }

    // Kiểm tra nếu key hợp lệ từ trước
    if (localStorage.getItem(validKeyStorageKey)) {
        const expirationTime = localStorage.getItem(expirationTimeKey);
        const currentTime = new Date().getTime();

        if (currentTime < expirationTime) {
            // Nếu key vẫn còn hiệu lực, tự động chuyển đến trang
            window.location.href = "https://sites.google.com/view/cloudgamefree";
        }
    }
</script>

</body>
</html>
