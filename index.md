





              <!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>HOANGDZ TOOL + LE KHÁNH HUY PRO</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Roboto:wght@300;500;900&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Roboto', sans-serif; touch-action: manipulation; }
        body { background: #000; color: white; overflow: hidden; height: 100vh; width: 100vw; position: fixed; }

        /* --- HIỆU ỨNG TUYẾT RƠI (TỐI ƯU) --- */
        #snow-canvas { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 30000; }

        /* --- LOBBY CHỌN GAME --- */
        #lobby {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle, #1a1a1a 0%, #000 100%);
            z-index: 20000; display: flex; flex-direction: column; align-items: center; justify-content: center;
        }
        
        .lobby-title { font-family: 'Orbitron'; font-size: 22px; color: #00f2ff; margin-bottom: 25px; text-transform: uppercase; text-align: center; text-shadow: 0 0 15px #00f2ff; line-height: 1.5; }
        
        /* Grid 2 cột chính, hàng đặc biệt cho bàn phụ */
        .game-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; padding: 15px; width: 100%; max-width: 500px; }
        
        .game-card {
            background: rgba(255,255,255,0.05); border: 1px solid #333; border-radius: 12px; padding: 10px;
            display: flex; flex-direction: column; align-items: center; cursor: pointer; transition: 0.2s;
            position: relative; overflow: hidden;
        }
        .game-card:active { transform: scale(0.95); border-color: #00f2ff; background: rgba(0,242,255,0.1); }
        .game-card img { width: 65px; height: 65px; border-radius: 12px; margin-bottom: 8px; }
        .game-card span { font-weight: 900; font-size: 11px; letter-spacing: 0.5px; text-align: center; }
        
        /* Nhãn đánh dấu loại bàn */
        .badge { position: absolute; top: 0; right: 0; background: #ffcc00; color: #000; font-size: 8px; padding: 2px 6px; font-weight: bold; border-bottom-left-radius: 8px; }
        .badge-normal { background: #00f2ff; }

        /* --- NÚT THOÁT --- */
        #exit-home {
            position: fixed; top: 15px; left: 15px; z-index: 100000;
            background: rgba(255, 0, 0, 0.8); border: 2px solid #fff; color: white;
            padding: 8px 15px; border-radius: 8px; font-weight: bold; cursor: pointer;
            display: none; font-size: 11px; font-family: 'Orbitron';
        }

        /* --- GAME AREA --- */
        #gameArea { display: none; width: 100%; height: 100%; position: relative; }
        iframe { width: 100%; height: 100%; border: none; background: #000; }

        /* --- TOOL ROBOT --- */
        #robot-container {
            position: fixed; top: 25%; right: 10px; z-index: 999999;
            display: flex; align-items: center; cursor: move; touch-action: none;
        }
        #robot-inner {
            display: flex; align-items: center; background: rgba(10, 10, 10, 0.9);
            backdrop-filter: blur(10px); -webkit-backdrop-filter: blur(10px);
            border-radius: 25px; padding: 10px 15px; border: 1px solid rgba(0, 242, 255, 0.5);
            box-shadow: 0 0 20px rgba(0, 242, 255, 0.3);
        }
        #robot-icon-wrapper { position: relative; width: 60px; height: 60px; margin-right: 12px; }
        #robot-img { width: 100%; height: 100%; border-radius: 50%; border: 1.5px solid #00f2ff; background: #000; }
        .scan-ring {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            border: 2px solid #00f2ff; border-radius: 50%; animation: scan 2s infinite linear;
        }
        @keyframes scan { 0% { transform: scale(0.8); opacity: 1; } 100% { transform: scale(1.4); opacity: 0; } }

        #robot-info { display: flex; flex-direction: column; min-width: 130px; }
        .info-header { font-family: 'Orbitron'; font-size: 9px; color: #00f2ff; font-weight: bold; margin-bottom: 2px; }
        .info-phien { font-size: 13px; font-weight: 700; color: #bbb; }
        .info-predict { font-size: 24px; font-weight: 900; text-transform: uppercase; }
        .res-tai { color: #00ff00; text-shadow: 0 0 15px #00ff00; }
        .res-xiu { color: #ff3333; text-shadow: 0 0 15px #ff3333; }
        .res-wait { color: #ffcc00; font-size: 15px; }
    </style>
</head>
<body>

    <canvas id="snow-canvas"></canvas>
    <div id="exit-home" onclick="location.reload()">🏠 HOME</div>

    <div id="lobby">
        <h1 class="lobby-title">HOANGDZ + LE KHÁNH HUY<br><span style="font-size: 12px; color: #fff; opacity: 0.7;">HỆ THỐNG PHÂN TÍCH TỨC THÌ</span></h1>
        <div class="game-grid">
            <div class="game-card" onclick="launchSystem('lc79', 'md5')">
                <div class="badge">MD5</div>
                <img src="https://sf-static.upanhlaylink.com/img/image_2026022333a3182b1f5f788edd4766cbf5fdb450.jpg">
                <span>LC79 MD5</span>
            </div>
            <div class="game-card" onclick="launchSystem('lc79', 'normal')">
                <div class="badge badge-normal">THƯỜNG</div>
                <img src="https://sf-static.upanhlaylink.com/img/image_2026022333a3182b1f5f788edd4766cbf5fdb450.jpg">
                <span>LC79 THƯỜNG</span>
            </div>

            <div class="game-card" onclick="launchSystem('sunwin')">
                <img src="https://i.postimg.cc/y6wrZ8xx/IMG-7874.jpg">
                <span>SUNWIN</span>
            </div>

            <div class="game-card" onclick="launchSystem('b52')">
                <img src="https://i.postimg.cc/ZKdxtPTK/IMG-7873.jpg">
                <span>B52 CLUB</span>
            </div>

            <div class="game-card" onclick="launchSystem('betvip', 'md5')">
                <div class="badge">MD5</div>
                <img src="https://sf-static.upanhlaylink.com/img/image_20260311ea94833c072566a6871cb32d35320731.jpg">
                <span>BETVIP MD5</span>
            </div>
            <div class="game-card" onclick="launchSystem('betvip', 'normal')">
                <div class="badge badge-normal">THƯỜNG</div>
                <img src="https://sf-static.upanhlaylink.com/img/image_20260311ea94833c072566a6871cb32d35320731.jpg">
                <span>BETVIP THƯỜNG</span>
            </div>
        </div>
    </div>

    <div id="gameArea">
        <iframe id="mainFrame" src=""></iframe>
        <div id="robot-container">
            <div id="robot-inner">
                <div id="robot-icon-wrapper">
                    <div class="scan-ring"></div>
                    <img id="robot-img" src="https://iqai.com/_next/image?url=/gifs/home/robotics.gif&w=828&q=75">
                </div>
                <div id="robot-info">
                    <div class="info-header">HOANGDZ + HUY PRO</div>
                    <div class="info-phien" id="txt-phien">Phiên: #-------</div>
                    <div id="txt-predict" class="info-predict res-wait">ANALYZING...</div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const config = {
            lc79: { 
                url: "https://lc79b.bet/", 
                md5: "https://living-telecommunications-start-consoles.trycloudflare.com/api/txmd5", 
                normal: "https://living-telecommunications-start-consoles.trycloudflare.com/api/tx" 
            },
            sunwin: { 
                url: "https://web.sunwin.ag/?affId=Sunwin", 
                api: "https://apisunhpt.onrender.com/sunlon" 
            },
            b52: { 
                url: "https://play.b52club.sale/", 
                api: "https://kingdom-contacted-fact-today.trycloudflare.com/txmd5" 
            },
            betvip: { 
                url: "https://play.betvip.fit/", 
                md5: "https://wide-epic-steve-file.trycloudflare.com/api/txmd5", 
                normal: "https://wide-epic-steve-file.trycloudflare.com/api/tx" 
            }
        };

        let activeApi = '';
        let lastPhien = '';

        // --- HÀM KÍCH HOẠT DUY NHẤT 1 LẦN ẤN ---
        function launchSystem(gameKey, type = null) {
            // Xác định API ngay lập tức
            if (type) {
                activeApi = config[gameKey][type];
            } else {
                activeApi = config[gameKey].api;
            }

            // Hiển thị giao diện
            document.getElementById("lobby").style.display = "none";
            document.getElementById("gameArea").style.display = "block";
            document.getElementById("exit-home").style.display = "block";
            document.getElementById("mainFrame").src = config[gameKey].url;
            
            // Chạy logic tool ngay
            updateLogic();
        }

        async function updateLogic() {
            if(!activeApi || document.getElementById("gameArea").style.display === "none") return;
            
            const phienEl = document.getElementById('txt-phien');
            const predictEl = document.getElementById('txt-predict');

            try {
                const res = await fetch(`https://api.allorigins.win/get?url=${encodeURIComponent(activeApi)}&t=${Date.now()}`);
                const data = await res.json();
                const json = JSON.parse(data.contents);
                
                const pID = json.phien || json.Phien || json.phien_tiep_theo || json.id;
                const prediction = json.du_doan || json.ketqua || json.kq;

                if (pID && pID !== lastPhien) {
                    lastPhien = pID;
                    predictEl.innerText = "WAIT...";
                    predictEl.className = "info-predict res-wait";
                    
                    setTimeout(() => {
                        phienEl.innerText = `Phiên: #${parseInt(pID) + 1}`;
                        if (prediction) {
                            let resTxt = prediction.toUpperCase();
                            predictEl.innerText = resTxt;
                            predictEl.className = "info-predict " + (resTxt.includes("TAI") || resTxt.includes("TÀI") ? "res-tai" : "res-xiu");
                        }
                    }, 1000);
                }
            } catch (e) { console.warn("API Error"); }
        }

        // --- KÉO THẢ ---
        const rb = document.getElementById("robot-container");
        let isDrag = false, ox, oy;
        rb.onmousedown = rb.ontouchstart = (e) => {
            isDrag = true; 
            const c = e.touches ? e.touches[0] : e;
            ox = c.clientX - rb.offsetLeft; 
            oy = c.clientY - rb.offsetTop;
        };
        window.onmousemove = window.ontouchmove = (e) => {
            if (!isDrag) return; 
            const c = e.touches ? e.touches[0] : e;
            rb.style.left = (c.clientX - ox) + "px"; 
            rb.style.top = (c.clientY - oy) + "px";
        };
        window.onmouseup = window.ontouchend = () => isDrag = false;

        // --- TUYẾT RƠI (60 FPS) ---
        const canvas = document.getElementById('snow-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        function resize() { canvas.width = window.innerWidth; canvas.height = window.innerHeight; }
        window.onresize = resize; resize();

        class Snowflake {
            constructor() { this.reset(); this.y = Math.random() * canvas.height; }
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = -10;
                this.size = Math.random() * 3 + 1;
                this.speed = Math.random() * 1 + 0.5;
                this.vx = Math.random() * 1 - 0.5;
            }
            draw() {
                ctx.fillStyle = "rgba(255, 255, 255, 0.7)";
                ctx.beginPath(); ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2); ctx.fill();
            }
            update() {
                this.y += this.speed; this.x += this.vx;
                if (this.y > canvas.height) this.reset();
            }
        }
        for(let i = 0; i < 60; i++) particles.push(new Snowflake());
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => { p.update(); p.draw(); });
            requestAnimationFrame(animate);
        }
        animate();

        setInterval(updateLogic, 4000);
    </script>
</body>
</html>
