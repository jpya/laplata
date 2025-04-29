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
  <video id="video" controls autoplay></video>

  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
  <script>
    const video = document.getElementById('video');
    const videoSrc = "https://sae11.playlist.live-video.net/v1/playlist/CtYF4BttfdRFSowpDOkgpZ9-wuCDI8H8O_avvsKaPMQV35w5F8XDDBo83vV0vfkfpv6P7AWythqdzGIvw9Z18P7jp00imuSg2swL4dj08QzKh1AmpMkspYFDa4EIwzaQD52PCi6Tf_Bs9515H5AXrayAltgnZsy_MU70CmLgTDRFnw4ouRNxIY4P7H0PzQAEleVhc0zafMmVFBC8gvYqhPC8q0-OU3nuSlWQK0HWAV9QLBDWXG3DxktXklZ61HtQSkiwPfEYpkhwS6teBrG-S4fbVky3O7lU7c5xTuk19N6kBCbUiCj1rMHU0YHAQD02Tu-ToG3D6stSoDFCY9LEZdJJVCueNJzISL5FQQgnGW1w2syzRC5uBQVG7BZu1yuxXpGTxKalARc1g_aHfK6KPvGlpErY3LrBdN7KiInt3VUME11Fqe46Icn8OXQFyu7g2z8d7Utxm__PJUiyWcn2bZ0y_r_LHg6Y_UTCQWn76tT206c4pjJQE0ujSRQiGyaCR2F8x4QW-Pk-uQIbD_8e4KBSDd3P84caHx2LVKtxJ3ouhLXtQ3mQsWot95vBc3AHtbhASpSA0qsbiX_sS7YMtRDEY75WAxMa0MQB2WqEAJsl4lcgHB9J3PcABdDJYDQgYzjc736z4VDHrNuamj2v6EM5cuG1UswQQqx7eLPlqvq-SuZzRNG6tYPLhWzWHCy2lHy66RKhXR75N0Njl6GjMFRj9CPm_TpM3D6qGgAEpRd3oOoBe2nu1QwUqhMAz-OddtYRO42zn0f7JLcURDvUyuC9CTpeYOtSfWOS6fNyqfeq5GxYkiYGqofQdHZMdz_Y971VsqIfXDF1B_V18CAz5tOFWCMmh7KiyL3ECOeB6TC1w4X1IVxzUUhkgyKH3Js4-w9iIXaCNyyhY0o_ZVG3nJgmTOqMl0hTacTTc2Jx6v7cI4qWJMOP6fl1lnc-QCprkNXh8wG7outWGgwLtgbp36yKJT2wE_8gASoJdXMtZWFzdC0yMJIM.m3u8";

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
