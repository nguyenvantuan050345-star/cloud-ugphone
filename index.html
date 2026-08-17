<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trình Tạo Ảnh Loading Tùy Chỉnh</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #121212;
            color: #ffffff;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        h2 {
            color: #00ffcc;
        }
        .container {
            max-width: 500px;
            margin: 0 auto;
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.5);
        }
        input[type="file"] {
            margin: 15px 0;
            color: #fff;
        }
        canvas {
            max-width: 100%;
            height: auto;
            border: 2px dashed #444;
            border-radius: 5px;
            margin-top: 15px;
            background: #000;
        }
        .btn {
            display: inline-block;
            background: #00ffcc;
            color: #000;
            padding: 10px 20px;
            font-weight: bold;
            text-decoration: none;
            border-radius: 5px;
            margin-top: 15px;
            cursor: pointer;
            border: none;
        }
        .btn:hover {
            background: #00cc99;
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>Tool Tạo Ảnh Loading Cá Nhân Hóa</h2>
        <p>Chọn ảnh của ní để ghép vào khung siêu nét:</p>
        
        <input type="file" id="uploadImage" accept="image/*">
        <br>
        
        <!-- Khung hiển thị canvas -->
        <canvas id="posterCanvas" width="800" height="450"></canvas>
        <br>
        
        <button class="btn" id="downloadBtn">Tải Ảnh Về Máy</button>
    </div>

    <script>
        const uploadImage = document.getElementById('uploadImage');
        const canvas = document.getElementById('posterCanvas');
        const ctx = canvas.getContext('2d');
        const downloadBtn = document.getElementById('downloadBtn');

        // Tạo khung nền mặc định khi mới vào web
        window.onload = function() {
            drawDefaultTemplate();
        };

        function drawDefaultTemplate(userImg = null) {
            // Xóa sạch canvas
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            if (userImg) {
                // Vẽ ảnh do người dùng chọn (căn full khung 16:9)
                ctx.drawImage(userImg, 0, 0, canvas.width, canvas.height);
            } else {
                // Hiển thị chữ hướng dẫn nếu chưa chọn ảnh
                ctx.fillStyle = "#333";
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                ctx.fillStyle = "#888";
                ctx.font = "20px Arial";
                ctx.textAlign = "center";
                ctx.fillText("Chưa có ảnh được chọn. Hãy chọn ảnh bên trên!", canvas.width / 2, canvas.height / 2);
            }

            // Vẽ lớp Khung / Viền đè lên trên (Ní có thể thay thế bằng khung game tùy ý)
            ctx.strokeStyle = "#00ffcc";
            ctx.lineWidth = 6;
            ctx.strokeRect(0, 0, canvas.width, canvas.height);

            // Thêm hiệu ứng chữ mờ hoặc tên thương hiệu góc ảnh
            ctx.fillStyle = "rgba(0, 0, 0, 0.6)";
            ctx.fillRect(20, canvas.height - 50, 200, 35);
            ctx.fillStyle = "#ffffff";
            ctx.font = "bold 16px Arial";
            ctx.textAlign = "left";
            ctx.fillText("Depkobay Custom", 30, canvas.height - 27);
        }

        // Xử lý khi người dùng up ảnh lên
        uploadImage.addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(event) {
                    const img = new Image();
                    img.onload = function() {
                        drawDefaultTemplate(img);
                    }
                    img.src = event.target.result;
                }
                reader.readAsDataURL(file);
            }
        });

        // Xử lý nút tải ảnh về
        downloadBtn.addEventListener('click', function() {
            const link = document.createElement('a');
            link.download = 'anh-loading-tu-che.png';
            link.href = canvas.toDataURL('image/png');
            link.click();
        });
    </script>

</body>
</html>
