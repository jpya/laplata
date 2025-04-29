<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Reproductor M3U8</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      background-color: #111;
      color: white;
      font-family: sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      flex-direction: column;
    }
    video {
      width: 80%;
      max-width: 800px;
      border: 2px solid white;
      border-radius: 10px;
    }
  </style>
</head>
<body>

  <h2>Reproductor HLS (M3U8)</h2>
  <video id="video" controls autoplay></video>

  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
  <script>
    const video = document.getElementById('video');
    const videoSrc = "https://fa723fc1b171.us-west-2.playback.live-video.net/api/video/v1/us-west-2.196233775518.channel.iQ63N98btHWQ.m3u8?browser_family=chrome&browser_version=135.0&cdm=wv&os_name=Linux&os_version=undefined&platform=web&player_backend=mediaplayer&player_version=1.31.0&supported_codecs=av1,h264&token=eyJ0eXAiOiJKV1QiLCJhbGciOiJFUzM4NCJ9.eyJhd3M6Y2hhbm5lbC1hcm4iOiJhcm46YXdzOml2czp1cy13ZXN0LTI6MTk2MjMzNzc1NTE4OmNoYW5uZWwvaVE2M045OGJ0SFdRIiwiYXdzOmFjY2Vzcy1jb250cm9sLWFsbG93LW9yaWdpbiI6Imh0dHBzOi8va2ljay5jb20saHR0cHM6Ly93d3cuZ3N0YXRpYy5jb20saHR0cHM6Ly8qLmtpY2subGl2ZSxodHRwczovL3BsYXllci5raWNrLmNvbSxodHRwczovL2FkbWluLmtpY2suY29tLGh0dHBzOi8vYmV0YS5raWNrLmNvbSxodHRwczovL25leHQua2ljay5jb20saHR0cHM6Ly9kYXNoYm9hcmQua2ljay5jb20saHR0cHM6Ly8qLnByZXZpZXcua2ljay5jb20iLCJhd3M6c3RyaWN0LW9yaWdpbi1lbmZvcmNlbWVudCI6ZmFsc2UsImV4cCI6MTc0NTk0MTU2Nn0.Q_puZSvJRm4-XFYkmcC40qSsN3U3IeSpnRQopU_KbZxeHRcwJq6YCNB7d3u51KGq1hw2ZsoutpRPrZ6G90IOwoID4fAOiSNU1EBiPxBDFrXoCNN-1QgbCXlEbW8kKhfq";

    if (Hls.isSupported()) {
      const hls = new Hls();
      hls.loadSource(videoSrc);
      hls.attachMedia(video);
      hls.on(Hls.Events.MANIFEST_PARSED, () => {
        video.play();
      });
    } else if (video.canPlayType('application/vnd.apple.mpegurl')) {
      video.src = videoSrc;
      video.addEventListener('loadedmetadata', () => {
        video.play();
      });
    } else {
      alert("Tu navegador no soporta HLS.");
    }
  </script>
</body>
</html>
