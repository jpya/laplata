<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Reproductor</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background-color: black;
      height: 100%;
      width: 100%;
      overflow: hidden;
    }
    video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  </style>
</head>
<body>
  <video id="video" autoplay muted playsinline></video>

  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
  <script>
    const video = document.getElementById('video');
    const videoSrc = "https://sae12.playlist.live-video.net/v1/playlist/CtYFV0RuhBYu3EEPZSRkNgtXsDcLNnSgcbEhSbL-g09f1h90K8mYrE9CQ_eihMn7uE4gWJUJ-h3NDVCEKLF39tfcu7MsFbkqzqvwlAy3Xj_CY1Z0w3tTPVlkTNNaonfC5k-R7Wr9sdmZo-k3RNinBt7mWoWjc9GypGVPHb5wN9fu_h5pc2QWXM8O_k7zj19up40VeZKi4rmivsMsDJRQF1OMcdgndAcjC1bbvVii-LkRBBGE8SjGE6hN2G2v7UBW8jpckxnXlmUqAjpmbBayhIgOjCGxd9gkd_aUSx4e8yoN4Pwxk3gwss10itrtFDoWAKP88oikvwE2naSK8-wdB-YLMwHD5TCanpBB1BtOAmCVv3dfk1WQnWg_v6Mg1s_6ee9XxVCQyOKjl2APTyASqLftoG5aEv5Li_2bY0EXYAyppZsYMO36xu2QwI0HO2-iONPio477i-ufj5iS1gbOlje7y--537OXqbDkSQOaZuDbRMvkcUB3uVUxccQ4nJ_xoJVx9Jbk9HOjLED5q92Lggjcl3nEqjopenZ_k5vKSiq-UgbsAG6HKWY0CQXbfNHyu444RSUj10f5LeKq36PDJGjA17Zm-SiuD7fB8ekHv6Ga0m29e0-5VA8P-Fn0EI2B6CNFg5VkIVCE_Sh9dy-GCtbRcxR9uU4qvkF_TXc-p5ZrnZH1LdgLzfuJdPsrUaBkLpEYjTEETMZcwthxZdlwRcSJOkvPr-eaE3h13x5jrh3dDlzETpfy6wuaogyTV4WPqAMx2QfoMsv9XYG70Y8gMJwI-CpGMRLYFCdGQiqUIyDkocy5DyaIh-V6g2VOjPZhGZ9KTseXf_sgjymrnyJBWLriEjmflrGCcBYQbh1P-cIbcKA3yTF2I7UvvzST34jcq4yXxusir-Uk6qoCHNdpaKPHU3LDlJLSfL1VGXJ3JXzt41rvBjQb92gQKbMz02sFnHp6LWpwkul3GgxZz8F9em_VaRMwIQAgASoJdXMtZWFzdC0yMJIM.m3u8";

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
