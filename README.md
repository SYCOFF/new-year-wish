# new-year-wish
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>2026 | Our New Chapter</title>
    
    <!-- Dependencies -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@200;400;700&family=Cormorant+Garamond:italic,wght@600&display=swap" rel="stylesheet">

    <style>
        :root {
            --bg: #030303;
            --accent: #e2b07e;
            --text-bright: #ffffff;
            --text-soft: rgba(255, 255, 255, 0.6);
            --glass: rgba(255, 255, 255, 0.03);
            --border: rgba(255, 255, 255, 0.08);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            background-color: var(--bg);
            color: var(--text-bright);
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* Cinematic Background Elements */
        .bg-elements {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            overflow: hidden;
        }

        .orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.4;
        }

        /* The Experience Wrapper */
        #experience-wrapper {
            display: none; /* Shown after start */
        }

        /* Start Screen */
        #entry-screen {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            background: radial-gradient(circle at center, #111 0%, #000 100%);
        }

        .start-btn {
            background: none;
            border: 1px solid var(--accent);
            color: var(--accent);
            padding: 1.5rem 3rem;
            font-size: 1rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.5s cubic-bezier(0.2, 1, 0.3, 1);
            position: relative;
        }

        .start-btn:hover {
            background: var(--accent);
            color: black;
            box-shadow: 0 0 30px rgba(226, 176, 126, 0.3);
        }

        /* Sections */
        section {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 5vw;
            position: relative;
        }

        .glass-box {
            background: var(--glass);
            backdrop-filter: blur(20px);
            border: 1px solid var(--border);
            padding: 4rem;
            border-radius: 40px;
            max-width: 800px;
            text-align: center;
        }

        /* Typography */
        h1 {
            font-size: clamp(2rem, 8vw, 5rem);
            font-weight: 200;
            letter-spacing: -2px;
            margin-bottom: 2rem;
        }

        .serif {
            font-family: 'Cormorant Garamond', serif;
            font-style: italic;
            color: var(--accent);
        }

        p {
            font-size: 1.2rem;
            color: var(--text-soft);
            max-width: 500px;
            margin: 0 auto;
        }

        /* Countdown */
        .timer {
            display: flex;
            gap: 2rem;
            margin-top: 3rem;
        }

        .timer-unit {
            text-align: center;
        }

        .timer-val {
            display: block;
            font-size: 3rem;
            font-weight: 700;
            color: var(--accent);
        }

        .timer-label {
            font-size: 0.7rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            opacity: 0.5;
        }

        /* Fireworks Overlay */
        #fw-canvas {
            position: fixed;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: 100;
        }

        /* Utility */
        .reveal { opacity: 0; transform: translateY(30px); }
        
        .preview-trigger {
            position: fixed;
            bottom: 20px;
            left: 20px;
            font-size: 10px;
            opacity: 0.3;
            cursor: pointer;
            z-index: 1000;
            color: white;
            text-decoration: underline;
        }
    </style>
