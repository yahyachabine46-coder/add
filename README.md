<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Screen Capture Tool</title>
    <style>
        body { font-family: sans-serif; text-align: center; padding: 20px; background: #f4f4f9; }
        video { width: 80%; border: 5px solid #333; border-radius: 10px; margin-top: 20px; }
        button { padding: 10px 20px; font-size: 16px; cursor: pointer; background: #007bff; color: white; border: none; border-radius: 5px; }
        button:hover { background: #0056b3; }
    </style>
</head>
<body>

    <h1>Universal Screen Viewer</h1>
    <p>Click the button to select the window you want to "solve."</p>
    
    <button id="startBtn">Capture Screen</button>
    <br>
    <video id="video" autoplay></video>

    <script>
        const startBtn = document.getElementById('startBtn');
        const videoElement = document.getElementById('video');

        startBtn.addEventListener('click', async () => {
            try {
                // This triggers the browser's built-in screen picker
                const mediaStream = await navigator.mediaDevices.getDisplayMedia({
                    video: { cursor: "always" },
                    audio: false
                });
                videoElement.srcObject = mediaStream;
            } catch (err) {
                console.error("Error: " + err);
                alert("Capture cancelled or failed.");
            }
        });
    </script>
</body>
</html>
