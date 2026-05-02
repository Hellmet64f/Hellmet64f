<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>Mauro de Souza — Digital Terminal</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Share+Tech+Mono&family=Rajdhani:wght@300;400;600;700&display=swap" rel="stylesheet"/>
<style>
*{margin:0;padding:0;box-sizing:border-box;}
:root{
  --neon-cyan:#00f5ff;
  --neon-pink:#ff0099;
  --neon-purple:#bf00ff;
  --neon-green:#00ff88;
  --neon-amber:#ffb800;
  --dark:#05050f;
  --dark2:#0a0a1a;
  --dark3:#0f0f28;
  --panel:#0d0d22;
  --panel2:#12122a;
  --text:#c8d6e5;
  --text2:#8899aa;
}
html{scroll-behavior:smooth;}
body{
  background:var(--dark);
  color:var(--text);
  font-family:'Rajdhani',sans-serif;
  font-size:16px;
  line-height:1.6;
  overflow-x:hidden;
}

/* SCANLINES */
body::before{
  content:'';
  position:fixed;
  top:0;left:0;right:0;bottom:0;
  background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,245,255,0.015) 2px,rgba(0,245,255,0.015) 4px);
  pointer-events:none;
  z-index:1000;
}

/* PARTICLES BG */
#particles{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none;}

/* GRID BACKGROUND */
.grid-bg{
  position:fixed;top:0;left:0;width:100%;height:100%;
  background-image:
    linear-gradient(rgba(0,245,255,0.04) 1px,transparent 1px),
    linear-gradient(90deg,rgba(0,245,255,0.04) 1px,transparent 1px);
  background-size:60px 60px;
  z-index:0;pointer-events:none;
}

/* MAIN WRAPPER */
.wrapper{position:relative;z-index:1;max-width:1100px;margin:0 auto;padding:0 20px;}

/* ===== HERO SECTION ===== */
.hero{
  min-height:100vh;display:flex;align-items:center;justify-content:center;
  flex-direction:column;text-align:center;padding:60px 20px;
  position:relative;
}

/* ANIME AVATAR */
.avatar-wrap{
  position:relative;width:180px;height:180px;margin:0 auto 40px;
}
.avatar-ring{
  position:absolute;inset:-10px;border-radius:50%;
  border:2px solid transparent;
  background:linear-gradient(135deg,var(--neon-cyan),var(--neon-pink),var(--neon-purple)) border-box;
  animation:spin 8s linear infinite;
}
.avatar-ring2{
  position:absolute;inset:-20px;border-radius:50%;
  border:1px solid rgba(0,245,255,0.2);
  animation:spin 14s linear infinite reverse;
}
.avatar-ring::before,.avatar-ring2::before{
  content:'';position:absolute;top:-2px;left:50%;width:8px;height:8px;
  background:var(--neon-cyan);border-radius:50%;
  box-shadow:0 0 10px var(--neon-cyan),0 0 20px var(--neon-cyan);
  transform:translateX(-50%);
}
.avatar-inner{
  width:180px;height:180px;border-radius:50%;overflow:hidden;
  background:linear-gradient(135deg,#1a1a3e,#2d0050);
  display:flex;align-items:center;justify-content:center;
  position:relative;border:3px solid rgba(0,245,255,0.3);
}
/* CSS Anime Character */
.anime-char{
  width:120px;height:160px;position:relative;
}
/* Body */
.anime-char .body{
  position:absolute;bottom:0;left:50%;transform:translateX(-50%);
  width:70px;height:70px;
  background:linear-gradient(180deg,#1a1a4e,#0a0a2a);
  border-radius:8px 8px 0 0;
}
.anime-char .body::before{
  content:'';position:absolute;top:5px;left:50%;transform:translateX(-50%);
  width:30px;height:4px;
  background:var(--neon-cyan);border-radius:2px;
  box-shadow:0 0 8px var(--neon-cyan);
}
/* Head */
.anime-char .head{
  position:absolute;top:0;left:50%;transform:translateX(-50%);
  width:64px;height:64px;
  background:linear-gradient(160deg,#ffe4c4,#f4c89a);
  border-radius:50% 50% 45% 45%;
  border:2px solid rgba(0,245,255,0.4);
}
/* Hair */
.anime-char .hair{
  position:absolute;top:-8px;left:50%;transform:translateX(-50%);
  width:72px;height:42px;
  background:linear-gradient(180deg,#1a0030,#3d0070);
  border-radius:50% 50% 0 0;
  overflow:hidden;
}
.anime-char .hair::before{
  content:'';position:absolute;bottom:0;right:-6px;
  width:20px;height:50px;
  background:#1a0030;
  border-radius:50%;
  transform:rotate(10deg);
}
.anime-char .hair::after{
  content:'';position:absolute;bottom:-5px;left:-4px;
  width:16px;height:40px;
  background:#1a0030;
  border-radius:50%;
  transform:rotate(-15deg);
}
/* Eyes */
.anime-char .eyes{
  position:absolute;top:26px;left:50%;transform:translateX(-50%);
  width:50px;display:flex;justify-content:space-between;
}
.anime-char .eye{
  width:14px;height:16px;
  background:var(--neon-cyan);
  border-radius:50% 50% 50% 50%;
  position:relative;
  animation:blink 4s ease-in-out infinite;
  box-shadow:0 0 6px var(--neon-cyan);
}
.anime-char .eye::before{
  content:'';position:absolute;top:2px;left:2px;
  width:5px;height:5px;background:white;border-radius:50%;
}
/* Ear pieces / tech accessories */
.anime-char .tech-left,.anime-char .tech-right{
  position:absolute;top:22px;
  width:12px;height:20px;
  background:var(--neon-purple);
  border-radius:2px;
  box-shadow:0 0 8px var(--neon-purple);
}
.anime-char .tech-left{left:-2px;}
.anime-char .tech-right{right:-2px;}

@keyframes blink{0%,90%,100%{transform:scaleY(1)}93%{transform:scaleY(0.1)}}
@keyframes spin{to{transform:rotate(360deg)}}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-12px)}}

.avatar-inner > *{animation:float 4s ease-in-out infinite;}

/* STATUS BADGE */
.status-badge{
  position:absolute;bottom:8px;right:8px;
  background:var(--dark2);
  border:1px solid var(--neon-green);
  border-radius:20px;padding:3px 12px;
  font-family:'Share Tech Mono',monospace;
  font-size:10px;color:var(--neon-green);
  box-shadow:0 0 10px rgba(0,255,136,0.3);
  white-space:nowrap;
}
.status-dot{
  display:inline-block;width:6px;height:6px;
  background:var(--neon-green);border-radius:50%;
  margin-right:5px;
  box-shadow:0 0 6px var(--neon-green);
  animation:pulse 2s ease-in-out infinite;
}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:0.3}}