</head>
<body>

    <!-- Background Orbs -->
    <div class="bg-elements">
        <div class="orb" style="width: 400px; height: 400px; background: #2e1a47; top: -10%; left: -10%;"></div>
        <div class="orb" style="width: 300px; height: 300px; background: #1a2e47; bottom: 10%; right: -5%;"></div>
        <div class="orb" style="width: 250px; height: 250px; background: #471a1a; top: 40%; left: 30%;"></div>
    </div>

    <!-- 1. Entry Screen -->
    <div id="entry-screen">
        <div class="reveal">
            <h2 style="font-weight: 200; margin-bottom: 2rem; letter-spacing: 10px;">HELLO MY LOVE</h2>
            <button class="start-btn" onclick="initExperience()">Begin Journey</button>
        </div>
    </div>

    <canvas id="fw-canvas"></canvas>

    <!-- 2. Main Experience -->
    <div id="experience-wrapper">
        
        <!-- Chapter 1: Reflection -->
        <section id="reflection">
            <div class="glass-box reveal">
                <h1 class="serif">2025 was beautiful...</h1>
                <p>Because every single day began and ended with the thought of you. You've turned ordinary moments into my favorite memories.</p>
            </div>
        </section>

        <!-- Chapter 2: The Wait -->
        <section id="countdown">
            <div class="reveal" style="text-align: center;">
                <h1 style="margin-bottom: 0.5rem;">Almost there.</h1>
                <p>Counting every heartbeat until the new year begins with you.</p>
                
                <div class="timer">
                    <div class="timer-unit"><span class="timer-val" id="days">00</span><span class="timer-label">Days</span></div>
                    <div class="timer-unit"><span class="timer-val" id="hours">00</span><span class="timer-label">Hrs</span></div>
                    <div class="timer-unit"><span class="timer-val" id="mins">00</span><span class="timer-label">Min</span></div>
                    <div class="timer-unit"><span class="timer-val" id="secs">00</span><span class="timer-label">Sec</span></div>
                </div>
            </div>
        </section>

        <!-- Chapter 3: The Climax (Hidden until 2026) -->
        <section id="finale" style="display: none;">
            <div class="glass-box" style="border-color: var(--accent);">
                <h1 class="serif" style="font-size: 6rem;">2026</h1>
                <h2 style="letter-spacing: 5px; font-weight: 400; margin-bottom: 2rem;">HAPPY NEW YEAR!</h2>
                <p style="color: white; font-size: 1.4rem;">To the person who makes my world complete: May this year be as bright and beautiful as your smile. I love you.</p>
            </div>
        </section>

    </div>

    <!-- Audio (Silent by default, starts on click) -->
    <audio id="bg-music" loop>
        <source src="https://assets.mixkit.co/music/preview/mixkit-beautiful-dream-493.mp3" type="audio/mpeg">
    </audio>

    <div class="preview-trigger" onclick="triggerFinale()">[ Dev Mode: Force 2026 Finale ]</div>

    <script>
        // Initial Animation
        gsap.to("#entry-screen .reveal", { opacity: 1, y: 0, duration: 1.5, ease: "power4.out" });

        function initExperience() {
            // Audio Playback
            const audio = document.getElementById('bg-music');
            audio.volume = 0.4;
            audio.play().catch(e => console.log("Audio play blocked"));

            // Transition Screens
            gsap.to("#entry-screen", { 
                opacity: 0, 
                duration: 1, 
                onComplete: () => {
                    document.getElementById('entry-screen').style.display = 'none';
                    document.getElementById('experience-wrapper').style.display = 'block';
                    startScrollAnimations();
                } 
            });
        }

        function startScrollAnimations() {
            gsap.registerPlugin(ScrollTrigger);

            // Animate items on scroll
            gsap.utils.toArray(".reveal").forEach((elem) => {
                gsap.to(elem, {
                    scrollTrigger: {
                        trigger: elem,
                        start: "top 80%",
                        toggleActions: "play none none none"
                    },
                    opacity: 1,
                    y: 0,
                    duration: 1.5,
                    ease: "power4.out"
                });
            });

            // Parallax Orbs
            gsap.to(".orb", {
                y: -100,
                scrollTrigger: {
                    trigger: "body",
                    scrub: 1
                }
            });
        }

        // Countdown Logic
        const target = new Date("January 1, 2026 00:00:00").getTime();

        const timerInterval = setInterval(() => {
            const now = new Date().getTime();
            const diff = target - now;

            const d = Math.floor(diff / (1000 * 60 * 60 * 24));
            const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
            const s = Math.floor((diff % (1000 * 60)) / 1000);

            document.getElementById('days').innerHTML = d;
            document.getElementById('hours').innerHTML = h;
            document.getElementById('mins').innerHTML = m;
            document.getElementById('secs').innerHTML = s;

            if (diff <= 0) {
                clearInterval(timerInterval);
                triggerFinale();
            }
        }, 1000);

        // Celebration & Fireworks
        function triggerFinale() {
            document.getElementById('countdown').style.display = 'none';
            const finale = document.getElementById('finale');
            finale.style.display = 'flex';
            gsap.from(finale, { opacity: 0, scale: 0.9, duration: 2, ease: "elastic.out(1, 0.3)" });
            
            initFireworks();
            window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
        }

        function initFireworks() {
            const canvas = document.getElementById('fw-canvas');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;

            class Firework {
                constructor() {
                    this.x = Math.random() * canvas.width;
                    this.y = canvas.height;
                    this.targetY = Math.random() * (canvas.height / 2);
                    this.color = `hsl(${Math.random() * 360}, 100%, 70%)`;
                    this.particles = [];
                    this.dead = false;
                }
                update() {
                    if (this.y > this.targetY) {
                        this.y -= 8;
                    } else if (this.particles.length === 0) {
                        for (let i = 0; i < 50; i++) {
                            this.particles.push({
                                x: this.x,
                                y: this.y,
                                vx: Math.cos(i) * Math.random() * 5,
                                vy: Math.sin(i) * Math.random() * 5,
                                alpha: 1
                            });
                        }
                    }
                    this.particles.forEach(p => {
                        p.x += p.vx;
                        p.y += p.vy;
                        p.alpha -= 0.01;
                    });
                    this.particles = this.particles.filter(p => p.alpha > 0);
                    if (this.y <= this.targetY && this.particles.length === 0) this.dead = true;
                }
                draw() {
                    if (this.y > this.targetY) {
                        ctx.fillStyle = this.color;
                        ctx.fillRect(this.x, this.y, 3, 3);
                    }
                    this.particles.forEach(p => {
                        ctx.fillStyle = this.color;
                        ctx.globalAlpha = p.alpha;
                        ctx.fillRect(p.x, p.y, 2, 2);
                    });
                    ctx.globalAlpha = 1;
                }
            }

            let fireworks = [];
            function loop() {
                ctx.fillStyle = 'rgba(0,0,0,0.1)';
                ctx.fillRect(0,0,canvas.width, canvas.height);
                if (Math.random() < 0.05) fireworks.push(new Firework());
                fireworks.forEach((f, i) => {
                    f.update();
                    f.draw();
                    if (f.dead) fireworks.splice(i, 1);
                });
                requestAnimationFrame(loop);
            }
            loop();
        }
    </script>
</body>
</html>
