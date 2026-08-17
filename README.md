<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tool Tạo Ảnh Loading Liên Quân Mobile</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #0b0e14;
            color: #ffffff;
            text-align: center;
            margin: 0;
            padding: 10px;
        }
        h2 {
            color: #f39c12;
            text-shadow: 0 0 10px rgba(243, 156, 18, 0.6);
            margin-bottom: 5px;
        }
        .container {
            max-width: 450px;
            margin: 0 auto;
            background: #151a21;
            padding: 15px;
            border-radius: 12px;
            border: 2px solid #f39c12;
            box-shadow: 0 5px 20px rgba(0,0,0,0.8);
        }
        input[type="file"] {
            margin: 10px 0;
            color: #ccc;
            font-size: 14px;
        }
        .canvas-box {
            position: relative;
            width: 100%;
            max-width: 400px;
            margin: 10px auto;
            border: 3px solid #ffd700;
            border-radius: 8px;
            overflow: hidden;
            background: #000;
        }
        canvas {
            width: 100%;
            height: auto;
            display: block;
        }
        .btn {
            display: block;
            width: 100%;
            background: linear-gradient(135deg, #f39c12, #e74c3c);
            color: #fff;
            padding: 12px;
            font-size: 16px;
            font-weight: bold;
            text-decoration: none;
            border-radius: 8px;
            margin-top: 15px;
            cursor: pointer;
            border: none;
            box-shadow: 0 4px 10px rgba(243, 156, 18, 0.4);
        }
        .btn:active {
            transform: scale(0.98);
        }
    </style>
</head>
<body>

    <div class="container">
        <h2>⚔️ TẠO ẢNH LOADING LQ ⚔️</h2>
        <p style="font-size: 13px; color: #aaa;">Chọn ảnh tướng/nhân vật của ní vào đây:</p>
        
        <input type="file" id="uploadImage" accept="image/*">
        
        <div class="canvas-box">
            <canvas id="posterCanvas" width="800" height="450"></canvas>
        </div>
        
        <button class="btn" id="downloadBtn">TẢI ẢNH LOADING VỀ MÁY</button>
    </div>

    <script>
        const uploadImage = document.getElementById('uploadImage');
        const canvas = document.getElementById('posterCanvas');
        const ctx = canvas.getContext('2d');
        const downloadBtn = document.getElementById('downloadBtn');

        let currentImg = null;

        window.onload = function() {
            drawDefault();
        };

        function drawDefault() {
            ctx.fillStyle = "#11161d";
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            ctx.fillStyle = "#f39c12";
            ctx.font = "bold 28px Arial";
            ctx.textAlign = "center";
            ctx.fillText("CHƯA CHỌN ẢNH TƯỚNG!", canvas.width / 2, canvas.height / 2 - 15);

            ctx.fillStyle = "#8b9bb4";
            ctx.font = "16px Arial";
            ctx.fillText("Bấm 'Chọn tệp' để tải ảnh lên nhé ní ơi", canvas.width / 2, canvas.height / 2 + 25);
        }

        function drawPoster(img) {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // Vẽ ảnh gốc vừa khung
            ctx.drawImage(img, 0, 0, canvas.width, canvas.height);

            // Giả lập khung viền loading game Liên Quân (Độ bóng vàng + viền sáng)
            ctx.strokeStyle = "#ffcc00";
            ctx.lineWidth = 8;
            ctx.strokeRect(0, 0, canvas.width, canvas.height);

            ctx.strokeStyle = "#ffffff";
            ctx.lineWidth = 2;
            ctx.strokeRect(6, 6, canvas.width - 12, canvas.height - 12);

            // Bảng tên góc dưới ngầu lòi
            ctx.fillStyle = "rgba(0, 0, 0, 0.75)";
            ctx.fillRect(15, canvas.height - 55, 220, 40);
            
            ctx.strokeStyle = "#f39c12";
            ctx.lineWidth = 2;
            ctx.strokeRect(15, canvas.height - 55, 220, 40);

            ctx.fillStyle = "#ffffff";
            ctx.font = "bold 16px Arial";
            ctx.textAlign = "left";
            ctx.fillText("LIÊN QUÂN MOBILE", 25, canvas.height - 28);
        }

        uploadImage.addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(event) {
                    const img = new Image();
                    img.onload = function() {
                        currentImg = img;
                        drawPoster(img);
                    }
                    img.src = event.target.result;
                }
                reader.readAsDataURL(file);
            }
        });

        downloadBtn.addEventListener('click', function() {
            if (!currentImg) {
                alert("Ní chưa chọn ảnh kìa!");
                return;
            }
            const link = document.createElement('a');
            link.download = 'anh-loading-lienquan.png';
            link.href = canvas.toDataURL('image/png');
            link.click();
        });
    </script>

</body>
</html>

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
