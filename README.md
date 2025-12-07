# Вывод изображений и текстовое поле
<!doctype html>
<html lang="az">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Tam ekran şəkil</title>
  <style>
    /* tam ekran konteyner */
    html, body {
      height: 100%;
      margin: 0;
      background: #000;
      font-family: Tahoma, Arial, sans-serif;
    }

    .fullscreen-wrap {
      display: grid;
      place-items: center;
      height: 100vh;
      width: 100vw;
      overflow: hidden;
      position: relative;
      cursor: zoom-in;
    }

    /* Şəklin aspekt nisbətini qoruyub, mümkün qədər böyük göstərilməsi */
    .fullscreen-wrap img {
      max-width: 100%;
      max-height: 100%;
      width: auto;
      height: auto;
      object-fit: contain;
      transition: transform .35s ease;
      user-select: none;
      -webkit-user-drag: none;
    }

    /* klikləyəndə böyüdülmüş effekti (opsional) */
    .fullscreen-wrap.zoomed img {
      transform: scale(1.05);
      cursor: zoom-out;
    }

    /* yuxarı sağ küncdə kiçik link/button */
    .controls {
      position: absolute;
      top: 12px;
      right: 12px;
      display: flex;
      gap: 8px;
      z-index: 10;
    }
    .controls a, .controls button {
      background: rgba(255,255,255,0.9);
      color: #111;
      padding: 6px 8px;
      border-radius: 6px;
      text-decoration: none;
      font-size: 13px;
      border: none;
    }
  </style>
</head>
<body>
  <div class="fullscreen-wrap" id="wrap" title="Şəkili kliklə: tam ekran / tam geri">
    <!--
      Burada src-u dəyiş: 
      - Əgər serverdə fayl eyni qovluqdadırsa: src="IMG_1349.JPG"
      - Yoxsa tam URL ver: src="https://example.com/path/to/image.jpg"
      - Daxili konteyner yolu nümunəsi: "/mnt/data/IMG_1349.JPG"
    -->
    <img id="theImage" src="/mnt/data/IMG_1349.JPG" alt="Tam ekran şəkil" />

    <div class="controls">
      <!-- Şəkli yeni tabda açmaq / yükləmək -->
      <a id="openNew" href="/mnt/data/IMG_1349.JPG" target="_blank" rel="noopener">Yeni tabda aç</a>
      <a id="download" href="/mnt/data/IMG_1349.JPG" download>Yüklə</a>
    </div>
  </div>

  <script>
    const wrap = document.getElementById('wrap');
    const img = document.getElementById('theImage');

    // Kliklə zoom və ya fullscreen rejiminə keçid (Fullscreen API)
    wrap.addEventListener('click', async (e) => {
      // əgər artıq zoomed sinfi varsa, çıxırıq
      if (wrap.classList.contains('zoomed')) {
        wrap.classList.remove('zoomed');
        // çıxmaq: əgər fullscreendəsə çıx
        if (document.fullscreenElement) {
          await document.exitFullscreen().catch(()=>{});
        }
        return;
      }

      // yoxsa zoom əlavə et
      wrap.classList.add('zoomed');

      // cəhd et fullscreen rejiminə keçməyə (brauzer icazəsinə bağlıdır)
      if (wrap.requestFullscreen) {
        wrap.requestFullscreen().catch(()=>{ /* istifadəçi icazəsi tələb oluna bilər */ });
      }
    });

    // ESC basıldıqda zoom sinfini götür
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') {
        wrap.classList.remove('zoomed');
      }
    });

    // Əgər şəkil yüklənməsə, qısa bildiriş göstər
    img.addEventListener('error', () => {
      img.alt = 'Şəkil tapılmadı. src yolunu yoxlayın.';
      img.style.maxWidth = '60%';
    });

    // Kontrollerin href-lərini img.src-ə dinamiki etmək (əgər src dəyişibsə)
    document.getElementById('openNew').href = img.src;
    document.getElementById('download').href = img.src;
  </script>
</body>
</html>
