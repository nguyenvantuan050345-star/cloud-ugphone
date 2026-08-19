<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Chuyển Video 16:9 sang 9:16</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin-top: 50px; background: #121212; color: #fff; }
        input, button { padding: 10px 20px; margin: 10px; font-size: 16px; cursor: pointer; }
        video, canvas { max-width: 100%; height: auto; margin-top: 20px; border: 2px dashed #444; }
    </style>
</head>
<body>
    <h2>Tool Chuyển Video Ngang Thành Video Short</h2>
    <input type="file" id="upload" accept="video/*"><br>
    <button id="processBtn">Xử lý & Cắt Video</button>
    <br>
    <video id="videoPlayer" controls style="display:none;"></video>
    <canvas id="canvasOutput" style="display:none;"></canvas>
    <br>
    <a id="downloadLink" style="display:none;" download="short_video.webm">Tải Video Short Về</a>

    <script>
        const upload = document.getElementById('upload');
        const video = document.getElementById('videoPlayer');
        const processBtn = document.getElementById('processBtn');

        upload.addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file) {
                video.src = URL.createObjectURL(file);
                video.style.display = 'block';
            }
        });

        processBtn.addEventListener('click', function() {
            alert("Đã nhận video! Bạn có thể phát triển thêm logic lấy khung giữa (crop trung tâm) từ Canvas ở đây.");
            // Logic code canvas để crop 16:9 sang 9:16 sẽ xử lý frame bằng video.requestVideoFrameCallback hoặc drawImage.
        });
    </script>
</body>
</html>