/* GLITCH TITLE */
.glitch-wrap{position:relative;margin-bottom:10px;}
.hero-title{
  font-family:'Orbitron',monospace;
  font-size:clamp(28px,6vw,64px);
  font-weight:900;
  color:white;
  text-transform:uppercase;
  letter-spacing:4px;
  position:relative;
}
.hero-title::before,.hero-title::after{
  content:attr(data-text);
  position:absolute;top:0;left:0;right:0;
}
.hero-title::before{
  color:var(--neon-cyan);
  clip-path:polygon(0 0,100% 0,100% 33%,0 33%);
  animation:glitch1 3s steps(1) infinite;
}
.hero-title::after{
  color:var(--neon-pink);
  clip-path:polygon(0 66%,100% 66%,100% 100%,0 100%);
  animation:glitch2 3s steps(1) infinite;
}
@keyframes glitch1{
  0%,91%,100%{transform:translate(0)}
  92%{transform:translate(-3px,1px)}
  93%{transform:translate(3px,-1px)}
  94%,95%{transform:translate(0)}
}
@keyframes glitch2{
  0%,91%,100%{transform:translate(0)}
  92%{transform:translate(3px,-1px)}
  93%{transform:translate(-3px,1px)}
  94%,95%{transform:translate(0)}
}

.hero-sub{
  font-family:'Share Tech Mono',monospace;
  font-size:clamp(12px,2vw,16px);
  color:var(--neon-cyan);
  margin-bottom:16px;
  letter-spacing:2px;
}
.hero-desc{
  max-width:600px;margin:0 auto 30px;
  font-size:17px;color:var(--text2);
  font-weight:300;
}

/* TYPING CURSOR */
.typing{
  font-family:'Share Tech Mono',monospace;
  font-size:14px;color:var(--neon-green);
  letter-spacing:1px;
}
.typing::after{
  content:'|';animation:blink-cursor 0.8s step-end infinite;
}
@keyframes blink-cursor{50%{opacity:0}}

/* SOCIAL BADGES */
.social-row{
  display:flex;gap:12px;flex-wrap:wrap;justify-content:center;margin-top:20px;
}
.social-btn{
  font-family:'Share Tech Mono',monospace;
  font-size:11px;
  padding:8px 18px;
  border-radius:4px;
  text-decoration:none;
  letter-spacing:1px;
  text-transform:uppercase;
  transition:all 0.2s;
  position:relative;
  overflow:hidden;
}
.social-btn::before{
  content:'';position:absolute;inset:0;
  background:currentColor;opacity:0;
  transition:opacity 0.2s;
}
.social-btn:hover::before{opacity:0.1;}
.social-btn:hover{transform:translateY(-2px);}
.sb-cyan{border:1px solid var(--neon-cyan);color:var(--neon-cyan);box-shadow:0 0 10px rgba(0,245,255,0.2);}
.sb-pink{border:1px solid var(--neon-pink);color:var(--neon-pink);box-shadow:0 0 10px rgba(255,0,153,0.2);}
.sb-purple{border:1px solid var(--neon-purple);color:var(--neon-purple);box-shadow:0 0 10px rgba(191,0,255,0.2);}
.sb-amber{border:1px solid var(--neon-amber);color:var(--neon-amber);box-shadow:0 0 10px rgba(255,184,0,0.2);}

/* SCROLL INDICATOR */
.scroll-hint{
  position:absolute;bottom:30px;left:50%;transform:translateX(-50%);
  font-family:'Share Tech Mono',monospace;font-size:11px;
  color:var(--text2);letter-spacing:2px;
  display:flex;flex-direction:column;align-items:center;gap:8px;
}
.scroll-arrow{
  width:20px;height:30px;border:1px solid var(--neon-cyan);
  border-radius:10px;position:relative;
  box-shadow:0 0 8px rgba(0,245,255,0.2);
}
.scroll-arrow::after{
  content:'';position:absolute;top:6px;left:50%;transform:translateX(-50%);
  width:4px;height:4px;background:var(--neon-cyan);border-radius:50%;
  animation:scroll-down 1.5s ease-in-out infinite;
}
@keyframes scroll-down{0%{top:6px;opacity:1}100%{top:18px;opacity:0}}

/* ===== SECTION STYLES ===== */
section{padding:80px 0;}
.section-header{
  text-align:center;margin-bottom:60px;
}
.section-label{
  font-family:'Share Tech Mono',monospace;
  font-size:12px;color:var(--neon-cyan);
  letter-spacing:4px;text-transform:uppercase;
  margin-bottom:12px;
}
.section-title{
  font-family:'Orbitron',monospace;
  font-size:clamp(20px,4vw,36px);
  font-weight:700;color:white;
  text-transform:uppercase;letter-spacing:2px;
  position:relative;display:inline-block;
}
.section-title::after{
  content:'';display:block;height:2px;margin-top:10px;
  background:linear-gradient(90deg,var(--neon-cyan),var(--neon-pink),transparent);
  border-radius:1px;
}
.section-subtitle{font-size:15px;color:var(--text2);margin-top:12px;}

/* DIVIDER */
.divider{
  height:1px;
  background:linear-gradient(90deg,transparent,var(--neon-cyan),transparent);
  margin:0;opacity:0.3;
}

/* ===== ABOUT SECTION ===== */
.about-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:40px;align-items:start;
}
@media(max-width:700px){.about-grid{grid-template-columns:1fr;}}

