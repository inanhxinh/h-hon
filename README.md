<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chúc Mừng Kỷ Niệm</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            font-family: 'Pacifico', cursive, sans-serif;
            text-align: center;
            overflow: hidden;
            position: relative;
            flex-direction: column;
        }
        .heart-container {
            position: relative;
            width: 400px;
            height: 400px;
            cursor: pointer;
            animation: bounce 3s ease-in-out infinite;
        }
        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        .fill {
            position: absolute;
            top: 100%;
            left: 0;
            width: 400px;
            height: 0;
            background: linear-gradient(45deg, #ff4d4d, #ff0000);
            clip-path: path("M200 50 C250 0, 400 0, 400 150 C400 300, 200 400, 200 400 C200 400, 0 300, 0 150 C0 0, 150 0, 200 50 Z");
            transition: height 6s ease-in-out;
        }
        .click-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.5rem;
            color: white;
            font-weight: bold;
            animation: blink 1s infinite alternate;
        }
        @keyframes blink {
            0% { opacity: 1; }
            100% { opacity: 0.5; }
        }
        .content-container {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            padding: 20px;
        }
        .anniversary-text {
            font-size: 2rem;
            font-weight: bold;
            color: #ff55aa;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 2s ease-out, transform 2s ease-out;
        }
        .photo-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 2s ease-out 2s, transform 2s ease-out 2s;
            margin-bottom: 20px;
        }
        .photo-frame {
            width: 160px;
            height: 150px;
            border: 4px solid #ff66b2;
            background-color: white;
            box-shadow: 0 0 15px rgba(255, 105, 180, 0.7);
            overflow: hidden;
            border-radius: 15px;
            transition: transform 0.3s;
        }
        .photo-frame img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        .photo-frame:hover {
            transform: scale(1.1);
        }
        #spotify-player {
            display: none;
            width: 300px;
            height: 80px;
        }
        .spotify-wrapper {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }
        .falling-heart {
            position: absolute;
            font-size: 1.5rem;
            opacity: 0.7;
            animation: fallDown linear infinite;
            top: -50px;
        }
        @keyframes fallDown {
            from { opacity: 1; transform: translateY(0); }
            to { transform: translateY(100vh) rotate(360deg); opacity: 0; }
        }
        .note {
            display: none;
            position: absolute;
            background-color: white(0, 0, 0, 0.7);
            color: black
            ;
            border-radius: 10px;
            z-index: 10;
            text-align: center;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.2em;
        }
        .photo-frame{
          position:relative;
        }
    </style>
</head>
<body>
  <div class="heart-container" onclick="fillHeart()">
    <div class="fill" id="fill"></div>
    <div class="click-text">Click here! 💖</div>
</div>

<div class="content-container" id="contentContainer">
    <div class="anniversary-text">🎂 Chúc Mừng Kỷ Niệm! 💖</div>
    
    <div class="photo-grid">
        <div class="photo-frame" data-note="Kỷ niệm lần đầu gặp nhau!">
            <img id="photo1" src="z6376983877357_08120225470302d5c0700bc517d79d3c.jpg" alt="Ảnh 1" onclick="showNote(this)">
        </div>
        <div class="photo-frame" data-note="Buổi hẹn hò đầu tiên.">
            <img id="photo2" src="z6376983889215_19482c05811b4b24ea06c4faaa8cb861.jpg" alt="Ảnh 2" onclick="showNote(this)">
        </div>
        <div class="photo-frame" data-note="Chuyến du lịch đáng nhớ.">
            <img id="photo3" src="z6376983893583_c105f0b486c66c9b8645d111a02ddf3e.jpg" alt="Ảnh 3" onclick="showNote(this)">
        </div>
        <div class="photo-frame" data-note="Khoảnh khắc hạnh phúc.">
            <img id="photo4" src="z6376983893848_37bff905f0dce2c431a134530a4d7600.jpg" alt="Ảnh 4" onclick="showNote(this)">
        </div>
    </div>
    
    <div class="spotify-wrapper">
        <iframe id="spotify-player" 
                src="https://open.spotify.com/embed/playlist/37i9dQZF1DXcBWIGoYBM5M?utm_source=generator"
                width="300" height="80" frameBorder="0" allowfullscreen="" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy">
        </iframe>
    </div>
    <div class="note" id="note"></div>
</div>

<script>
     function fillHeart() {
      document.getElementById('fill').style.height = `100%`;
      document.getElementById('fill').style.top = `0%`;
      setTimeout(() => {
        document.querySelector('.heart-container').style.display = 'none';
        document.getElementById('contentContainer').style.display = 'flex';
        document.querySelector('.anniversary-text').style.opacity = 1;
        document.querySelector('.photo-grid').style.opacity = 1;
        document.getElementById('spotify-player').style.display = 'block';
      }, 6000);
    }
    function createFallingHearts() {
      let heart = document.createElement("div");
      heart.innerHTML = "💖";
      heart.classList.add("falling-heart");
      document.body.appendChild(heart);
      heart.style.left = Math.random() * window.innerWidth + "px";
      heart.style.animationDuration = Math.random() * 3 + 3 + "s";
      setTimeout(() => heart.remove(), 5000);
    }
    setInterval(createFallingHearts, 1000);

        function showNote(element) {
            const photoFrame = element.parentElement;
            const noteText = photoFrame.getAttribute('data-note');
            const noteDiv = document.getElementById('note');

            if (photoFrame && noteDiv) {
                element.style.display = 'none';

                noteDiv.textContent = noteText;
                noteDiv.style.display = 'flex'; // Dùng flex để căn giữa

                // Lấy kích thước VÀ vị trí của khung chứa ảnh.
                const rect = photoFrame.getBoundingClientRect();

                // Gán vị trí của note bằng vị trí và kích thước của khung chứa ảnh.
                noteDiv.style.position = 'absolute';
                noteDiv.style.left = rect.left + 'px';
                noteDiv.style.top = rect.top + 'px';
                noteDiv.style.width = rect.width + 'px';
                noteDiv.style.height = rect.height + 'px';

            } else {
                console.error("Không tìm thấy phần tử photoFrame hoặc note");
            }
        }
  </script>
</body>
</html>
