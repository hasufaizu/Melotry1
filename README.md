<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fullscreen Player</title>
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">
  <style>
    html, body {
      margin: 0;
      padding: 0;
      height: 100%;
      background: black;
    }

    #player-container {
      position: relative;
      width: 100vw;
      height: 100vh;
      cursor: pointer;
    }

    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
</head>
<body>
  <div id="player-container">
    <iframe id="video" src="https://hi351sinoom.com/play/tt18411490" allow="fullscreen; autoplay; encrypted-media; picture-in-picture" allowfullscreen></iframe>
  </div>

  <script>
    const container = document.getElementById('player-container');

    container.addEventListener('click', async () => {
      if (!document.fullscreenElement) {
        try {
          await container.requestFullscreen();
          if (screen.orientation && screen.orientation.lock) {
            try {
              await screen.orientation.lock('landscape');
            } catch (err) {
              console.warn('Orientation lock not supported:', err);
            }
          }
        } catch (err) {
          console.error('Fullscreen request failed:', err);
        }
      }
    });
  </script>
</body>
</html>
