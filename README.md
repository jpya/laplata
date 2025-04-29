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
    const videoSrc = "https://sae12.playlist.live-video.net/v1/playlist/CtcFONr5-6DkDgRTwB8f0_xY9hUPWRiNbyuOPLr01pgxOUdMY_in7KLxLd46_LupmdK9MS8xRL7CgpaYR3GyyEkE1fGARS0gJm7klY8d3WIepWen48B2QOrsn3fOOlWdgw0ZoMVOis-fjDkQ3pNf_azzZ6s7Fu1Z4u1LheqZaeQ5EzA28bJMq5AwkwYqgUW3VOi_dlOsL5tItN4iQdKmj3GGpRYBbcEx9n3wFvPQcuKDkWIh-5p7ALONs5F-YogtzfTQPNBUe675aa1L8GnFFiMdn2rdN3hNTvYJzQ5WV623c22-W0Jlq5VbH1SjnTt1pwQzN6tBSslWWBW-XT2qYzDwE4syeGExyXDg-kHy8O9kICNjCtfED3pA6kjroaKvBha1DPVvDZR3GxLSR2-QP5L-s-sHp7uqv2lgXjMkKEkppDud5gXOgK58I0lV8SS2RC6AiGD7qe8qGO0LK3agPWtvP3j4Q5twag5sCJT7KlfM396fjPytdQCEvVhnynt8fZGIZ6xTgaEWD9NeaMjeAJIyTs9vmpz6P3Qj_HvMw5e6hSRO1MQ8UcPbNRaWmjZC4AJK1lj3QqXnEYTKtPRvhXPjc5J-VzmUau3dJXttSLGDa4fMELKy9JKju060yEM2pfEkKduphlij0P9qkHOGIleGdlJ8p48ujsHfSD9oLhBqZKJpiwZZiT9AoStaYhTGbFfi3OX8l4Nci0hTwItsGip3zcncHycaDqGQZSbbnWBsyjU-kkp80xr7g69TovuV9tJvmh1AKf5gqNf97XxYjnwm2BYpWeKaWiwfBZKqo8eHIKgjs2-OKRFX7jBBryHxPThxeawKQkX7UXHFSL4xKbC25_in0BEElsjvqkNTwdSiwYkTuHS2v7R8VfqHlFJ4LxB_1UXQ1QmGVVLyx204LaMUJlzQiDaaT3v_lLfizeZiUacTOzqBYjulUAjfhLRHX3ZQSkUR-T64ZhoMHtM_HHg07Yec_-qfIAEqCXVzLWVhc3QtMjCSDA.m3u8";

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