.terminal-box{
  background:var(--panel);
  border:1px solid rgba(0,245,255,0.2);
  border-radius:8px;
  overflow:hidden;
  font-family:'Share Tech Mono',monospace;
}
.terminal-bar{
  background:var(--panel2);
  padding:10px 16px;
  display:flex;align-items:center;gap:8px;
  border-bottom:1px solid rgba(0,245,255,0.1);
}
.dot-red,.dot-yellow,.dot-green{width:10px;height:10px;border-radius:50%;}
.dot-red{background:#ff5f57;}
.dot-yellow{background:#febc2e;}
.dot-green{background:#28c840;}
.terminal-title{
  font-size:11px;color:var(--text2);
  margin-left:8px;letter-spacing:1px;
}
.terminal-body{padding:20px;font-size:13px;line-height:1.9;color:var(--neon-green);}
.t-comment{color:var(--text2);}
.t-key{color:var(--neon-cyan);}
.t-val{color:var(--neon-amber);}
.t-str{color:var(--neon-pink);}
.t-num{color:#ff7eb3;}

.timeline-list{display:flex;flex-direction:column;gap:24px;}
.tl-item{
  display:flex;gap:16px;
  padding:16px;
  background:var(--panel);
  border:1px solid rgba(0,245,255,0.1);
  border-radius:8px;
  border-left:3px solid var(--neon-cyan);
  transition:all 0.3s;
  position:relative;
}
.tl-item:hover{
  border-left-color:var(--neon-pink);
  background:var(--panel2);
  transform:translateX(4px);
}
.tl-year{
  font-family:'Orbitron',monospace;
  font-size:10px;color:var(--neon-cyan);
  white-space:nowrap;padding-top:3px;
  min-width:80px;
}
.tl-content{}
.tl-role{font-weight:700;font-size:16px;color:white;}
.tl-company{font-size:13px;color:var(--neon-purple);margin-bottom:4px;font-family:'Share Tech Mono',monospace;}
.tl-desc{font-size:13px;color:var(--text2);}

/* ===== TECH STACK ===== */
.stack-section{background:var(--dark2);}
.stack-categories{display:flex;flex-direction:column;gap:40px;}
.stack-cat-title{
  font-family:'Share Tech Mono',monospace;
  font-size:12px;color:var(--neon-amber);
  letter-spacing:3px;text-transform:uppercase;
  margin-bottom:16px;
}
.tech-grid{
  display:flex;flex-wrap:wrap;gap:10px;
}
.tech-chip{
  display:flex;align-items:center;gap:8px;
  padding:8px 14px;
  background:var(--panel);
  border:1px solid rgba(255,255,255,0.08);
  border-radius:6px;
  font-size:13px;font-weight:600;color:var(--text);
  transition:all 0.25s;
  cursor:default;
  position:relative;overflow:hidden;
}
.tech-chip::before{
  content:'';position:absolute;left:0;top:0;bottom:0;width:2px;
  background:var(--chip-color,var(--neon-cyan));
}
.tech-chip:hover{
  border-color:var(--chip-color,var(--neon-cyan));
  color:var(--chip-color,var(--neon-cyan));
  background:var(--panel2);
  transform:translateY(-2px);
  box-shadow:0 4px 20px rgba(0,0,0,0.3);
}
.tech-dot{
  width:8px;height:8px;border-radius:50%;
  background:var(--chip-color,var(--neon-cyan));
  flex-shrink:0;
}

/* ===== PROJECTS (STEAM-LIKE) ===== */
.projects-section{background:var(--dark);}
.steam-shelf{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(320px,1fr));
  gap:24px;
}
.steam-card{
  background:var(--panel);
  border:1px solid rgba(255,255,255,0.07);
  border-radius:10px;
  overflow:hidden;
  transition:all 0.3s cubic-bezier(0.23,1,0.32,1);
  cursor:pointer;
  position:relative;
}
.steam-card:hover{
  border-color:var(--card-accent,var(--neon-cyan));
  transform:translateY(-6px);
  box-shadow:0 20px 60px rgba(0,0,0,0.5),0 0 30px rgba(0,245,255,0.1);
}
.steam-banner{
  height:160px;position:relative;overflow:hidden;
  background:var(--panel2);
}
/* Animated project banners (CSS art) */
.sb-1{background:linear-gradient(135deg,#0a001f,#1a004a,#0d1b3e);}
.sb-2{background:linear-gradient(135deg,#001f0a,#004a1a,#0d3e1b);}
.sb-3{background:linear-gradient(135deg,#1f000a,#4a001a,#3e0d1b);}
.sb-4{background:linear-gradient(135deg,#1a0f00,#3a2200,#2e1a00);}

.sb-glow{
  position:absolute;inset:0;
  display:flex;align-items:center;justify-content:center;
}
.sb-glow::before{
  content:'';position:absolute;
  width:200px;height:200px;border-radius:50%;
  background:var(--card-accent,var(--neon-cyan));
  opacity:0.08;filter:blur(60px);
  animation:breathe 4s ease-in-out infinite;
}
@keyframes breathe{0%,100%{opacity:0.06;transform:scale(0.9)}50%{opacity:0.12;transform:scale(1.1)}}

/* mini CSS art per card */
.mini-art{
  position:relative;width:100%;height:100%;
  display:flex;align-items:center;justify-content:center;
}
.hex-grid{
  display:grid;grid-template-columns:repeat(3,30px);gap:6px;
  opacity:0.5;
}
.hex{
  width:24px;height:24px;
  background:var(--card-accent);
  clip-path:polygon(25% 0%,75% 0%,100% 50%,75% 100%,25% 100%,0% 50%);
  animation:hex-pulse 2s ease-in-out infinite;
}
.hex:nth-child(2){animation-delay:0.2s;}
.hex:nth-child(3){animation-delay:0.4s;}
.hex:nth-child(4){animation-delay:0.6s;}
.hex:nth-child(5){animation-delay:0.8s;}
.hex:nth-child(6){animation-delay:1.0s;}
.hex:nth-child(7){animation-delay:1.2s;}
.hex:nth-child(8){animation-delay:1.4s;}
.hex:nth-child(9){animation-delay:1.6s;}
@keyframes hex-pulse{0%,100%{opacity:0.3}50%{opacity:1}}

.circuit-lines{
  position:absolute;inset:0;
  background-image:
    linear-gradient(var(--card-accent) 1px,transparent 1px),
    linear-gradient(90deg,var(--card-accent) 1px,transparent 1px);
  background-size:30px 30px;
  opacity:0.06;
}

/* Project card tags */
.steam-tags{
  position:absolute;top:10px;right:10px;
  display:flex;gap:6px;flex-wrap:wrap;justify-content:flex-end;
}
.steam-tag{
  font-family:'Share Tech Mono',monospace;
  font-size:9px;padding:3px 8px;
  border-radius:3px;
  background:rgba(0,0,0,0.6);
  border:1px solid var(--card-accent);
  color:var(--card-accent);
  letter-spacing:1px;text-transform:uppercase;
  backdrop-filter:blur(4px);
}

/* Project icon */
.proj-icon-wrap{
  position:absolute;bottom:-20px;left:20px;
  width:50px;height:50px;
  border-radius:8px;
  border:2px solid var(--card-accent);
  background:var(--dark);
  display:flex;align-items:center;justify-content:center;
  font-size:24px;
  box-shadow:0 0 20px rgba(0,0,0,0.8);
  z-index:2;
}

/* Steam card body */
.steam-body{
  padding:30px 20px 20px;
}
.steam-proj-title{
  font-family:'Orbitron',monospace;
  font-size:15px;font-weight:700;
  color:white;letter-spacing:1px;
  margin-bottom:6px;
}
.steam-proj-sub{
  font-family:'Share Tech Mono',monospace;
  font-size:11px;color:var(--card-accent);
  letter-spacing:2px;text-transform:uppercase;
  margin-bottom:10px;
  opacity:0.8;
}
.steam-proj-desc{
  font-size:13px;color:var(--text2);
  line-height:1.6;margin-bottom:16px;
}
.steam-stats{
  display:flex;gap:16px;margin-bottom:16px;
}
.steam-stat{
  font-family:'Share Tech Mono',monospace;
  font-size:11px;color:var(--text2);
}
.steam-stat span{color:var(--neon-green);font-weight:700;}

/* progress bar style lang indicator */
.lang-bar-wrap{margin-bottom:16px;}
.lang-label{display:flex;justify-content:space-between;margin-bottom:4px;font-size:11px;}
.lang-bar{height:4px;background:rgba(255,255,255,0.05);border-radius:2px;overflow:hidden;}
.lang-fill{height:100%;border-radius:2px;animation:fill-in 1.5s ease-out forwards;}
@keyframes fill-in{from{width:0}}

.steam-btns{display:flex;gap:10px;flex-wrap:wrap;}
.steam-btn{
  flex:1;
  font-family:'Share Tech Mono',monospace;
  font-size:11px;padding:9px 14px;
  border-radius:4px;text-decoration:none;
  letter-spacing:1px;text-transform:uppercase;
  text-align:center;transition:all 0.2s;
  border:1px solid var(--card-accent);
  color:var(--card-accent);
  background:transparent;cursor:pointer;
  white-space:nowrap;
}
.steam-btn:hover{
  background:var(--card-accent);
  color:var(--dark);
  font-weight:700;
}
.steam-btn.filled{
  background:var(--card-accent);color:var(--dark);font-weight:700;
}
.steam-btn.filled:hover{opacity:0.85;}

/* REVIEW STARS */
.steam-score{
  position:absolute;top:10px;left:10px;
  font-family:'Share Tech Mono',monospace;
  font-size:10px;
  background:rgba(0,0,0,0.7);
  border:1px solid rgba(255,255,255,0.1);
  padding:4px 10px;
  border-radius:3px;
  backdrop-filter:blur(4px);
  color:var(--neon-amber);
}

/* ===== STATS SECTION ===== */
.stats-section{background:var(--dark2);}
.stats-grid{
  display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
  gap:20px;margin-bottom:40px;
}
.stat-card{
  background:var(--panel);
  border:1px solid rgba(255,255,255,0.07);
  border-radius:8px;padding:24px;
  text-align:center;position:relative;overflow:hidden;
  transition:all 0.3s;
}
.stat-card::before{
  content:'';position:absolute;bottom:0;left:0;right:0;
  height:2px;background:var(--stat-color,var(--neon-cyan));
  box-shadow:0 0 10px var(--stat-color,var(--neon-cyan));
}
.stat-card:hover{transform:translateY(-4px);background:var(--panel2);}
.stat-num{
  font-family:'Orbitron',monospace;
  font-size:40px;font-weight:900;
  color:var(--stat-color,var(--neon-cyan));
  line-height:1;margin-bottom:8px;
}
.stat-label{font-size:13px;color:var(--text2);font-family:'Share Tech Mono',monospace;letter-spacing:1px;}

/* CONTRIB GRID */
.contrib-wrap{
  background:var(--panel);border:1px solid rgba(0,245,255,0.1);
  border-radius:8px;padding:20px;
}
.contrib-title{
  font-family:'Share Tech Mono',monospace;font-size:12px;
  color:var(--neon-cyan);letter-spacing:2px;margin-bottom:16px;
  text-transform:uppercase;
}
.contrib-grid{
  display:flex;gap:3px;flex-wrap:wrap;
}
.contrib-week{display:flex;flex-direction:column;gap:3px;}
.contrib-cell{
  width:12px;height:12px;border-radius:2px;
  background:rgba(255,255,255,0.04);
  transition:all 0.2s;
}
.contrib-cell:hover{transform:scale(1.4);}
.cc-0{background:rgba(255,255,255,0.04);}
.cc-1{background:rgba(0,245,255,0.2);}
.cc-2{background:rgba(0,245,255,0.45);}
.cc-3{background:rgba(0,245,255,0.7);}
.cc-4{background:var(--neon-cyan);box-shadow:0 0 4px var(--neon-cyan);}

/* ===== HOBBIES ===== */
.hobbies-section{background:var(--dark);}
.hobbies-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:24px;
}
@media(max-width:600px){.hobbies-grid{grid-template-columns:1fr;}}
.hobby-card{
  background:var(--panel);
  border:1px solid rgba(255,255,255,0.07);
  border-radius:10px;padding:24px;
  border-top:3px solid var(--hobby-color,var(--neon-amber));
}
.hobby-header{
  font-family:'Orbitron',monospace;
  font-size:13px;font-weight:700;
  color:var(--hobby-color,var(--neon-amber));
  letter-spacing:2px;margin-bottom:18px;
  text-transform:uppercase;
}
.hobby-list{list-style:none;display:flex;flex-direction:column;gap:10px;}
.hobby-list li{
  font-size:14px;color:var(--text2);
  padding-left:20px;position:relative;
  transition:color 0.2s;
}
.hobby-list li::before{
  content:attr(data-icon);
  position:absolute;left:0;top:0;
  font-size:12px;
}
.hobby-list li:hover{color:var(--text);}

/* ===== FAQ ===== */
.faq-section{background:var(--dark2);}
.faq-list{display:flex;flex-direction:column;gap:16px;max-width:750px;margin:0 auto;}
.faq-item{
  background:var(--panel);
  border:1px solid rgba(0,245,255,0.1);
  border-radius:8px;
  overflow:hidden;
}
.faq-q{
  padding:16px 20px;
  font-family:'Share Tech Mono',monospace;
  font-size:13px;color:var(--neon-cyan);
  cursor:pointer;
  display:flex;justify-content:space-between;align-items:center;
  transition:background 0.2s;
}
.faq-q:hover{background:var(--panel2);}
.faq-q::before{content:'> ';color:var(--neon-green);}
.faq-arrow{color:var(--text2);transition:transform 0.3s;font-size:10px;}
.faq-a{
  padding:0 20px;max-height:0;overflow:hidden;
  transition:max-height 0.4s ease,padding 0.3s;
  font-size:14px;color:var(--text2);
  border-top:0 solid rgba(0,245,255,0.05);
}
.faq-item.open .faq-a{
  max-height:200px;padding:16px 20px;
  border-top-width:1px;
}
.faq-item.open .faq-arrow{transform:rotate(180deg);}

/* ===== FOOTER ===== */
footer{
  background:var(--dark2);
  border-top:1px solid rgba(0,245,255,0.1);
  padding:40px 20px;text-align:center;
}
.footer-ascii{
  font-family:'Share Tech Mono',monospace;
  font-size:clamp(6px,1.5vw,11px);
  color:rgba(0,245,255,0.2);
  line-height:1.3;margin-bottom:20px;
  letter-spacing:1px;
}
.footer-copy{
  font-family:'Share Tech Mono',monospace;
  font-size:11px;color:var(--text2);letter-spacing:2px;
}

/* NAV */
nav{
  position:fixed;top:0;left:0;right:0;
  z-index:500;
  padding:0 40px;
  background:rgba(5,5,15,0.85);
  backdrop-filter:blur(20px);
  border-bottom:1px solid rgba(0,245,255,0.1);
  display:flex;align-items:center;justify-content:space-between;
  height:56px;
}
.nav-logo{
  font-family:'Orbitron',monospace;
  font-size:14px;font-weight:700;
  color:var(--neon-cyan);letter-spacing:2px;
}
.nav-links{display:flex;gap:28px;list-style:none;}
.nav-links a{
  font-family:'Share Tech Mono',monospace;
  font-size:11px;color:var(--text2);text-decoration:none;
  letter-spacing:2px;text-transform:uppercase;
  transition:color 0.2s;padding:4px 0;
  border-bottom:1px solid transparent;
}
.nav-links a:hover{color:var(--neon-cyan);border-bottom-color:var(--neon-cyan);}
@media(max-width:640px){.nav-links{display:none;}}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">MS.DEV</div>
  <ul class="nav-links">
    <li><a href="#about">Sobre</a></li>
    <li><a href="#stack">Stack</a></li>
    <li><a href="#projects">Projetos</a></li>
    <li><a href="#stats">Stats</a></li>
    <li><a href="#hobbies">Hobbies</a></li>
  </ul>
</nav>

<div class="grid-bg"></div>
<canvas id="particles"></canvas>

<!-- HERO -->
<section class="hero">
  <div class="wrapper">
    <!-- Avatar -->
    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar-ring2"></div>
      <div class="avatar-inner">
        <div class="anime-char">
          <div class="hair"></div>
          <div class="head">
            <div class="tech-left"></div>
            <div class="tech-right"></div>
            <div class="eyes">
              <div class="eye"></div>
              <div class="eye"></div>
            </div>
          </div>
          <div class="body"></div>
        </div>
      </div>
      <div class="status-badge"><span class="status-dot"></span>ONLINE</div>
    </div>

    <!-- Title -->
    <div class="glitch-wrap">
      <h1 class="hero-title" data-text="MAURO DE SOUZA">MAURO DE SOUZA</h1>
    </div>
    <div class="hero-sub">// FULL-STACK DEVELOPER · CYBERPUNK ARCHITECT</div>
    <p class="hero-desc">
      Desenvolvedor apaixonado por transformar código em experiências digitais.
      TypeScript/Next.js no front · Go/Rust no back · Sempre explorando o próximo nível.
    </p>
    <div class="typing" id="typing-text"></div>

    <!-- Social -->
    <div class="social-row">
      <a href="LINK_LINKEDIN" class="social-btn sb-cyan">LinkedIn</a>
      <a href="https://github.com/maurodesouza" class="social-btn sb-purple">GitHub</a>
      <a href="LINK_TWITTER" class="social-btn sb-pink">Twitter / X</a>
      <a href="LINK_DISCORD" class="social-btn sb-amber">Discord</a>
    </div>
  </div>
  <div class="scroll-hint">
    <span>SCROLL</span>
    <div class="scroll-arrow"></div>
  </div>
</section>

<div class="divider"></div>

<!-- ABOUT -->
<section id="about">
  <div class="wrapper">
    <div class="section-header">
      <div class="section-label">// ACESSO_CONCEDIDO</div>
      <h2 class="section-title">Sobre Mim</h2>
      <p class="section-subtitle">Lendo arquivo de identidade do sistema...</p>
    </div>
    <div class="about-grid">
      <div class="terminal-box">
        <div class="terminal-bar">
          <div class="dot-red"></div><div class="dot-yellow"></div><div class="dot-green"></div>
          <span class="terminal-title">profile.json</span>
        </div>
        <div class="terminal-body">
<span class="t-comment">// Sistema de identificação pessoal</span><br>
{<br>
&nbsp;&nbsp;<span class="t-key">"nome"</span>: <span class="t-str">"Mauro de Souza"</span>,<br>
&nbsp;&nbsp;<span class="t-key">"cargo"</span>: <span class="t-str">"Senior Full-Stack Dev"</span>,<br>
&nbsp;&nbsp;<span class="t-key">"experiencia"</span>: <span class="t-num">8</span>,<br>
&nbsp;&nbsp;<span class="t-key">"localizacao"</span>: <span class="t-str">"Brasil 🇧🇷"</span>,<br>
&nbsp;&nbsp;<span class="t-key">"stack_fav"</span>: [<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="t-str">"Next.js"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="t-str">"Go"</span>,<br>
&nbsp;&nbsp;&nbsp;&nbsp;<span class="t-str">"Rust"</span><br>
&nbsp;&nbsp;],<br>
&nbsp;&nbsp;<span class="t-key">"foco"</span>: <span class="t-str">"Microserviços & DX"</span>,<br>
&nbsp;&nbsp;<span class="t-key">"aprendendo"</span>: <span class="t-str">"Flutter"</span>,<br>
&nbsp;&nbsp;<span class="t-key">"status"</span>: <span class="t-val">ONLINE</span><br>
}
        </div>
      </div>

      <div class="timeline-list">
        <div class="tl-item">
          <div class="tl-year">2022 →<br>PRESENTE</div>
          <div class="tl-content">
            <div class="tl-role">Senior Full-Stack Developer</div>
            <div class="tl-company">[ Empresa Atual ]</div>
            <div class="tl-desc">Arquitetura de microserviços Go · Liderança técnica de 4 pessoas · Lançamento do produto principal.</div>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-year">2020 →<br>2022</div>
          <div class="tl-content">
            <div class="tl-role">Desenvolvedor Back-End Pleno</div>
            <div class="tl-company">[ Empresa Anterior ]</div>
            <div class="tl-desc">APIs Python de alta escala · Integração de parceiros de pagamento · Otimização SQL.</div>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-year">2018 →<br>2020</div>
          <div class="tl-content">
            <div class="tl-role">Dev Junior & Estagiário</div>
            <div class="tl-company">[ Empresa de Início ]</div>
            <div class="tl-desc">Primeiro contato com Next.js · Manutenção de sistemas legados · Scripts de deploy.</div>
          </div>
        </div>
        <div class="tl-item">
          <div class="tl-year">2016 →<br>2018</div>
          <div class="tl-content">
            <div class="tl-role">Freelancer & Estudante</div>
            <div class="tl-company">[ Autodidata ]</div>
            <div class="tl-desc">Sites estáticos · Java autônomo · Mods de jogos.</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- TECH STACK -->
<section id="stack" class="stack-section">
  <div class="wrapper">
    <div class="section-header">
      <div class="section-label">// MÓDULOS_INSTALADOS</div>
      <h2 class="section-title">Tech Stack</h2>
      <p class="section-subtitle">Ferramentas que uso para moldar a realidade digital</p>
    </div>
    <div class="stack-categories">

      <div>
        <div class="stack-cat-title">⬡ LINGUAGENS PRINCIPAIS</div>
        <div class="tech-grid">
          <div class="tech-chip" style="--chip-color:#f7df1e"><div class="tech-dot"></div>JavaScript</div>
          <div class="tech-chip" style="--chip-color:#3178c6"><div class="tech-dot"></div>TypeScript</div>
          <div class="tech-chip" style="--chip-color:#3572a5"><div class="tech-dot"></div>Python</div>
          <div class="tech-chip" style="--chip-color:#00add8"><div class="tech-dot"></div>Go</div>
          <div class="tech-chip" style="--chip-color:#dea584"><div class="tech-dot"></div>Rust</div>
          <div class="tech-chip" style="--chip-color:#4eaa25"><div class="tech-dot"></div>Bash</div>
          <div class="tech-chip" style="--chip-color:#ed8b00"><div class="tech-dot"></div>Java</div>
        </div>
      </div>

      <div>
        <div class="stack-cat-title">⬡ FRONT-END</div>
        <div class="tech-grid">
          <div class="tech-chip" style="--chip-color:#00f5ff"><div class="tech-dot"></div>Next.js</div>
          <div class="tech-chip" style="--chip-color:#61dafb"><div class="tech-dot"></div>React</div>
          <div class="tech-chip" style="--chip-color:#38bdf8"><div class="tech-dot"></div>Tailwind CSS</div>
          <div class="tech-chip" style="--chip-color:#ff4785"><div class="tech-dot"></div>Storybook</div>
          <div class="tech-chip" style="--chip-color:#cc6699"><div class="tech-dot"></div>SASS/SCSS</div>
        </div>
      </div>

      <div>
        <div class="stack-cat-title">⬡ BACK-END & BANCO DE DADOS</div>
        <div class="tech-grid">
          <div class="tech-chip" style="--chip-color:#e0234e"><div class="tech-dot"></div>NestJS</div>
          <div class="tech-chip" style="--chip-color:#000000"><div class="tech-dot"></div>Express</div>
          <div class="tech-chip" style="--chip-color:#e535ab"><div class="tech-dot"></div>GraphQL</div>
          <div class="tech-chip" style="--chip-color:#009688"><div class="tech-dot"></div>FastAPI</div>
          <div class="tech-chip" style="--chip-color:#336791"><div class="tech-dot"></div>PostgreSQL</div>
          <div class="tech-chip" style="--chip-color:#47a248"><div class="tech-dot"></div>MongoDB</div>
          <div class="tech-chip" style="--chip-color:#dc382d"><div class="tech-dot"></div>Redis</div>
        </div>
      </div>

      <div>
        <div class="stack-cat-title">⬡ INFRA & FERRAMENTAS</div>
        <div class="tech-grid">
          <div class="tech-chip" style="--chip-color:#f05032"><div class="tech-dot"></div>Git</div>
          <div class="tech-chip" style="--chip-color:#181717"><div class="tech-dot"></div>GitHub Actions</div>
          <div class="tech-chip" style="--chip-color:#2496ed"><div class="tech-dot"></div>Docker</div>
          <div class="tech-chip" style="--chip-color:#326ce5"><div class="tech-dot"></div>Kubernetes</div>
          <div class="tech-chip" style="--chip-color:#ff9900"><div class="tech-dot"></div>AWS</div>
          <div class="tech-chip" style="--chip-color:#7b42bc"><div class="tech-dot"></div>Terraform</div>
          <div class="tech-chip" style="--chip-color:#007acc"><div class="tech-dot"></div>VS Code</div>
        </div>
      </div>

      <div>
        <div class="stack-cat-title" style="color:var(--neon-green)">🌱 ATUALMENTE APRENDENDO</div>
        <div class="tech-grid">
          <div class="tech-chip" style="--chip-color:#54c5f8"><div class="tech-dot"></div>Flutter</div>
          <div class="tech-chip" style="--chip-color:#61dafb"><div class="tech-dot"></div>React Native</div>
          <div class="tech-chip" style="--chip-color:#ffca28"><div class="tech-dot"></div>Firebase</div>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- PROJECTS (STEAM) -->
<section id="projects" class="projects-section">
  <div class="wrapper">
    <div class="section-header">
      <div class="section-label">// BIBLIOTECA_DE_PROJETOS</div>
      <h2 class="section-title">Projetos em Destaque</h2>
      <p class="section-subtitle">Explore minha biblioteca — estilo Steam</p>
    </div>

    <div class="steam-shelf">

      <!-- Card 1 -->
      <div class="steam-card" style="--card-accent:#00f5ff">
        <div class="steam-banner sb-1">
          <div class="circuit-lines"></div>
          <div class="sb-glow">
            <div class="mini-art">
              <div class="hex-grid" style="--card-accent:#00f5ff">
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
              </div>
            </div>
          </div>
          <div class="steam-score">★ 98% POSITIVO</div>
          <div class="steam-tags">
            <span class="steam-tag">Rust</span>
            <span class="steam-tag">Go</span>
            <span class="steam-tag">Auth</span>
          </div>
          <div class="proj-icon-wrap">🔐</div>
        </div>
        <div class="steam-body">
          <div class="steam-proj-title">Neo-Scribe</div>
          <div class="steam-proj-sub">Microserviço Distribuído</div>
          <p class="steam-proj-desc">Gerenciamento de tokens de autenticação. Core em Rust para criptografia, Go para a API pública. Escala para milhões de req/s.</p>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#dea584;font-family:monospace;font-size:11px">Rust</span><span style="color:var(--text2);font-size:11px">64%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:64%;background:#dea584;"></div></div>
          </div>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#00add8;font-family:monospace;font-size:11px">Go</span><span style="color:var(--text2);font-size:11px">36%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:36%;background:#00add8;"></div></div>
          </div>
          <div class="steam-stats">
            <div class="steam-stat">Stars: <span>247</span></div>
            <div class="steam-stat">Forks: <span>38</span></div>
            <div class="steam-stat">Issues: <span>2</span></div>
          </div>
          <div class="steam-btns">
            <a href="LINK_PROJETO_1_GITHUB" class="steam-btn filled">▶ Ver Código</a>
            <a href="LINK_DEMO_1" class="steam-btn">◈ Demo Live</a>
          </div>
        </div>
      </div>

      <!-- Card 2 -->
      <div class="steam-card" style="--card-accent:#00ff88">
        <div class="steam-banner sb-2">
          <div class="circuit-lines"></div>
          <div class="sb-glow">
            <div class="mini-art">
              <div class="hex-grid" style="--card-accent:#00ff88">
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
              </div>
            </div>
          </div>
          <div class="steam-score">★ 95% POSITIVO</div>
          <div class="steam-tags">
            <span class="steam-tag" style="border-color:#00ff88;color:#00ff88">Next.js</span>
            <span class="steam-tag" style="border-color:#00ff88;color:#00ff88">GraphQL</span>
          </div>
          <div class="proj-icon-wrap" style="border-color:#00ff88">☁️</div>
        </div>
        <div class="steam-body">
          <div class="steam-proj-title">Kumo-Front</div>
          <div class="steam-proj-sub">Plataforma Colaborativa</div>
          <p class="steam-proj-desc">Dashboard em tempo real para times de desenvolvimento. Next.js + GraphQL + Tailwind. CI/CD via GitHub Actions.</p>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#3178c6;font-family:monospace;font-size:11px">TypeScript</span><span style="color:var(--text2);font-size:11px">71%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:71%;background:#3178c6;"></div></div>
          </div>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#f1e05a;font-family:monospace;font-size:11px">CSS/SCSS</span><span style="color:var(--text2);font-size:11px">29%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:29%;background:#f1e05a;"></div></div>
          </div>
          <div class="steam-stats">
            <div class="steam-stat">Stars: <span>183</span></div>
            <div class="steam-stat">Forks: <span>29</span></div>
            <div class="steam-stat">Issues: <span>5</span></div>
          </div>
          <div class="steam-btns">
            <a href="LINK_PROJETO_2_GITHUB" class="steam-btn" style="border-color:#00ff88;color:#00ff88">▶ Ver Código</a>
            <a href="LINK_DEMO_2" class="steam-btn filled" style="background:#00ff88;color:var(--dark)">◈ Demo Live</a>
          </div>
        </div>
      </div>

      <!-- Card 3 -->
      <div class="steam-card" style="--card-accent:#ff0099">
        <div class="steam-banner sb-3">
          <div class="circuit-lines"></div>
          <div class="sb-glow">
            <div class="mini-art">
              <div class="hex-grid" style="--card-accent:#ff0099">
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
              </div>
            </div>
          </div>
          <div class="steam-score" style="color:#ff0099">★ 92% POSITIVO</div>
          <div class="steam-tags">
            <span class="steam-tag" style="border-color:#ff0099;color:#ff0099">Python</span>
            <span class="steam-tag" style="border-color:#ff0099;color:#ff0099">FastAPI</span>
          </div>
          <div class="proj-icon-wrap" style="border-color:#ff0099">⚡</div>
        </div>
        <div class="steam-body">
          <div class="steam-proj-title">Flux-API</div>
          <div class="steam-proj-sub">Gateway de Alta Escala</div>
          <p class="steam-proj-desc">API gateway com rate limiting, observabilidade e múltiplos provedores de pagamento. Suporta 50k req/min.</p>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#3572a5;font-family:monospace;font-size:11px">Python</span><span style="color:var(--text2);font-size:11px">82%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:82%;background:#3572a5;"></div></div>
          </div>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#336791;font-family:monospace;font-size:11px">SQL</span><span style="color:var(--text2);font-size:11px">18%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:18%;background:#336791;"></div></div>
          </div>
          <div class="steam-stats">
            <div class="steam-stat">Stars: <span>91</span></div>
            <div class="steam-stat">Forks: <span>14</span></div>
            <div class="steam-stat">Issues: <span>1</span></div>
          </div>
          <div class="steam-btns">
            <a href="LINK_PROJETO_3_GITHUB" class="steam-btn" style="border-color:#ff0099;color:#ff0099">▶ Ver Código</a>
            <a href="LINK_DEMO_3" class="steam-btn" style="border-color:#ff0099;color:#ff0099">◈ Docs</a>
          </div>
        </div>
      </div>

      <!-- Card 4 -->
      <div class="steam-card" style="--card-accent:#ffb800">
        <div class="steam-banner sb-4">
          <div class="circuit-lines"></div>
          <div class="sb-glow">
            <div class="mini-art">
              <div class="hex-grid" style="--card-accent:#ffb800">
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
                <div class="hex"></div><div class="hex"></div><div class="hex"></div>
              </div>
            </div>
          </div>
          <div class="steam-score" style="color:#ffb800">★ NOVO</div>
          <div class="steam-tags">
            <span class="steam-tag" style="border-color:#ffb800;color:#ffb800">Flutter</span>
            <span class="steam-tag" style="border-color:#ffb800;color:#ffb800">Firebase</span>
          </div>
          <div class="proj-icon-wrap" style="border-color:#ffb800">📱</div>
        </div>
        <div class="steam-body">
          <div class="steam-proj-title">Kibo-Mobile</div>
          <div class="steam-proj-sub">App Mobile Cross-Platform</div>
          <p class="steam-proj-desc">Meu primeiro app Flutter — agenda inteligente com Firebase e notificações push em tempo real. Em desenvolvimento ativo.</p>
          <div class="lang-bar-wrap">
            <div class="lang-label"><span style="color:#54c5f8;font-family:monospace;font-size:11px">Dart/Flutter</span><span style="color:var(--text2);font-size:11px">90%</span></div>
            <div class="lang-bar"><div class="lang-fill" style="width:90%;background:#54c5f8;"></div></div>
          </div>
          <div class="steam-stats">
            <div class="steam-stat">Stars: <span>12</span></div>
            <div class="steam-stat">WIP: <span>SIM</span></div>
          </div>
          <div class="steam-btns">
            <a href="LINK_PROJETO_4_GITHUB" class="steam-btn filled" style="background:#ffb800;color:var(--dark)">▶ Ver Progresso</a>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="divider"></div>

<!-- STATS -->
<section id="stats" class="stats-section">
  <div class="wrapper">
    <div class="section-header">
      <div class="section-label">// RELATÓRIO_DE_ATIVIDADE</div>
      <h2 class="section-title">Stats & Atividade</h2>
    </div>
    <div class="stats-grid">
      <div class="stat-card" style="--stat-color:#00f5ff">
        <div class="stat-num">8+</div>
        <div class="stat-label">ANOS DE XPERIÊNCIA</div>
      </div>
      <div class="stat-card" style="--stat-color:#00ff88">
        <div class="stat-num">50+</div>
        <div class="stat-label">REPOSITÓRIOS</div>
      </div>
      <div class="stat-card" style="--stat-color:#ff0099">
        <div class="stat-num">500+</div>
        <div class="stat-label">TOTAL DE STARS</div>
      </div>
      <div class="stat-card" style="--stat-color:#ffb800">
        <div class="stat-num">2.1k</div>
        <div class="stat-label">COMMITS / ANO</div>
      </div>
    </div>

    <!-- Contribution grid sim -->
    <div class="contrib-wrap">
      <div class="contrib-title">// CONTRIBUIÇÕES — ÚLTIMO ANO</div>
      <div class="contrib-grid" id="contrib-grid"></div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- HOBBIES -->
<section id="hobbies" class="hobbies-section">
  <div class="wrapper">
    <div class="section-header">
      <div class="section-label">// DADOS_PESSOAIS</div>
      <h2 class="section-title">Hobbies & Cultura</h2>
      <p class="section-subtitle">Além do código — o que me alimenta</p>
    </div>
    <div class="hobbies-grid">
      <div class="hobby-card" style="--hobby-color:#00f5ff">
        <div class="hobby-header">⬡ Animes Favoritos</div>
        <ul class="hobby-list">
          <li data-icon="◈">Ghost in the Shell</li>
          <li data-icon="◈">Neon Genesis Evangelion</li>
          <li data-icon="◈">Cowboy Bebop</li>
          <li data-icon="◈">Attack on Titan</li>
          <li data-icon="◈">Psycho-Pass</li>
        </ul>
      </div>
      <div class="hobby-card" style="--hobby-color:#ff0099">
        <div class="hobby-header">⬡ Jogos Favoritos</div>
        <ul class="hobby-list">
          <li data-icon="◉">Cyberpunk 2077</li>
          <li data-icon="◉">Deus Ex: Human Revolution</li>
          <li data-icon="◉">NieR: Automata</li>
          <li data-icon="◉">Elden Ring</li>
          <li data-icon="◉">Minecraft</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- FAQ -->
<section class="faq-section">
  <div class="wrapper">
    <div class="section-header">
      <div class="section-label">// CONSULTAS_FREQUENTES</div>
      <h2 class="section-title">FAQ</h2>
      <p class="section-subtitle">Perguntas frequentes ao meu terminal digital</p>
    </div>
    <div class="faq-list">
      <div class="faq-item">
        <div class="faq-q" onclick="toggleFaq(this)">Qual é a sua stack favorita? <span class="faq-arrow">▼</span></div>
        <div class="faq-a">TS/Next.js no front, Go no back. É o equilíbrio perfeito de velocidade de desenvolvimento e performance em produção. Rust quando performance é crítica.</div>
      </div>
      <div class="faq-item">
        <div class="faq-q" onclick="toggleFaq(this)">Linux ou Windows? <span class="faq-arrow">▼</span></div>
        <div class="faq-a">Linux (Arch) para terminal e produção — o controle é absoluto. Windows para jogos, claro. Cada um no seu lugar.</div>
      </div>
      <div class="faq-item">
        <div class="faq-q" onclick="toggleFaq(this)">Como gerencia o tempo? <span class="faq-arrow">▼</span></div>
        <div class="faq-a">Pomodoro para foco, Notion para tarefas e Trello para projetos maiores. E muita música lo-fi synthwave ao fundo.</div>
      </div>
      <div class="faq-item">
        <div class="faq-q" onclick="toggleFaq(this)">Aceita colaborações open source? <span class="faq-arrow">▼</span></div>
        <div class="faq-a">Com certeza! Procure repositórios com a tag 'help-wanted' ou me mande mensagem. Adoro colaborar com a comunidade.</div>
      </div>
      <div class="faq-item">
        <div class="faq-q" onclick="toggleFaq(this)">Por que o tema cyberpunk? <span class="faq-arrow">▼</span></div>
        <div class="faq-a">Cresci vendo Ghost in the Shell e lendo Gibson. A estética representa o que acredito: tecnologia como extensão da humanidade. Além disso, neon é bonito demais.</div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-ascii">
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
█ MAURO DE SOUZA · DIGITAL TERMINAL © 2024 █
▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀▀
  </div>
  <div class="footer-copy">// FIM DA LINHA — SESSÃO ENCERRADA</div>
</footer>

<script>
// PARTICLES
(function(){
  const canvas=document.getElementById('particles');
  const ctx=canvas.getContext('2d');
  let W,H,pts=[];
  function resize(){W=canvas.width=innerWidth;H=canvas.height=innerHeight;}
  resize();window.addEventListener('resize',resize);
  for(let i=0;i<60;i++){
    pts.push({
      x:Math.random()*innerWidth,
      y:Math.random()*innerHeight,
      r:Math.random()*1.5+0.3,
      vx:(Math.random()-0.5)*0.3,
      vy:(Math.random()-0.5)*0.3,
      o:Math.random()*0.5+0.1,
      c:Math.random()<0.5?'0,245,255':'255,0,153'
    });
  }
  function draw(){
    ctx.clearRect(0,0,W,H);
    pts.forEach(p=>{
      p.x+=p.vx;p.y+=p.vy;
      if(p.x<0)p.x=W;if(p.x>W)p.x=0;
      if(p.y<0)p.y=H;if(p.y>H)p.y=0;
      ctx.beginPath();
      ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
      ctx.fillStyle=`rgba(${p.c},${p.o})`;
      ctx.fill();
    });
    // connection lines
    pts.forEach((a,i)=>{
      pts.slice(i+1).forEach(b=>{
        const d=Math.hypot(a.x-b.x,a.y-b.y);
        if(d<120){
          ctx.beginPath();
          ctx.moveTo(a.x,a.y);ctx.lineTo(b.x,b.y);
          ctx.strokeStyle=`rgba(0,245,255,${0.06*(1-d/120)})`;
          ctx.lineWidth=0.5;ctx.stroke();
        }
      });
    });
    requestAnimationFrame(draw);
  }
  draw();
})();

// TYPING ANIMATION
(function(){
  const el=document.getElementById('typing-text');
  const msgs=[
    'Construindo o futuro, uma linha de código por vez...',
    'TypeScript • Next.js • Go • Rust • Kubernetes',
    'Transformando cafeína em microserviços desde 2016',
    '$ git commit -m "mais um passo rumo ao próximo nível"'
  ];
  let mi=0,ci=0,del=false;
  function tick(){
    const msg=msgs[mi];
    if(!del){
      el.textContent=msg.slice(0,++ci);
      if(ci===msg.length){del=true;setTimeout(tick,2000);return;}
    }else{
      el.textContent=msg.slice(0,--ci);
      if(ci===0){del=false;mi=(mi+1)%msgs.length;}
    }
    setTimeout(tick,del?40:55);
  }
  tick();
})();

// CONTRIBUTION GRID
(function(){
  const grid=document.getElementById('contrib-grid');
  const levels=[0,0,0,1,1,2,2,3,4];
  for(let w=0;w<52;w++){
    const week=document.createElement('div');
    week.className='contrib-week';
    for(let d=0;d<7;d++){
      const cell=document.createElement('div');
      const lv=levels[Math.floor(Math.random()*levels.length)];
      cell.className=`contrib-cell cc-${lv}`;
      cell.title=`${Math.floor(Math.random()*12)} contribuições`;
      week.appendChild(cell);
    }
    grid.appendChild(week);
  }
})();

// FAQ TOGGLE
function toggleFaq(el){
  const item=el.parentElement;
  const open=item.classList.contains('open');
  document.querySelectorAll('.faq-item').forEach(i=>i.classList.remove('open'));
  if(!open)item.classList.add('open');
}

// SCROLL REVEAL (simple)
const observer=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.style.opacity='1';
      e.target.style.transform='translateY(0)';
    }
  });
},{threshold:0.1});
document.querySelectorAll('.steam-card,.tl-item,.stat-card,.hobby-card,.faq-item').forEach(el=>{
  el.style.opacity='0';
  el.style.transform='translateY(20px)';
  el.style.transition='opacity 0.6s ease, transform 0.6s ease';
  observer.observe(el);
});
</script>
</body>
</html>
