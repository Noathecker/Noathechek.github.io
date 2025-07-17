<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Key Authentication</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        .container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .container h2 {
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        input[type="text"] {
            width: 100%;
            padding: 8px;
            border-radius: 4px;
            border: 1px solid #ddd;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .error {
            color: red;
            display: none;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Vui Lòng Nhập Key Để Vào Cloud</h2>
    <div class="form-group">
        <input type="text" id="keyInput" placeholder="Nhập key ở đây" />
        <div class="error" id="errorMessage">Key không hợp lệ hoặc đã hết hạn. Vui lòng thử lại sau 24 giờ.</div>
    </div>
    <button id="submitBtn">Xác nhận</button>
</div>

<script>
    const validKey = "Key_869";  // Thay thế bằng key thực tế của bạn
    const redirectUrl = "https://sites.google.com/view/cloudgamefree";
    
    // Lấy thời gian hiện tại từ localStorage
    const lastAccessTime = localStorage.getItem("lastAccessTime");
    const currentTime = new Date().getTime();
    
    if (lastAccessTime && (currentTime - lastAccessTime < 24 * 60 * 60 * 1000)) {
        // Nếu đã nhập key trong vòng 24 giờ
        window.location.href = redirectUrl;
    }

    document.getElementById('submitBtn').addEventListener('click', () => {
        const enteredKey = document.getElementById('keyInput').value;
        const errorMessage = document.getElementById('errorMessage');
        
        // Kiểm tra key
        if (enteredKey === validKey) {
            // Lưu thời gian truy cập thành công vào localStorage
            localStorage.setItem("lastAccessTime", currentTime.toString());
            window.location.href = redirectUrl;
        } else {
            // Hiển thị thông báo lỗi nếu key không hợp lệ
            errorMessage.style.display = "block";
        }
    });
</script>

</body>
</html>
