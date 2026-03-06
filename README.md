<!DOCTYPE html>
<html lang="tr" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Neleryokki — Web Developer & İçerik Üreticisi</title>
<meta name="description" content="Neleryokki — Oyun toplulukları, forum platformları ve premium web projeleri geliştiren full-stack developer. Dark tema, modern UI/UX uzmanı.">
<meta name="keywords" content="Neleryokki, web developer, oyun geliştirme, discord bot, MyBB tema, forum sitesi, dark tema, full-stack developer, tamproxy">
<meta name="author" content="Neleryokki">
<meta name="robots" content="index, follow">
<meta property="og:title" content="Neleryokki — Web Developer & İçerik Üreticisi">
<meta property="og:description" content="Oyun toplulukları, forum platformları ve premium web projeleri geliştiren full-stack developer.">
<meta property="og:type" content="website">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;900&family=Rajdhani:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#000000;--bg2:#030508;--bg3:#060810;
  --surface:#09090f;--surface2:#0d0f18;
  --border:#121624;--border2:#1a2236;
  --text:#dde6f8;--text2:#6b85a8;--text3:#334055;
  --accent:#00aaff;--accent2:#0077cc;--accent3:#00ffcc;
  --accentglow:rgba(0,170,255,.15);
  --card:#060810;--header:rgba(0,0,0,.92);
}
[data-theme="light"]{
  --bg:#f4f7ff;--bg2:#edf2ff;--bg3:#e4ecff;
  --surface:#fff;--surface2:#f0f5ff;
  --border:#d0daf0;--border2:#b8c8e8;
  --text:#0a0f1e;--text2:#3a5075;--text3:#8a9fc0;
  --accent:#0066cc;--accent2:#004499;--accent3:#007755;
  --accentglow:rgba(0,102,204,.1);
  --card:#fff;--header:rgba(244,247,255,.95);
}
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{font-family:"Rajdhani",sans-serif;background:var(--bg);color:var(--text);overflow-x:hidden;cursor:none}

/* CURSOR */
#cursor{position:fixed;pointer-events:none;z-index:99999;top:0;left:0;transform:translate(-50%,-50%)}
#cursor-ring{width:34px;height:34px;border-radius:50%;border:1.5px solid rgba(0,170,255,.5);position:absolute;transform:translate(-50%,-50%);transition:width .2s,height .2s,border-color .2s;box-shadow:0 0 8px rgba(0,170,255,.15)}
#cursor-dot{width:4px;height:4px;background:#00aaff;border-radius:50%;position:absolute;transform:translate(-50%,-50%);box-shadow:0 0 6px #00aaff}

/* PROGRESS BAR */
#pbar{position:fixed;top:0;left:0;height:2.5px;width:0%;z-index:99998;background:linear-gradient(90deg,#00aaff,#00ffcc);box-shadow:0 0 10px rgba(0,170,255,.7);transition:width .08s linear}

/* GRID CANVAS */
#grid-canvas{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:1}

/* HEADER */
header{position:fixed;top:0;left:0;right:0;height:62px;z-index:1000;background:var(--header);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;padding:0 3rem}
.logo{display:flex;align-items:center;gap:.65rem;text-decoration:none;color:var(--text);font-family:"Orbitron",monospace;font-weight:900;font-size:1.2rem;letter-spacing:.06em}
.logo-avatar{width:36px;height:36px;border-radius:50%;border:2px solid var(--accent);object-fit:cover;flex-shrink:0;box-shadow:0 0 10px rgba(0,170,255,.3);transition:box-shadow .3s}
.logo-avatar:hover{box-shadow:0 0 18px rgba(0,170,255,.6)}
.logo-nm b{color:var(--accent)}
@keyframes blink{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.3;transform:scale(.7)}}

nav{display:flex;align-items:center;gap:2rem}
nav a{font-family:"JetBrains Mono",monospace;font-size:.63rem;letter-spacing:.12em;text-transform:uppercase;color:var(--text3);text-decoration:none;transition:color .2s;position:relative}
nav a::after{content:"";position:absolute;bottom:-4px;left:0;width:0;height:1px;background:var(--accent);transition:width .3s}
nav a:hover{color:var(--accent)}
nav a:hover::after{width:100%}

.header-right{display:flex;align-items:center;gap:.6rem}
.hbtn{width:33px;height:33px;border:1px solid var(--border2);background:var(--surface);border-radius:7px;display:flex;align-items:center;justify-content:center;cursor:none;color:var(--text2);transition:all .2s}
.hbtn:hover{border-color:var(--accent);color:var(--accent)}
.hbtn svg{width:14px;height:14px}
.lang-btn{font-family:"JetBrains Mono",monospace;font-size:.6rem;letter-spacing:.08em;padding:0 .6rem;height:33px;border:1px solid var(--border2);background:var(--surface);border-radius:7px;display:flex;align-items:center;cursor:none;color:var(--text2);transition:all .2s;white-space:nowrap}
.lang-btn:hover{border-color:var(--accent);color:var(--accent)}
.lang-active{border-color:var(--accent)!important;color:var(--accent)!important}

/* HAMBURGER */
.hamburger{display:none;flex-direction:column;gap:5px;cursor:none;background:none;border:none;padding:4px}
.hamburger span{display:block;width:22px;height:2px;background:var(--text2);border-radius:2px;transition:all .3s}
.hamburger.open span:nth-child(1){transform:rotate(45deg) translate(5px,5px)}
.hamburger.open span:nth-child(2){opacity:0}
.hamburger.open span:nth-child(3){transform:rotate(-45deg) translate(5px,-5px)}
.mobile-nav{display:none;position:fixed;top:62px;left:0;right:0;background:var(--header);backdrop-filter:blur(20px);border-bottom:1px solid var(--border);padding:1.25rem 2rem;z-index:999;flex-direction:column;gap:1.1rem}
.mobile-nav.open{display:flex}
.mobile-nav a{font-family:"JetBrains Mono",monospace;font-size:.7rem;letter-spacing:.12em;text-transform:uppercase;color:var(--text2);text-decoration:none;padding:.4rem 0;border-bottom:1px solid var(--border)}
.mobile-nav a:last-child{border-bottom:none}
.mobile-nav a:hover{color:var(--accent)}

/* HERO */
.hero{min-height:100vh;display:flex;align-items:center;padding:9rem 5.5rem 5rem;position:relative;overflow:hidden}
.hero-glow1{position:absolute;width:650px;height:650px;background:radial-gradient(circle,rgba(0,170,255,.07) 0%,transparent 65%);top:-100px;left:-180px;pointer-events:none}
.hero-glow2{position:absolute;width:380px;height:380px;background:radial-gradient(circle,rgba(0,255,204,.04) 0%,transparent 65%);bottom:0;right:8%;pointer-events:none}
.hero-inner{position:relative;z-index:2;max-width:820px}
.eyebrow{display:inline-flex;align-items:center;gap:.55rem;font-family:"JetBrains Mono",monospace;font-size:.63rem;letter-spacing:.18em;text-transform:uppercase;color:var(--accent);border:1px solid rgba(0,170,255,.18);background:rgba(0,170,255,.04);padding:.32rem .95rem;border-radius:100px;margin-bottom:2rem;animation:fup .7s ease both}
.edot{width:5px;height:5px;background:var(--accent3);border-radius:50%;animation:blink 1.5s infinite}
.hero h1{font-family:"Orbitron",monospace;font-size:clamp(2.6rem,6.5vw,5rem);font-weight:900;letter-spacing:-.02em;line-height:1.05;margin-bottom:1.6rem;animation:fup .7s .1s ease both}
.h1-small{color:var(--text2);font-size:.45em;font-weight:400;font-family:"Rajdhani",sans-serif;display:block;margin-bottom:.35rem;letter-spacing:.1em}
.h1-acc{color:var(--accent)}
.hero-desc{font-size:1rem;color:var(--text2);line-height:1.85;max-width:540px;font-weight:400;margin-bottom:2.75rem;animation:fup .7s .2s ease both}
.hero-desc strong{color:var(--text);font-weight:600}
.hero-cta{display:flex;gap:1rem;flex-wrap:wrap;animation:fup .7s .3s ease both}
@keyframes fup{from{opacity:0;transform:translateY(22px)}to{opacity:1;transform:translateY(0)}}

/* CURRENT PROJECT CARD */
.now-card{
  display:inline-flex;align-items:center;gap:1rem;
  background:var(--card);border:1px solid var(--border2);border-radius:12px;
  padding:.85rem 1.25rem;margin-bottom:2rem;
  animation:fup .7s .05s ease both;
  position:relative;overflow:hidden;
}
.now-card::before{content:"";position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,var(--accent),transparent)}
.now-dot{width:8px;height:8px;background:#00ffcc;border-radius:50%;box-shadow:0 0 8px #00ffcc;animation:blink 1.5s infinite;flex-shrink:0}
.now-label{font-family:"JetBrains Mono",monospace;font-size:.6rem;color:var(--text3);letter-spacing:.1em;text-transform:uppercase}
.now-text{font-size:.85rem;color:var(--text);font-weight:600}
.now-text span{color:var(--accent)}

/* SOCIAL ICONS ROW */
.social-row{display:flex;align-items:center;gap:.7rem;margin-top:1.5rem;animation:fup .7s .35s ease both}
.soc-btn{
  width:38px;height:38px;border-radius:9px;
  border:1px solid var(--border2);background:var(--surface);
  display:flex;align-items:center;justify-content:center;
  text-decoration:none;cursor:none;transition:all .25s;
  color:var(--text3);
}
.soc-btn svg{width:16px;height:16px;transition:color .25s}
.soc-btn:hover{transform:translateY(-3px)}
.soc-btn.instagram:hover{border-color:#e1306c;color:#e1306c;box-shadow:0 6px 20px rgba(225,48,108,.25)}
.soc-btn.twitter:hover{border-color:#1da1f2;color:#1da1f2;box-shadow:0 6px 20px rgba(29,161,242,.25)}
.soc-btn.github:hover{border-color:#9b9b9b;color:#c9d1d9;box-shadow:0 6px 20px rgba(201,209,217,.15)}
.soc-btn.discord:hover{border-color:#5865f2;color:#5865f2;box-shadow:0 6px 20px rgba(88,101,242,.25)}

/* TECH STACK STRIP */
.tech-strip{background:var(--surface);border-top:1px solid var(--border);border-bottom:1px solid var(--border);padding:1.2rem 5.5rem;display:flex;align-items:center;gap:2.5rem;overflow-x:auto;position:relative;z-index:2}
.tech-strip-label{font-family:"JetBrains Mono",monospace;font-size:.58rem;color:var(--text3);letter-spacing:.12em;text-transform:uppercase;white-space:nowrap}
.tech-divider{width:1px;height:20px;background:var(--border2);flex-shrink:0}
.tech-item{display:flex;align-items:center;gap:.5rem;white-space:nowrap;opacity:.5;transition:opacity .2s;cursor:default}
.tech-item:hover{opacity:1}
.tech-item svg{width:18px;height:18px}
.tech-item span{font-family:"JetBrains Mono",monospace;font-size:.65rem;color:var(--text2);letter-spacing:.05em}

/* STATS BAR */
.stats{background:var(--surface);border-bottom:1px solid var(--border);padding:1.4rem 5.5rem;display:flex;gap:4rem;overflow-x:auto;position:relative;z-index:2}
.stn{font-family:"Orbitron",monospace;font-size:1.45rem;font-weight:700;color:var(--accent);line-height:1}
.stl{font-family:"JetBrains Mono",monospace;font-size:.6rem;color:var(--text3);letter-spacing:.07em;margin-top:.2rem}

/* SECTION */
section{padding:5.5rem 5.5rem;position:relative;z-index:2}
.alt{background:var(--bg2)}
.stag{font-family:"JetBrains Mono",monospace;font-size:.6rem;color:var(--accent);letter-spacing:.2em;text-transform:uppercase;display:flex;align-items:center;gap:.7rem;margin-bottom:.7rem}
.stag::before{content:"";display:inline-block;width:18px;height:1px;background:var(--accent)}
.sh{font-family:"Orbitron",monospace;font-size:clamp(1.5rem,3vw,2.3rem);font-weight:700;letter-spacing:-.02em;margin-bottom:3rem}

/* ABOUT */
.about-grid{display:grid;grid-template-columns:1fr 1fr;gap:4rem;align-items:start}
.about-p{color:var(--text2);line-height:1.85;font-size:.93rem;margin-bottom:1.35rem}
.about-p strong{color:var(--text);font-weight:600}
.spec-box{background:var(--card);border:1px solid var(--border);border-radius:14px;overflow:hidden}
.spec-top{padding:.9rem 1.35rem;border-bottom:1px solid var(--border);font-family:"JetBrains Mono",monospace;font-size:.6rem;color:var(--text3);letter-spacing:.12em;text-transform:uppercase;display:flex;align-items:center;gap:.5rem}
.spec-top svg{width:11px;height:11px;color:var(--accent)}
.spec-row{display:flex;align-items:center;gap:.85rem;padding:.7rem 1.35rem;border-bottom:1px solid var(--border);transition:background .2s}
.spec-row:last-child{border-bottom:none}
.spec-row:hover{background:var(--surface)}
.spec-ico{width:30px;height:30px;background:var(--surface2);border-radius:7px;border:1px solid var(--border2);display:flex;align-items:center;justify-content:center;flex-shrink:0}
.spec-ico svg{width:13px;height:13px}
.spec-nm{font-size:.79rem;color:var(--text);font-weight:600}
.spec-vl{font-family:"JetBrains Mono",monospace;font-size:.58rem;color:var(--text3)}

/* CERTS */
.certs-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:1.1rem}
.cert-card{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:1.2rem;display:flex;align-items:flex-start;gap:1rem;transition:border-color .2s,transform .2s}
.cert-card:hover{border-color:rgba(0,170,255,.4);transform:translateY(-2px)}
.cert-ico{width:40px;height:40px;border-radius:10px;background:var(--surface2);border:1px solid var(--border2);display:flex;align-items:center;justify-content:center;flex-shrink:0}
.cert-ico svg{width:18px;height:18px}
.cert-title{font-family:"Rajdhani",sans-serif;font-weight:700;font-size:.9rem;color:var(--text);margin-bottom:.2rem}
.cert-sub{font-family:"JetBrains Mono",monospace;font-size:.58rem;color:var(--text3);letter-spacing:.05em}
.cert-badge{display:inline-block;margin-top:.45rem;font-family:"JetBrains Mono",monospace;font-size:.52rem;padding:.18rem .5rem;border-radius:4px;letter-spacing:.05em;text-transform:uppercase}
.badge-gold{background:rgba(245,158,11,.1);color:#f59e0b;border:1px solid rgba(245,158,11,.25)}
.badge-blue{background:rgba(0,170,255,.08);color:var(--accent);border:1px solid rgba(0,170,255,.2)}
.badge-green{background:rgba(0,255,204,.07);color:var(--accent3);border:1px solid rgba(0,255,204,.2)}

/* PROJECTS */
.pgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:1.5rem}
.pcard{background:var(--card);border:1px solid var(--border);border-radius:14px;overflow:hidden;display:flex;flex-direction:column;text-decoration:none;color:inherit;cursor:none;transition:border-color .3s,transform .3s,box-shadow .3s}
.pcard:hover{border-color:var(--accent);transform:translateY(-5px);box-shadow:0 16px 48px rgba(0,0,0,.5),0 0 0 1px rgba(0,170,255,.25)}
.pcard.off{opacity:.4}
.pcard.off:hover{opacity:.65}
.prev-wrap{width:100%;height:168px;position:relative;overflow:hidden;background:var(--surface);border-bottom:1px solid var(--border);flex-shrink:0}
.prev-wrap iframe{width:200%;height:200%;border:none;transform:scale(.5);transform-origin:top left;pointer-events:none}
.prev-overlay{position:absolute;inset:0;background:linear-gradient(to bottom,transparent 50%,var(--card) 100%);z-index:1}
.prev-lbl{position:absolute;top:.55rem;right:.55rem;font-family:"JetBrains Mono",monospace;font-size:.52rem;color:var(--text3);background:var(--surface);border:1px solid var(--border);border-radius:4px;padding:.18rem .45rem;z-index:2;letter-spacing:.08em;text-transform:uppercase}
.noprev{width:100%;height:168px;background:var(--surface);border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:center;flex-shrink:0}
.noprev svg{width:32px;height:32px;color:var(--border2)}
.pbody{padding:1.4rem;flex:1;display:flex;flex-direction:column}
.phead{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:.9rem}
.pico{width:40px;height:40px;background:var(--surface2);border-radius:9px;border:1px solid var(--border2);display:flex;align-items:center;justify-content:center}
.pico svg{width:18px;height:18px}
.pbadge{font-family:"JetBrains Mono",monospace;font-size:.56rem;padding:.2rem .55rem;border-radius:100px;letter-spacing:.05em;text-transform:uppercase}
.bon{background:rgba(0,255,204,.07);color:var(--accent3);border:1px solid rgba(0,255,204,.2)}
.boff{background:rgba(55,65,80,.15);color:var(--text3);border:1px solid var(--border)}
.pname{font-family:"Orbitron",monospace;font-weight:700;font-size:.88rem;margin-bottom:.3rem}
.purl{font-family:"JetBrains Mono",monospace;font-size:.58rem;color:var(--accent);margin-bottom:.7rem}
.pdesc{font-size:.8rem;color:var(--text2);line-height:1.65;flex:1;font-weight:400}
.ptags{display:flex;gap:.4rem;flex-wrap:wrap;margin-top:.9rem}
.ptag{font-family:"JetBrains Mono",monospace;font-size:.53rem;color:var(--text3);background:var(--surface2);border:1px solid var(--border);border-radius:4px;padding:.16rem .48rem;letter-spacing:.05em;text-transform:uppercase}

/* SKILLS */
.sgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(185px,1fr));gap:1rem}
.sbox{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:1.15rem;transition:border-color .2s}
.sbox:hover{border-color:rgba(0,170,255,.35)}
.shead{display:flex;align-items:center;gap:.7rem;margin-bottom:.8rem}
.sico{width:32px;height:32px;background:var(--surface2);border-radius:7px;border:1px solid var(--border2);display:flex;align-items:center;justify-content:center}
.sico svg{width:15px;height:15px;color:var(--accent)}
.snm{font-family:"Rajdhani",sans-serif;font-weight:600;font-size:.87rem;letter-spacing:.03em}
.strack{height:2px;background:var(--border);border-radius:100px;overflow:hidden}
.sfill{height:100%;background:linear-gradient(90deg,var(--accent),var(--accent3));border-radius:100px;width:0;transition:width 1.2s cubic-bezier(.4,0,.2,1)}

/* CLIENTS */
.clients-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:1.25rem}
.tcard{background:var(--card);border:1px solid var(--border);border-radius:14px;padding:1.6rem;position:relative;overflow:hidden;transition:border-color .3s,transform .3s}
.tcard::before{content:"";position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--accent),var(--accent3));opacity:0;transition:opacity .3s}
.tcard:hover{border-color:rgba(0,170,255,.4);transform:translateY(-3px)}
.tcard:hover::before{opacity:1}
.tcard-quote{font-family:"JetBrains Mono",monospace;font-size:2.5rem;line-height:1;color:var(--accent);opacity:.2;margin-bottom:.5rem}
.tcard-text{font-size:.9rem;color:var(--text2);line-height:1.75;font-weight:400;font-style:italic;margin-bottom:1.25rem}
.tcard-text b{color:var(--text);font-style:normal;font-weight:600}
.tcard-footer{display:flex;align-items:center;gap:.85rem;padding-top:1rem;border-top:1px solid var(--border)}
.tcard-avatar{width:38px;height:38px;border-radius:50%;background:linear-gradient(135deg,var(--accent),var(--accent3));display:flex;align-items:center;justify-content:center;font-family:"Orbitron",monospace;font-weight:700;font-size:.72rem;color:#000;flex-shrink:0}
.tcard-name{font-family:"Rajdhani",sans-serif;font-weight:700;font-size:.88rem;color:var(--text)}
.tcard-role{font-family:"JetBrains Mono",monospace;font-size:.56rem;color:var(--text3);margin-top:.1rem}
.tcard-stars{display:flex;gap:.2rem;margin-top:.35rem}
.tcard-stars svg{width:11px;height:11px;fill:#f59e0b}
.tcard-project{position:absolute;top:1rem;right:1rem;font-family:"JetBrains Mono",monospace;font-size:.55rem;color:var(--accent2);background:rgba(0,170,255,.07);border:1px solid rgba(0,170,255,.15);border-radius:4px;padding:.18rem .45rem;letter-spacing:.06em;text-transform:uppercase}

/* FAQ */
.faq-list{display:flex;flex-direction:column;gap:.7rem;max-width:760px}
.faq-item{background:var(--card);border:1px solid var(--border);border-radius:12px;overflow:hidden;transition:border-color .2s}
.faq-item.open{border-color:rgba(0,170,255,.35)}
.faq-q{display:flex;justify-content:space-between;align-items:center;padding:1.1rem 1.4rem;cursor:none;gap:1rem}
.faq-q-text{font-family:"Rajdhani",sans-serif;font-weight:700;font-size:.95rem;color:var(--text)}
.faq-icon{width:22px;height:22px;border-radius:50%;border:1px solid var(--border2);display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:all .3s;color:var(--text3)}
.faq-icon svg{width:10px;height:10px;transition:transform .3s}
.faq-item.open .faq-icon{border-color:var(--accent);color:var(--accent)}
.faq-item.open .faq-icon svg{transform:rotate(45deg)}
.faq-a{display:none;padding:0 1.4rem 1.1rem;font-size:.87rem;color:var(--text2);line-height:1.8;border-top:1px solid var(--border)}
.faq-a.visible{display:block}

/* FOOTER */
footer{background:var(--surface);border-top:1px solid var(--border);padding:2.5rem 5.5rem;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:1.5rem;position:relative;z-index:2}
.fbrand{font-family:"Orbitron",monospace;font-weight:700;font-size:.95rem}
.fbrand b{color:var(--accent)}
.fcopy{font-family:"JetBrains Mono",monospace;font-size:.58rem;color:var(--text3);margin-top:.25rem}
.flinks{display:flex;gap:1.5rem;flex-wrap:wrap}
.flinks a{font-family:"JetBrains Mono",monospace;font-size:.6rem;color:var(--text3);text-decoration:none;letter-spacing:.1em;text-transform:uppercase;transition:color .2s}
.flinks a:hover{color:var(--accent)}

/* WA */
.wa-wrap{position:fixed;bottom:2rem;right:2rem;z-index:9999}
.wa-tip{position:absolute;bottom:calc(100% + .7rem);right:0;background:var(--surface);border:1px solid var(--border2);border-radius:10px;padding:.6rem 1rem;font-family:"Rajdhani",sans-serif;font-size:.82rem;font-weight:600;color:var(--text);white-space:nowrap;box-shadow:0 8px 28px rgba(0,0,0,.4);opacity:0;transform:translateY(8px);pointer-events:none;transition:all .4s cubic-bezier(.34,1.56,.64,1)}
.wa-tip::after{content:"";position:absolute;bottom:-5px;right:18px;width:10px;height:10px;background:var(--surface);border-right:1px solid var(--border2);border-bottom:1px solid var(--border2);transform:rotate(45deg)}
.wa-tip.show{opacity:1;transform:translateY(0)}
.wa-btn{width:52px;height:52px;background:#25D366;border-radius:13px;display:flex;align-items:center;justify-content:center;box-shadow:0 6px 24px rgba(37,211,102,.35);cursor:none;text-decoration:none;transition:all .3s;border:none;position:relative;z-index:2}
.wa-btn:hover{transform:translateY(-4px) scale(1.06);box-shadow:0 12px 38px rgba(37,211,102,.5)}
.wa-btn svg{width:25px;height:25px;fill:white}
.stbtn{position:fixed;bottom:2rem;right:5.3rem;width:40px;height:40px;background:var(--surface);border:1px solid var(--border2);border-radius:9px;display:flex;align-items:center;justify-content:center;cursor:none;z-index:9999;color:var(--text2);transition:all .3s;opacity:0;pointer-events:none}
.stbtn.show{opacity:1;pointer-events:all}
.stbtn:hover{border-color:var(--accent);color:var(--accent);transform:translateY(-2px)}
.stbtn svg{width:15px;height:15px}

/* COOKIE */
#cookie{position:fixed;bottom:0;left:0;right:0;z-index:9998;background:var(--surface);border-top:1px solid var(--border);padding:1rem 3rem;display:flex;align-items:center;justify-content:space-between;gap:1.5rem;flex-wrap:wrap;transform:translateY(100%);transition:transform .5s cubic-bezier(.34,1.2,.64,1)}
#cookie.show{transform:translateY(0)}
.cookie-text{font-family:"JetBrains Mono",monospace;font-size:.62rem;color:var(--text2);letter-spacing:.04em;flex:1}
.cookie-text a{color:var(--accent);text-decoration:none}
.cookie-btns{display:flex;gap:.6rem}
.cookie-ok{background:var(--accent);color:#000;font-family:"Orbitron",monospace;font-size:.62rem;font-weight:700;padding:.45rem 1rem;border-radius:6px;border:none;cursor:none;letter-spacing:.05em}
.cookie-ok:hover{opacity:.85}
.cookie-no{background:transparent;color:var(--text3);font-family:"JetBrains Mono",monospace;font-size:.6rem;padding:.45rem .8rem;border-radius:6px;border:1px solid var(--border2);cursor:none}
.cookie-no:hover{color:var(--text);border-color:var(--text3)}

hr.div{border:none;border-top:1px solid var(--border);margin:0 5.5rem}
.fi{opacity:0;transform:translateY(26px);transition:opacity .7s ease,transform .7s ease}
.fi.vis{opacity:1;transform:translateY(0)}

@media(max-width:960px){
  header{padding:0 1.5rem}
  nav{display:none}
  .hamburger{display:flex}
  .hero{padding:8rem 1.5rem 4rem}
  section{padding:4rem 1.5rem}
  .stats{padding:1.4rem 1.5rem;gap:2rem}
  .tech-strip{padding:1.2rem 1.5rem}
  footer{padding:2rem 1.5rem}
  hr.div{margin:0 1.5rem}
  .about-grid{grid-template-columns:1fr}
  #cookie{padding:1rem 1.5rem}
}
</style>
</head>
<body>

<div id="pbar"></div>
<div id="cursor"><div id="cursor-ring"></div><div id="cursor-dot"></div></div>
<canvas id="grid-canvas"></canvas>

<!-- HEADER -->
<header>
  <a href="#" class="logo">
    <img src="data:image/jpeg;base64,/9j/2wCEAAgGBgcGBQgHBwcJCQgKDBQNDAsLDBkSEw8UHRofHh0aHBwgJC4nICIsIxwcKDcpLDAxNDQ0Hyc5PTgyPC4zNDIBCQkJDAsMGA0NGDIhHCEyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMjIyMv/AABEIAToBOgMBIgACEQEDEQH/xAGiAAABBQEBAQEBAQAAAAAAAAAAAQIDBAUGBwgJCgsQAAIBAwMCBAMFBQQEAAABfQECAwAEEQUSITFBBhNRYQcicRQygZGhCCNCscEVUtHwJDNicoIJChYXGBkaJSYnKCkqNDU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6g4SFhoeIiYqSk5SVlpeYmZqio6Slpqeoqaqys7S1tre4ubrCw8TFxsfIycrS09TV1tfY2drh4uPk5ebn6Onq8fLz9PX29/j5+gEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoLEQACAQIEBAMEBwUEBAABAncAAQIDEQQFITEGEkFRB2FxEyIygQgUQpGhscEJIzNS8BVictEKFiQ04SXxFxgZGiYnKCkqNTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqCg4SFhoeIiYqSk5SVlpeYmZqio6Slpqeoqaqys7S1tre4ubrCw8TFxsfIycrS09TV1tfY2dri4+Tl5ufo6ery8/T19vf4+fr/2gAMAwEAAhEDEQA/AKmKMU+iuzmP1S4zFGKfRRzBcZijFPoo5guMxRin0UcwXGYoxT6KOYLjMUYp9FHMFxmKMU+ijmC4zFGKfRRzBcZijFPoo5guMxRin0UcwXGYoxT6KOYLjMUYp9FHMFxmKMU+ijmC4zFGKfRRzBcZijFPoo5guMxRin0UcwXGYoxT6KOYLjMUYp9FHMFxmKMU+ijmC4zFGKfRRzBcdijFPxRgVjzGVxmKMU/FGBRzBcZijFPxRgUcwXGYoxT8UYFHMFxmKMU/FGBRzBcZijFPxRgUcwXGYoxT8UYFHMFxmKMU/FGBRzBcZijFPxSY+vv7UcwXG4oxWdqPiDTNLJW5uQJOuxeTWVH4+0Z5ApW5QH+Joxj+dLnOSeOw8JcspK502KMVXsdSstSi8y0nWVcgcZzz7datYFPmOmFSM1eL0G4oxT8UYFHMXcZijFPxRgUcwrjMUYp+KMCjmC4zFGKfijAo5guMxRin4owKOYLjMUYp+KMCjmC4zFGKfijAo5guMxRin4owKOYLjMUYp+KKOYLjqKdijFY8xFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmE3Yb2J9BmuZ8Y+IDo9msEDYupgdpB5Re5/H+ldJcTx2ltJcTOEijUu7E9AP8mvFda1OTVtUlupMgMcKv91RwB+VO55GbYz2FPljuylLM0spkdizNyzHkn6+tM3dOOlNPWjNI+Mbu7y1Zd07UbnTbtLm2lZJFPPPDZ7GvYtG1OLWNMivI8DcMMv8AdbuP6/jXiIrrPA2tjT9T+yTPtguDgk9FfoD+uPxouexlONdGpySejPUaKdtx2x7UYo5j7JSXQbRTsUYo5h3G0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLj6KdijFZcxncbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBzDaOKdjFUdY1KHR9MmvJhkRj7h43E9B+P9KLmdSqoRcnscZ8Qdd27NIgb5iA8+PQjKr/X8q88PrU97dS3l5LczuXllYuzHuTUBI7Voj4bGYmVeq5sQ0lFFM5BRT0Yo4I65zTBS7hQNNp3R7H4R1pda0dd75uYMRy56n0b9P0reHIzXjXhbWjo2rxzOT9nc+XMo7qe/4HB/CvZkZXjWRSChAII5BHr+PWs5Ox9nlWM9tRs90FFOxRilc9W42inYoxRzCuNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guPop2KMVjzGdxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjOPb86XFbGhaFLrk8kccqxCNQSSCc/hW5/wr25/5/o/+/Z/xqkm9TjrY+jSlyylqcUcDnvXlvj7Wze6mNOgY+Takh+c7n7/AFx0/OvoG7+HWoSWksdtqUMczKQjtESFPrjPNeJ+PvhJqvgrTY9Se7jv7ZpAkrxIVMRPTOc9cYz6/UVpCLW542aZlCrDkpM82frx0xTaU9aStTwAooooAKKKKAHpnHH1r1PwBrhvtObT5n/f2oyrE/eT/wCtkD8RXK+APBF1471x9NtbqO18uIyvLICcDIHAHfmvWNL+AGq6VqUF9B4iti0TZ2m3bBHcfe7ipkro7cDivq9ZS6EnHOKUc12n/Cvbr/n+j/79n/GsfXfDcuhxxPLMkqysV+VcEcZrBxa1PqaWY0KslGL1MOinYoxU8x3XG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXH0U7FGKw5jO42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFPmC51/w//wCPy7/3B/Ou/FcF4AGLu7P+wP513grspawPkM0f+0y+QtU9U0201bTp9PvoVmtrhGjeMjggj/P44q7TSCSPStTzj4s8e+Dbvwb4pn02Xc9u37y1mI/1sZPB+vY+/wCFcsRivsj4l+BofG/hmS1VVXUYAZLOU9nxyp9mxj24Pavj68tZ7S7mt7mNo54WKSIwwVYHBB/GgCvRQRg4ooAKKKKAPY/2c/8AkddQ6f8AHif/AENa+mxXzJ+zl/yOuo/9eJ/9DWvpztQAmK4v4hf8edp/11P8jXaE4Ncb8QBmzsx/01P8qzqO0Wzty5/7RE4HFFOxkZ7GjFcPMfZ3G0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXH0U6iseYi42inUUcwXG0U6ijmC42inUUcwXG0U6ijmC42jFOoo5hXOt8Bf8fV2f9lf5mu7HNeb/AA/1OGbxFqOmxENLBbpLJ/skn5R+X869IA446V6VC/s9T5HMZKWIk0OooorY4RpXJzxXg3x2+HgaNvFumQ5ZQFvkUdR0En8sn8a97qG5hiuIJIZkV4pEZXVhkMp4II9CKAPgh+vtTa7v4peApvBPiZ0hRm0u6JktZDzgd0PuP5YrhWXacHH4UAJRRRQB7H+zl/yOuo/9eJ/9DWvpztXzH+zl/wAjrqP/AF4n/wBDWvpztQAhNed/FLVo9NGhxTbViurloi5/hbb8v5nivRCMmvEv2jyU8P6IR1+1P/6BUyXMuU0o1HTqKa6DuvOOvNGK53wXrw13RVMjZurciObPU8HDfiB+ddJxXlyvGVj7SlWVWCmhtFOoqeY1uNop1FHMFxtFOoo5guNop1FHMFxtFOoo5guNop1FHMFx2KMU+isuYyuMxRj2p2KMGjmC43FGKfRRzBcZijHtTsUYNHMFxuKMU+ilzBcZjAz29az9b1WHRdJuL6bBEa4WMnG9j0X8f6GtPHp1wcfWvH/iN4gGoaqNNt3zbWhIYg53Sd/y6fnW+Hg6k/JHLjMR7GndbnoP7PV3NfeJPEV1PIXmlijZ2PclzX0GOlfOv7N3/IZ13/r3i/8AQjX0X2r1z5KUnJ3YVE1zCk6QNIoldSyoSASAQCR9Mj8xUteNfG7X77wvrPhXV7B9s0Es2QTw6kKCh9iOPy9KBHsoOaQjJrG8L+I7LxR4etNWsWzDOvK5yUYcMp9wcj9ehrZByM0Ac3428JWfjLw3caVdBVfG+CbHMUgHB9/Qj0zXxrrOj3miatcabfQmK5t3KSKfUd/p6etfdpBJ4NePfG34d/23pJ8Q6dAp1GzjPnIi8zRDn8SvJHtx2FAHzIRjrSU587uc/jTaAPY/2cv+R11H/rxP/oa19Odq+Y/2cv8AkddR/wCvE/8Aoa19OdqACvEP2k+PDuif9fT/APoNe314h+0n/wAi7on/AF9P/wCgUAeIeEddbQtbinJJtpD5cyjupPX6jr+Fe6I6yRq6sGQgEMORg9/pXzapwPxzXrnw28Qfb9NOlzvm4tRmMk8vGf8ADp+IrjxdK8eZbns5XibP2cjuMe2KMU4UtebzH0DYzFGPanYowaOYVxuKMU+inzBcZijHtTsUYNHMFxuKMU+ijmC4zFGPanYowaOYLj8UYp+KMVjzEXGYoxT6KOYLjMUYp+KMUcwXGYoxT6KOYLjMUcd/Wn4prEKCxIAA6nt/n+lF7sHKyuc74x19dA0OSRWC3c37uBT/AHiOv0Az+leESMXfcSST610XjXxD/buuu0TsbSD93COxA6n8TmuaJBPAwK9rDUuSHmfM47EOrUsnoj3P9mz/AJDGu/8AXCL/ANCNfRfavnP9mz/kMa7/ANcIv/QjX0Z2rpOAK8F/aUIEPh4ns03Xn+5XvVeCftK/8e/h/wD35v8A2WgDiPhB8QD4T102V/MRpF84WUuciGQjCyf0PqOf4a+r1cFQQMg8jFfAysFznP4V9KfA/wCIX9s6aPDWpTZvbRP9GdzkzRD+H6r+o+hoA9nBz0prpuPPTGCKVelOoA+UvjN8PT4U13+07CIDSr9iyqg4hk6sn0PUe2R2ry5hg19zeJdAsfE2i3OlahHugnjI3AfMjdmHuDyPx9a+M/FPhu+8LeIbrSL5QJYDw4+66HlWHsR/h1oA9I/Zy/5HXUf+vE/+hrX052r5k/ZzGPG2o/8AXif/AENa+m+1ABXiH7Sf/Iu6J/19P/6BXt9eIftJ/wDIu6J/19P/AOgUAfOFaOjapLouqW99AfmifJH94dCPxBIrNpwYDrQ1zKzKhNxfMuh9JWF3BqFjFd2z74ZVDKfT2Pv2+tWK8w+GHiILK+i3DnDZe3LHof4l/r9RXqIHH+f8+9eDXg6c7H1eFrqrBMbijFPorLmOi4zFGKfijFHMFxmKMU+ijmC4zFGKfijFHMFxmKMU+ijmC47FGKfRWPMZ3GYoxT6KOYLjMUYp9FHMFxmKMU+ijmC4wgAEk9BmuI+JPiH+ytI/s6B8XV2CGweVj6H8+n512d3dw6faTXc7hIoVLsx7AZ5/+tXzxr+sTa5rFxfTZXecIp52IPuj8q7sDR9rK72R5+PxKpw5VuzLc5bmm0pOTSV7Z88e5/s1/wDIY13/AK4Rf+hGvoztXzn+zX/yGNd/64Rf+hGvoztQAV4J+0r/AMe/h/8A35v/AGWve68E/aV/49/D/wDvzf8AstAHz3V/SdUu9G1O21CxmaG6t5BJG69QR/n8s+tUKUHAoA+1/AvjCz8Z+GLfU4CEm+5cQg5MUgHI+nce34104Oa+Ovhh47l8E+JUmkZjptztju4x/d7OPcdfcZHevr+1nhubaOeB1khkUOjqcgqRkEGgCRgSePxrzb4ufD7/AIS7w/8AarGJTq9ipaDaMGVOrRn69R6Ee9el01l3en0NAHzR+zyph8caiHyGFkcg9R8619MiuH03wLDofxJu/EVkqrbX9qwnjHGyXcp3D2Izkev147denXNAC14h+0n/AMi7on/X0/8A6BXt9eIftJ/8i7on/X0//oFAHzeaKDRQBYtLmWzuI7iByksbh1YdiDwa+hPDusxa9okF9FgMwxIg/hfoR+ePzr50XHfNdv8ADjxH/ZOtCznfFrdkLknhZOin8c4/H2rkxlH2kOZbo78BiPZT5Xsz2nFGKfj2/wA9KK8Bux9Fe+wzFGKfRT5guMxRin0UcwXGYoxT6KOYLjMUYp9FHMFx2KMU+isOZmdxmKMU7FLijmYXGYoxT6KOZhcZijFOI4zWbr2rwaDo1xqE4yIl+RD/ABsei/iauCc5KK3FKpyq7PP/AIp+I8eXoVs/XElxj16qv9T+FeVsc4x+tWL+8nvr6a7uZDJPM5d3Pcmq2a+ooUlSp2R83iKrqzuwNJRRWpznuf7Nf/IX14/9MIv/AEI19FjpXxN4Q8c6z4JnuZtHaBXuFCyGWIPkDkfSur/4X5437TWWPe2FAH1fXgn7Sv8Ax7+H/wDem/ktcX/wv3xv/wA9rH/wFFcz4u+IOueN1tV1l4WFqW8vyYgn3sZz+QoA5Y0lKxyc0lADlYL1BPNe/wDwJ+IYbb4S1KU/LlrCRzyepaP+oH1Havn6p7O5ltLmK4gkaOaJ1eN1bBVgcgg9qAPvdenXNLXEfDHx1B408MJNIyLqVt8l5EOMN2Yexwfp07V2yncM0AIRk5GM+9KBilooAK8Q/aT/AORd0T/r6f8A9Ar2+vEP2k/+Rd0T/r6f/wBAoA+bzRQaKAFHSnoSpGOuc1HSg4p6PRjTtqj33wJ4iHiDQk8183dviOb344b8QPzBrqMcDjFfPvgvxA3h7Xorlm/0V/3c6eqnv9Qefwr6DRlkjDxncjAMpByCPWvncdQ9nO62Z9Bg66qQs9xMUYp9FcHM2dtxmKMU7FLijmYrjMUYp9FHMwuMxRTsUYo5mFx9FOorLmM7jaKdRRzBcbRTqKOYLjOmT0PrXjfxV11rnWk0iI4gtF3Nz1kYd/oOPxNezEcHPSvnrx+jr451YPnJm3DPoQCP516eVRU6rb6HDj6jVOyOZbGeOlJSkYOKTFfRHiBRRRQAUUuKMGgBKKXBowaAEopcGjBoASnKQBzSYNGDQB1HgTxjd+C/E0Gp2+54jiO4h3YEsZxkfXuPcCvsjStUs9X0q31CxlE1tcIJImXuD0+h7Y7HivhAHAwR/wDXFez/AAP+IX9makPDWpzYsrt82zyHiOU/w/Rj/wCPfWgD6VBBGRS0gPFLmgArxD9pP/kXdE/6+n/9Ar2/NeIftJ/8i7on/X0//oFAHzeaKXFGDQAlFLikxQA5DjPOK9t+FutvqWgSWEx3TWLAKc9UOcflgj8q8RAz3xXqPwajc3uqvz5flIp+pbI/kfyNcWYRjKg2+h2YKbjVSPWSME0U7riivl+Y9642inUUcwrjaKdRRzBcbRTqKOYLjsUYp9FY8xncZijFPoo5guMxRin0UcwXGAV5b8VPCskxXXrSMttUJcqvXA+6+PQdCe2BXqtIQCCGAIPBB710YbEuhPmRnVpqpHlZ8ourA8gj2PWkwa901z4V6RqczTWMr2EjHLBF3If+A8Y/A49MVh/8KZkIGdaT/wABz/8AFV9JHM6Eldux5EsJUWiPJ/zo/OvV/wDhS7/9BpP/AAHP/wAVR/wpd/8AoNJ/4Dn/AOKqv7Rw/wDMT9Vq9jyj86Pzr1f/AIUu/wD0Gk/8Bz/8VR/wpd/+g0n/AIDn/wCKo/tHD9w+q1ex5R+dH516v/wpd/8AoNJ/4Dn/AOKo/wCFLv8A9BpP/Ac//FUf2jh+4fVavY8o/Oj869X/AOFLv/0Gk/8AAc//ABVH/Cl3/wCg0n/gOf8A4qj+0cP3D6rV7HlH50fnXq//AApd/wDoNJ/4Dn/4qj/hS7/9BpP/AAHP/wAVR/aOH7h9Vq9jyj86fG/luGGQQcg+leqf8KXf/oNJ/wCA5/8AiqT/AIUu/wD0Gk/8Bz/8VR/aOH7h9Vq9j1r4QfENfFvh4WV9LnV7EBJc9ZU6K/uex9+e9ek+avQkA+lfL6fByeL/AFeuhT6iA/8AxX+cCpP+FR3mAB4iYAcAeU3T/vuj+0MP/MH1Wr2PpzzU/vV4l+0g6v4e0UKwz9qc4/4BXIf8KivP+hif/v03/wAVTG+Ds8nMmuh+3zQEnr67uOlH9o4fuH1Wr2PJenv9KPzr1c/BiQ9dbQ+/2c//ABVH/Cl3/wCg0n/gOf8A4qj+0cP3D6rV7HlGM0YJ7V6v/wAKXf8A6DSf+A5/+KpV+DDbhu1tdvfFuc/h81DzHD/zDWFqdjyuKF5XEcaM7twoUZJORxX0D4D8NHw7oAjuFAu7hvNmwc7T2X8Bn8Saf4c8B6P4cdZ4ojcXaj/XzYJB/wBkDp/P3rqMcV5GYZiqy9nDY7sLhvZ+9LcYBxRin0V5HMd9xmKMU+ijmFcZijFPoo5guMxRin0UcwXHYoxT6Kx5iLjMUYp9FHMFxmKMU+ijmC4zFGKfRRzBcZijFPqKK5tp3KQ3EMrDqEkViPrg8VS5ne3QXMh22jbTmZUUs7BVHVmOAPrnpUH26y2b/tltsyRu85cce+aaU3shOSW5Lto21El9ZSOES8tndvuqsykn6DOaebm3WURNPEJWGRGZAGPGfu9elDjUW6GpxHbaNtOcrGpZ2CqOSxOAB65qt/aOn9Pt9p7/AOkJx+tCU5bIHJLcn20baY11bJEJWuIRGRw5kAU/Q55pq31kzBVvbZiewmU/1pqFR7Jic0iXbRtpJpobZd08qQqeMysEGfTnHNLHLFMgkilSRD0ZGBB/Gp961x8yvYNtG2n4xQcDOe1JOTdkO6GbaNtNS4t5W2xzxOfRHB/lTpJI4kLvIiqOrFwAPxqmpp2aJUk9g20baIpYp08yGRJU/vI24fpTJbu1hk8uW5gjc9FeVVJ/M0lzN2QOSSuP20baalzbSymKO5heQcFFkBYeuR1p0ksUKb5pI414yzuFAz7nih86duocytcNtGKaLm2MJnFzCYRwZBICo/HoKdHLFMm+KSORc43I4YfmKLSQ+ZBijFPoqeYdxmKMU+ijmC4zFGKfRRzBcZijFPoo5guMxRin0UcwXHYoxT6Kw5mRcZijFPoo5mFxmKMU+ijmYXGYoxT6KOZhcjPA/wAK+bLDW7rQPFcupWwZjHOyyKekiEnKn2OD+We1fSxHFeJ+AtHt9d1fxNp96mYZoW5yMr+9GGHuDg17mVVIRhUc1ocmIu5LlPRdY1O31n4eajqFpIXinsZGB752sMH6V4TMdvhC1GQR9vlI9P8AVx+3vXQxahe+Cv7e8LakD5FzBIsZAOA5Q7GA9GGAfw9DXPyc+ELTH/P/AC59R+7j6969fBYZUU7P3W7o5qtVzsmeoeHvhZaWV1puqrqcztGY7jZ5a4J4OM/jWXqBx8d7fByS8WcYGf3I9PrRb/DPxPNaQSr4hCq8SsqmWXgEZ/Sr+neANbs/G2nalPNFPBbLGskrS5ZiqAHg89a5HUpxnJzqX0ehpq4qyO48Ujb4R1k45+wzdP8Arm2K8d8D+A7fxbYXN5LfSW5in8sKqBgRjOf1r2XxUp/4RDWeCR9hm/8ARbV4p4M8Iax4h0+4uNN1UWccUpVlLuoZsA9uOhrDLXbCz1truVX/AIisj1G/8Cw6h4TsdBa+mWO1YFZdgJbgjp24NcrffB63trG4uYdWkDxIz/vovl4z1OenvWV4l8P6/wCD/DzT3GtyzGeZUQxSuCAA2eTWFrWma9Y+HrDUr3UZriy1EblUTO23uA2eM11YalNpONXRv7yKk09HHU7P4fhvF3hHVNB1RnkhgKiGQ8vHlWI5PXaRkA9sj0qn4S1y48CeIrrw9rbmO1aTKyMcqjdVb/dYf5649A8CaLp2j+GrdtPlM6XQWd5mHLkj9MZxjsc+prmfjFpdq2hW2pGPbdRTCEMOMowJIP48/ia5oYmnUxEqDXuv77l8rjBTRoeG/H0/ifXpbSw0sCwh3M9y7n5U7cY6t6duTXKarqGsfELxXNo2m3Bg0u2JDkk7SoIUu39456D3ruPh5plvZ+B7SS3jCzXkZlkfuzHIH4AYH0B9a4/4RTRWuvaxYT4S5ZBhW6na2GHPPfP4U6bpU/aTpR+EJOTtzMdf/CKezszc6Tq7vex/MiuoTeR/dYEYPHf9KqxeLbrW/hvrun6kxa9s0Qh2yDIhlUc+4P8AOvQPD+h6poupareanrLXdtdNuRGdvlGSSfmOAcdhxj6YrxwA39x4vv7cH7MYmbjgEPOhH6c/gTW+Ek691Us7ap/oTV/d7HbeEvElt4Z+F8d5OfMmaaVIIc4MjZ6f4ntVXwL4au/E2ryeKtezIjSZhjb7sjZ4IH91ccDp09OfPIbPU30qDUZ7WabSoJREMnCkk5Zc9RnoT6kDrxX0V4a1bT9a0K2utM2xwbAnlKBmI4HycenQVOO/2aLlT15nq+wUvffKzzDwfKsXxZ1iWRwiKLkszNgABgcknp0JqLVtQvvid4qi0vTS8ek2x3GTbwB3kYdzzhR/9fHNajY6hqPjXWLLTIpJJZpZVZIz1TOTn24H413/AMJNW06O1n0d4Rb6oJDI5Y4abk/qvIx7k1riIKnTdeCTkkvkTGbm+V7G14x0220f4X31jZx+XDFCgA65PmIST6kkkn60nwqyfA0Gf+e0n86vfEZT/wAIBqwxj92ufbEiZNU/hQD/AMILB/11k/nXlObngHKW9zo2rKK2OzxRin0V5FzpuMxRin0UuZjuMxRin0UczC4zFGKfRRzMLjMUYp9FHMwuOxRin0VlzGVxmKMU+ijmC4zFGKfRRzBcZijFPoo5guMx/SoorWC3kZ4II43bqUUA/wAqsUVSm0mk9xXV7nE/ELwZ/wAJPpiS2aL/AGlbA+VkhRIp6rnt2I+hHevP5fhr4mPhqCzWziM8d3JK4NxHgKyIAc7sdQa91xSgYx2x09vpmvRw+bVqVNU7XRjOjFu55XoOm/EeDVdPTUJf+JekiLKnnQH92CM8DkjHpV3xVZ/ECXXZW0Ccpp5RNg82NcHaN3DHP3s16Njtk49z1pcf5wKTzRupzqCGqSStc8gGkfEy6huLe/l3201vKjqZoecowA9epFZukeFPiNoMTQ6Yot4nfe6rcRHJxjqTXuHPYmjaO/PrwOa2/tmSTioKz8ifYLueceKPDfiHXvAenWUqrNqyyB7gvKi5ODznIX06Vqy+FZb/AOGlvod2qx3cdqoXLAhJR05+vH4n0rssHvQAQc9D6jvXM8xqcqS6O6LVON3fscZ8OtM1zRNHk03WLdUEcmYCsquSGySvyk45wfxp/wARNBvvEPhqOy06NZJvtCHDSKoIAbuSBXYY4x29Af8AJo5z6dqh42Tre2S1K5Fy8pieFNPuNM8KabZXSbJ4YQrrkHB57j61yni/4dT6hqp1zQLoWl+W3urMUDMP4lYdDj8K9GAoAwcjr7UqePqU6zqw6icFKNmePzeG/iRrkf2DUtQSO1f5XJnTDDvkR/MfXB6119j8PrGx8Iz6GkxJumVri4CgMxDA8DtwCAO2e9dlk+ufxP8AjRgdhW1TNK00orRCjShHzM3+xNP/ALF/sj7LH9h8kxeSBxtxz9T3+vNed6J4T8TeDfFU0mlRi90eU/Ov2hFLp64JHzjPXvyOhNerdOR1o7568557/Xsayo5hUpqSeqfcJU4vbcw9E8NWWiz3t3Eoe6vZ3llmK9ixwq/7P8+tcb438AX1zrEOveGwI73eDKgcINw6OCcDPr/9evTv85pMc5GP60UsfVp1PaXuOUItHmnimw8b+INCtLSOzjiDxFb+ETRFWIYFWBJOBxwAam+Hei+KdBmez1ZUj01ULRossbESEg9Vy3r3xXoxGTz2OfWjn+8359fyxWs8ynKi6PKrMlU7S5rjMevUdaMU4DilrzuY2uMxRin0UcwXGYoxT6KOYLjMUYp9FHMFxmKMU+ijmC46inYoxWPMRcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guPop2KMVjzGdxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRijmC42inYoxRzBcbRTsUYo5guNop2KMUcwXG0U7FGKOYLjaKdijFHMFxtFOxRRzBcfRTqKw5mZ3GYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYpcU6ijmYXG0U6ijmYXGYoxT6KOZhcdijFOorLmIuNxRinUUcwXG4oxTqKOYLjcUYp1FHMFxuKMU6ijmC43FGKdRRzBcbijFOoo5guNxRinUUcwXG4oxTqKOYLjcUYp1FHMFxuKMU6ijmC43FGKdRRzBcbijFOoo5guNxRinUUcwXG4oxTqKOYLjcUYp1FHMFxuKMU6ijmC43FGKdRRzBcbijFOoo5guNxRinUUcwXP//Z" class="logo-avatar" alt="Neleryokki logo">
    <span class="logo-nm">Neler<b>yokki</b></span>
  </a>
  <nav>
    <a href="#about" data-tr="Hakkımda" data-en="About">Hakkımda</a>
    <a href="#projects" data-tr="Projeler" data-en="Projects">Projeler</a>
    <a href="#skills" data-tr="Yetenekler" data-en="Skills">Yetenekler</a>
    <a href="#certs" data-tr="Sertifikalar" data-en="Certs">Sertifikalar</a>
    <a href="#clients" data-tr="Müşteriler" data-en="Clients">Müşteriler</a>
    <a href="#faq" data-tr="SSS" data-en="FAQ">SSS</a>
    <a href="#contact" data-tr="İletişim" data-en="Contact">İletişim</a>
  </nav>
  <div class="header-right">
    <button class="lang-btn" onclick="toggleLang()" id="langBtn">EN</button>
    <button class="hbtn" onclick="toggleTheme()" title="Tema">
      <svg id="ico-sun" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M4.93 19.07l1.41-1.41M17.66 6.34l1.41-1.41"/></svg>
      <svg id="ico-moon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="display:none"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
    </button>
    <button class="hamburger" id="hamburger" onclick="toggleMobileNav()">
      <span></span><span></span><span></span>
    </button>
  </div>
</header>

<!-- MOBILE NAV -->
<div class="mobile-nav" id="mobileNav">
  <a href="#about" onclick="closeMobileNav()" data-tr="Hakkımda" data-en="About">Hakkımda</a>
  <a href="#projects" onclick="closeMobileNav()" data-tr="Projeler" data-en="Projects">Projeler</a>
  <a href="#skills" onclick="closeMobileNav()" data-tr="Yetenekler" data-en="Skills">Yetenekler</a>
  <a href="#certs" onclick="closeMobileNav()" data-tr="Sertifikalar" data-en="Certs">Sertifikalar</a>
  <a href="#clients" onclick="closeMobileNav()" data-tr="Müşteriler" data-en="Clients">Müşteriler</a>
  <a href="#faq" onclick="closeMobileNav()" data-tr="SSS" data-en="FAQ">SSS</a>
  <a href="#contact" onclick="closeMobileNav()" data-tr="İletişim" data-en="Contact">İletişim</a>
</div>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-glow1"></div>
  <div class="hero-glow2"></div>
  <div class="hero-inner">
    <div class="eyebrow"><div class="edot"></div><span data-tr="Web Developer &amp; İçerik Üreticisi" data-en="Web Developer &amp; Content Creator">Web Developer &amp; İçerik Üreticisi</span></div>
    <h1>
      <span class="h1-small" data-tr="Merhaba, ben" data-en="Hello, I'm">Merhaba, ben</span>
      Neler<span class="h1-acc">yokki</span>
    </h1>
    <div class="now-card">
      <div class="now-dot"></div>
      <div>
        <div class="now-label" data-tr="Şu an çalışıyorum" data-en="Currently working on">Şu an çalışıyorum</div>
        <div class="now-text"><span data-tr="TamProxy" data-en="TamProxy">TamProxy</span> &mdash; <span style="color:var(--text2);font-weight:400;font-size:.8rem" data-tr="Proxy platformu geliştirme" data-en="Proxy platform development">Proxy platformu geliştirme</span></div>
      </div>
    </div>
    <p class="hero-desc">
      <span data-tr="Oyun toplulukları, forum platformları ve özel web projeleri geliştiren bir" data-en="A full-stack developer building game communities, forum platforms and custom web projects.">Oyun toplulukları, forum platformları ve özel web projeleri geliştiren bir</span>
      <strong data-tr="full-stack developer" data-en="full-stack developer">full-stack developer</strong>. <span data-tr="Dark tema, modern UI/UX ve premium hissiyatlı tasarımlar benim dünyam." data-en="Dark themes, modern UI/UX and premium-feeling designs are my world.">Dark tema, modern UI/UX ve premium hissiyatlı tasarımlar benim dünyam.</span>
    </p>
    <div class="hero-cta">
      <a href="#projects" class="bp">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" width="13"><polyline points="13 17 18 12 13 7"/><polyline points="6 17 11 12 6 7"/></svg>
        <span data-tr="Projelerimi Gör" data-en="See My Projects">Projelerimi Gör</span>
      </a>
      <a href="#contact" class="bo">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="13"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg>
        <span data-tr="İletişim" data-en="Contact">İletişim</span>
      </a>
    </div>
    <div class="social-row">
      <a href="https://instagram.com/neleryokki" target="_blank" rel="noopener" class="soc-btn instagram" title="Instagram">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="2" width="20" height="20" rx="5"/><path d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg>
      </a>
      <a href="https://x.com/neleryokki" target="_blank" rel="noopener" class="soc-btn twitter" title="X / Twitter">
        <svg viewBox="0 0 24 24" fill="currentColor" stroke="none" width="16"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
      </a>
      <a href="https://github.com/neleryokki" target="_blank" rel="noopener" class="soc-btn github" title="GitHub">
        <svg viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/></svg>
      </a>
      <a href="https://discord.gg/neleryokki" target="_blank" rel="noopener" class="soc-btn discord" title="Discord">
        <svg viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 00-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 00-5.487 0 12.36 12.36 0 00-.617-1.23A.077.077 0 008.562 3c-1.714.29-3.354.8-4.885 1.491a.07.07 0 00-.032.027C.533 9.093-.32 13.555.099 17.961a.08.08 0 00.031.055 20.03 20.03 0 005.993 2.98.078.078 0 00.084-.026c.462-.62.874-1.275 1.226-1.963.021-.04.001-.088-.041-.104a13.2 13.2 0 01-1.872-.878.075.075 0 01-.008-.125c.126-.093.252-.19.372-.287a.075.075 0 01.078-.01c3.927 1.764 8.18 1.764 12.061 0a.075.075 0 01.079.009c.12.098.245.195.372.288a.075.075 0 01-.006.125c-.598.344-1.22.635-1.873.877a.075.075 0 00-.041.105c.36.687.772 1.341 1.225 1.962a.077.077 0 00.084.028 19.963 19.963 0 006.002-2.981.076.076 0 00.032-.054c.5-5.094-.838-9.52-3.549-13.442a.06.06 0 00-.031-.028z"/></svg>
      </a>
    </div>
  </div>
</section>

<!-- TECH STRIP -->
<div class="tech-strip">
  <span class="tech-strip-label" data-tr="Teknolojiler" data-en="Tech Stack">Teknolojiler</span>
  <div class="tech-divider"></div>
  <div class="tech-item"><svg viewBox="0 0 24 24" fill="#e34c26"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.438L1.5 0zm7.031 9.75l-.232-2.718 10.059.003.23-2.622L5.412 4.41l.698 8.01h9.126l-.326 3.426-2.91.804-2.955-.81-.188-2.11H6.248l.33 4.171L12 19.351l5.379-1.443.744-8.157H8.531z"/></svg><span>HTML</span></div>
  <div class="tech-item"><svg viewBox="0 0 24 24" fill="#264de4"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.438L1.5 0zm17.09 4.413L5.41 4.41l.213 2.622 10.125.003-.255 2.716h-6.64l.24 2.573h6.182l-.366 3.523-2.91.804-2.956-.81-.188-2.11h-2.61l.29 3.855L12 19.288l5.373-1.53L18.59 4.414z"/></svg><span>CSS</span></div>
  <div class="tech-item"><svg viewBox="0 0 24 24" fill="#f7df1e"><rect width="24" height="24" rx="2"/><path fill="#000" d="M6.186 20.459l1.717-1.04c.331.588.633.986 1.218.986.562 0 .917-.22.917-1.076v-5.815h2.11v5.843c0 2.228-1.307 3.242-3.212 3.242-1.717 0-2.717-.89-3.217-1.96M13.67 20.18l1.717-1.013c.454.741.987 1.249 1.974 1.249.824 0 1.35-.412 1.35-1.004 0-.688-.55-.946-1.48-1.358l-.509-.22c-1.468-.624-2.44-1.413-2.44-3.073 0-1.524 1.162-2.688 2.975-2.688 1.29 0 2.22.454 2.89 1.634l-1.634 1.04c-.344-.619-.714-.824-1.249-.824-.564 0-.921.357-.921.824 0 .577.357.811 1.179 1.167l.509.22c1.727.742 2.699 1.496 2.699 3.2 0 1.836-1.442 2.85-3.38 2.85-1.88 0-3.097-.896-3.69-2.009"/></svg><span>JavaScript</span></div>
  <div class="tech-item"><svg viewBox="0 0 24 24" fill="#5865f2"><path d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 00-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 00-5.487 0 12.36 12.36 0 00-.617-1.23A.077.077 0 008.562 3c-1.714.29-3.354.8-4.885 1.491a.07.07 0 00-.032.027C.533 9.093-.32 13.555.099 17.961a.08.08 0 00.031.055 20.03 20.03 0 005.993 2.98.078.078 0 00.084-.026c.462-.62.874-1.275 1.226-1.963.021-.04.001-.088-.041-.104a13.2 13.2 0 01-1.872-.878.075.075 0 01-.008-.125c.126-.093.252-.19.372-.287a.075.075 0 01.078-.01c3.927 1.764 8.18 1.764 12.061 0a.075.075 0 01.079.009c.12.098.245.195.372.288a.075.075 0 01-.006.125c-.598.344-1.22.635-1.873.877a.075.075 0 00-.041.105c.36.687.772 1.341 1.225 1.962a.077.077 0 00.084.028 19.963 19.963 0 006.002-2.981.076.076 0 00.032-.054c.5-5.094-.838-9.52-3.549-13.442a.06.06 0 00-.031-.028z"/></svg><span>Discord.js</span></div>
  <div class="tech-item"><svg viewBox="0 0 24 24" fill="#3776ab"><path d="M14.31.18l.9.2.73.26.59.3.45.32.34.34.25.34.16.33.1.3.04.26.02.2-.01.13V8.5l-.05.63-.13.55-.21.46-.26.38-.3.31-.33.25-.35.19-.35.14-.33.1-.3.07-.26.04-.21.02H8.83l-.69.05-.59.14-.5.22-.41.27-.33.32-.27.35-.2.36-.15.37-.1.35-.07.32-.04.27-.02.21v3.06H3.23l-.21-.03-.28-.07-.32-.12-.35-.18-.36-.26-.36-.36-.35-.46-.32-.59-.28-.73-.21-.88-.14-1.05L0 11.97l.06-1.22.16-1.04.24-.87.32-.71.36-.57.4-.44.42-.33.42-.24.4-.16.36-.1.32-.05.24-.01h.16l.06.01h8.16v-.83H6.24l-.01-2.75-.02-.37.05-.34.11-.31.17-.28.25-.26.31-.23.38-.2.44-.18.51-.15.58-.12.64-.1.71-.06.77-.04.84-.02 1.27.05 1.07.13zm-6.3 1.98l-.23.33-.08.41.08.41.23.34.33.22.41.09.41-.09.33-.22.23-.34.08-.41-.08-.41-.23-.33-.33-.22-.41-.09-.41.09-.33.22z"/></svg><span>Python</span></div>
  <div class="tech-item"><svg viewBox="0 0 32 32" fill="#00b4d8"><text y="26" font-size="28" font-weight="bold" font-family="serif">M</text></svg><span>MyBB</span></div>
  <div class="tech-item"><svg viewBox="0 0 24 24" fill="#ff5722"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 14H9V8h2v8zm4 0h-2V8h2v8z"/></svg><span>Blogger</span></div>
</div>

<!-- STATS BAR -->
<div class="stats">
  <div><div class="stn" data-target="6">0</div><div class="stl" data-tr="Aktif Proje" data-en="Active Projects">Aktif Proje</div></div>
  <div><div class="stn" data-target="3">0</div><div class="stl" data-tr="Yıl Deneyim" data-en="Years Experience">Yıl Deneyim</div></div>
  <div><div class="stn" data-target="10">0</div><div class="stl" data-tr="Tamamlanan Proje" data-en="Completed Projects">Tamamlanan Proje</div></div>
  <div><div class="stn" id="inf-stat">0</div><div class="stl" data-tr="Öğrenme İsteği" data-en="Will to Learn">Öğrenme İsteği</div></div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="stag" data-tr="Kim Miyim" data-en="Who Am I">Kim Miyim</div>
  <h2 class="sh" data-tr="Hakkımda" data-en="About Me">Hakkımda</h2>
  <div class="about-grid">
    <div class="fi">
      <p class="about-p"><span data-tr="Oyun dünyasını ve yazılımı seven," data-en="Passionate about gaming and software,">Oyun dünyasını ve yazılımı seven,</span> <strong data-tr="web geliştirici &amp; içerik üreticisi" data-en="web developer &amp; content creator">web geliştirici &amp; içerik üreticisi</strong> <span data-tr="olarak aktif projeler üretiyorum. Bloglardan Discord benzeri platformlara, forum temalarına ve özel web sitelerine kadar geniş bir yelpazede çalışıyorum." data-en="actively building projects. From blogs to Discord-like platforms, forum themes and custom websites.">olarak aktif projeler üretiyorum. Bloglardan Discord benzeri platformlara, forum temalarına ve özel web sitelerine kadar geniş bir yelpazede çalışıyorum.</span></p>
      <p class="about-p"><strong data-tr="Modern &amp; minimalist tasarım" data-en="Modern &amp; minimalist design">Modern &amp; minimalist tasarım</strong> <span data-tr="anlayışım, dark tema sevgim ve oyun odaklı içeriklerim benimle özdeşleşmiş. Kullanıcı deneyimini ön planda tutarak premium hissiyatlı arayüzler inşa ediyorum." data-en="philosophy, love for dark themes and game-focused content define my work. I build premium-feeling interfaces with user experience as priority.">anlayışım, dark tema sevgim ve oyun odaklı içeriklerim benimle özdeşleşmiş. Kullanıcı deneyimini ön planda tutarak premium hissiyatlı arayüzler inşa ediyorum.</span></p>
      <div style="display:flex;gap:1rem;flex-wrap:wrap;margin-top:1.75rem">
        <a href="https://tamproxy.com.tr" target="_blank" rel="noopener" class="bp" style="font-size:.68rem;padding:.6rem 1.2rem">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="12"><path d="M12 2a10 10 0 100 20A10 10 0 0012 2z"/><path d="M2 12h20M12 2a15.3 15.3 0 010 20M12 2a15.3 15.3 0 000 20"/></svg>
          tamproxy.com.tr
        </a>
        <a href="#projects" class="bo" style="font-size:.68rem;padding:.6rem 1.2rem">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="12"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg>
          <span data-tr="Tüm Projeler" data-en="All Projects">Tüm Projeler</span>
        </a>
      </div>
    </div>
    <div class="spec-box fi">
      <div class="spec-top"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="3" width="20" height="14" rx="2"/><path d="M8 21h8M12 17v4"/></svg><span data-tr="Sistem Konfigürasyonu" data-en="System Specs">Sistem Konfigürasyonu</span></div>
      <div class="spec-row"><div class="spec-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#00aaff" stroke-width="1.8"><rect x="4" y="4" width="16" height="16" rx="2"/><rect x="9" y="9" width="6" height="6" rx="1"/><path d="M9 1v3M15 1v3M9 20v3M15 20v3M1 9h3M1 15h3M20 9h3M20 15h3"/></svg></div><div><div class="spec-nm">AMD Ryzen 5 5600</div><div class="spec-vl">CPU · 6 Core / 12 Thread</div></div></div>
      <div class="spec-row"><div class="spec-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#f59e0b" stroke-width="1.8"><path d="M9 3H5a2 2 0 00-2 2v14a2 2 0 002 2h14a2 2 0 002-2V9l-6-6z"/><polyline points="9 3 9 9 15 9"/></svg></div><div><div class="spec-nm">ASUS PRIME A520M-R</div><div class="spec-vl">Anakart · AM4</div></div></div>
      <div class="spec-row"><div class="spec-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="1.8"><rect x="2" y="8" width="20" height="8" rx="2"/><path d="M6 8V6a2 2 0 012-2h8a2 2 0 012 2v2M6 16v2a2 2 0 002 2h8a2 2 0 002-2v-2"/></svg></div><div><div class="spec-nm">GOODRAM IRDM PRO 8GB</div><div class="spec-vl">RAM · DDR4</div></div></div>
      <div class="spec-row"><div class="spec-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#f97316" stroke-width="1.8"><rect x="2" y="6" width="20" height="12" rx="2"/><path d="M6 12h4M14 12h4"/></svg></div><div><div class="spec-nm">ASUS RTX 3050 Dual</div><div class="spec-vl">GPU · 8GB GDDR6</div></div></div>
      <div class="spec-row"><div class="spec-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#a855f7" stroke-width="1.8"><ellipse cx="12" cy="12" rx="10" ry="7"/><ellipse cx="12" cy="12" rx="5" ry="3"/><line x1="2" y1="12" x2="22" y2="12"/></svg></div><div><div class="spec-nm">GOODRAM PX500 GEN3 1TB</div><div class="spec-vl">SSD · M.2 NVMe</div></div></div>
    </div>
  </div>
</section>

<hr class="div">

<!-- PROJECTS -->
<section id="projects" class="alt">
  <div class="stag" data-tr="Ne Yaptım" data-en="What I Built">Ne Yaptım</div>
  <h2 class="sh" data-tr="Projelerim" data-en="My Projects">Projelerim</h2>
  <div class="pgrid">
    <a href="https://tamproxy.com.tr" target="_blank" rel="noopener" class="pcard fi">
      <div class="prev-wrap"><iframe src="https://tamproxy.com.tr" title="tamproxy.com.tr" loading="lazy" sandbox="allow-scripts allow-same-origin"></iframe><div class="prev-overlay"></div><div class="prev-lbl">Live</div></div>
      <div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#00aaff" stroke-width="1.8"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg></div><span class="pbadge bon" data-tr="Aktif" data-en="Active">Aktif</span></div><div class="pname">TamProxy</div><div class="purl">tamproxy.com.tr</div><div class="pdesc" data-tr="Güvenli ve hızlı proxy hizmetleri platformu. Premium dark temalı özel web projesi." data-en="Secure and fast proxy services platform. Premium dark theme custom web project.">Güvenli ve hızlı proxy hizmetleri platformu. Premium dark temalı özel web projesi.</div><div class="ptags"><span class="ptag">Proxy</span><span class="ptag">Web</span></div></div>
    </a>
    <a href="https://lolaforum.com.tr" target="_blank" rel="noopener" class="pcard fi">
      <div class="prev-wrap"><iframe src="https://lolaforum.com.tr" title="lolaforum.com.tr" loading="lazy" sandbox="allow-scripts allow-same-origin"></iframe><div class="prev-overlay"></div><div class="prev-lbl">Live</div></div>
      <div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#00aaff" stroke-width="1.8"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg></div><span class="pbadge bon" data-tr="Aktif" data-en="Active">Aktif</span></div><div class="pname">LolaForum</div><div class="purl">lolaforum.com.tr</div><div class="pdesc" data-tr="MyBB tabanlı premium forum sitesi. Dark temalı oyun topluluğu platformu." data-en="Premium MyBB-based forum. Dark themed gaming community platform.">MyBB tabanlı premium forum sitesi. Dark temalı oyun topluluğu platformu.</div><div class="ptags"><span class="ptag">Forum</span><span class="ptag">MyBB</span></div></div>
    </a>
    <a href="https://frostsubs.com.tr" target="_blank" rel="noopener" class="pcard fi">
      <div class="prev-wrap"><iframe src="https://frostsubs.com.tr" title="frostsubs.com.tr" loading="lazy" sandbox="allow-scripts allow-same-origin"></iframe><div class="prev-overlay"></div><div class="prev-lbl">Live</div></div>
      <div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#00aaff" stroke-width="1.8"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg></div><span class="pbadge bon" data-tr="Aktif" data-en="Active">Aktif</span></div><div class="pname">FrostSubs</div><div class="purl">frostsubs.com.tr</div><div class="pdesc" data-tr="Türkçe anime izleme platformu." data-en="Turkish anime streaming platform.">Türkçe anime izleme platformu.</div><div class="ptags"><span class="ptag">Anime</span><span class="ptag">Streaming</span></div></div>
    </a>
    <div class="pcard fi"><div class="noprev"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3"><path d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 00-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 00-5.487 0 12.36 12.36 0 00-.617-1.23A.077.077 0 008.562 3c-1.714.29-3.354.8-4.885 1.491a.07.07 0 00-.032.027C.533 9.093-.32 13.555.099 17.961a.08.08 0 00.031.055 20.03 20.03 0 005.993 2.98.078.078 0 00.084-.026c.462-.62.874-1.275 1.226-1.963.021-.04.001-.088-.041-.104a13.2 13.2 0 01-1.872-.878.075.075 0 01-.008-.125c.126-.093.252-.19.372-.287a.075.075 0 01.078-.01c3.927 1.764 8.18 1.764 12.061 0a.075.075 0 01.079.009c.12.098.245.195.372.288a.075.075 0 01-.006.125c-.598.344-1.22.635-1.873.877a.075.075 0 00-.041.105c.36.687.772 1.341 1.225 1.962a.077.077 0 00.084.028 19.963 19.963 0 006.002-2.981.076.076 0 00.032-.054c.5-5.094-.838-9.52-3.549-13.442a.06.06 0 00-.031-.028z"/></svg></div><div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#00aaff" stroke-width="1.8"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0110 0v4"/></svg></div><span class="pbadge bon" data-tr="Aktif" data-en="Active">Aktif</span></div><div class="pname">Discord Token Generator</div><div class="purl">Neleryokki · Özel</div><div class="pdesc" data-tr="Discord araçları için özel platform." data-en="Custom platform for Discord tools.">Discord araçları için özel platform.</div><div class="ptags"><span class="ptag">Discord</span><span class="ptag">Tool</span></div></div></div>
    <div class="pcard fi off"><div class="noprev"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 002 1.61h9.72a2 2 0 001.99-1.85L23 6H6"/></svg></div><div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#555" stroke-width="1.8"><path d="M6 2L3 6v14a2 2 0 002 2h14a2 2 0 002-2V6l-3-4zM3 6h18"/><path d="M16 10a4 4 0 01-8 0"/></svg></div><span class="pbadge boff" data-tr="Bırakıldı" data-en="Archived">Bırakıldı</span></div><div class="pname">MegaXShop</div><div class="purl">megaxshop.com.tr</div><div class="pdesc" data-tr="E-ticaret platformu." data-en="E-commerce platform.">E-ticaret platformu.</div><div class="ptags"><span class="ptag">Shop</span></div></div></div>
    <div class="pcard fi off"><div class="noprev"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg></div><div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#555" stroke-width="1.8"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg></div><span class="pbadge boff" data-tr="Bırakıldı" data-en="Archived">Bırakıldı</span></div><div class="pname">GGChat</div><div class="purl">gchat.optikl.ink</div><div class="pdesc" data-tr="Discord benzeri sohbet platformu." data-en="Discord-like chat platform.">Discord benzeri sohbet platformu.</div><div class="ptags"><span class="ptag">Chat</span></div></div></div>
    <div class="pcard fi off"><div class="noprev"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.3"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg></div><div class="pbody"><div class="phead"><div class="pico"><svg viewBox="0 0 24 24" fill="none" stroke="#555" stroke-width="1.8"><polygon points="23 7 16 12 23 17 23 7"/><rect x="1" y="5" width="15" height="14" rx="2"/></svg></div><span class="pbadge boff" data-tr="Bırakıldı" data-en="Archived">Bırakıldı</span></div><div class="pname">SinemaKulesi</div><div class="purl">sinemakulesi</div><div class="pdesc" data-tr="Film platformu." data-en="Movie streaming platform.">Film platformu.</div><div class="ptags"><span class="ptag">Film</span></div></div></div>
  </div>
</section>

<hr class="div">

<!-- SKILLS -->
<section id="skills">
  <div class="stag" data-tr="Ne Biliyorum" data-en="What I Know">Ne Biliyorum</div>
  <h2 class="sh" data-tr="Yetenekler" data-en="Skills">Yetenekler</h2>
  <div class="sgrid">
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M10 13a5 5 0 007.54.54l3-3a5 5 0 00-7.07-7.07l-1.72 1.71"/><path d="M14 11a5 5 0 00-7.54-.54l-3 3a5 5 0 007.07 7.07l1.71-1.71"/></svg></div><span class="snm">HTML / CSS</span></div><div class="strack"><div class="sfill" data-w="90"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/></svg></div><span class="snm">JavaScript</span></div><div class="strack"><div class="sfill" data-w="80"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M8 14s1.5 2 4 2 4-2 4-2"/><line x1="9" y1="9" x2="9.01" y2="9"/><line x1="15" y1="9" x2="15.01" y2="9"/></svg></div><span class="snm">UI/UX Tasarım</span></div><div class="strack"><div class="sfill" data-w="85"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 00-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 00-5.487 0 12.36 12.36 0 00-.617-1.23A.077.077 0 008.562 3c-1.714.29-3.354.8-4.885 1.491a.07.07 0 00-.032.027C.533 9.093-.32 13.555.099 17.961a.08.08 0 00.031.055 20.03 20.03 0 005.993 2.98.078.078 0 00.084-.026c.462-.62.874-1.275 1.226-1.963.021-.04.001-.088-.041-.104a13.2 13.2 0 01-1.872-.878.075.075 0 01-.008-.125c.126-.093.252-.19.372-.287a.075.075 0 01.078-.01c3.927 1.764 8.18 1.764 12.061 0a.075.075 0 01.079.009c.12.098.245.195.372.288a.075.075 0 01-.006.125c-.598.344-1.22.635-1.873.877a.075.075 0 00-.041.105c.36.687.772 1.341 1.225 1.962a.077.077 0 00.084.028 19.963 19.963 0 006.002-2.981.076.076 0 00.032-.054c.5-5.094-.838-9.52-3.549-13.442a.06.06 0 00-.031-.028z"/></svg></div><span class="snm">Discord.py/.js</span></div><div class="strack"><div class="sfill" data-w="75"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8z"/><polyline points="14 2 14 8 20 8"/></svg></div><span class="snm">MyBB Tema Dev</span></div><div class="strack"><div class="sfill" data-w="88"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="3" width="7" height="7" rx="1"/><rect x="14" y="3" width="7" height="7" rx="1"/><rect x="3" y="14" width="7" height="7" rx="1"/><rect x="14" y="14" width="7" height="7" rx="1"/></svg></div><span class="snm">Blogger / CMS</span></div><div class="strack"><div class="sfill" data-w="70"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 16V8a2 2 0 00-1-1.73l-7-4a2 2 0 00-2 0l-7 4A2 2 0 003 8v8a2 2 0 001 1.73l7 4a2 2 0 002 0l7-4A2 2 0 0021 16z"/></svg></div><span class="snm">Game Dev</span></div><div class="strack"><div class="sfill" data-w="55"></div></div></div>
    <div class="sbox fi"><div class="shead"><div class="sico"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg></div><span class="snm">Dark Theme Design</span></div><div class="strack"><div class="sfill" data-w="95"></div></div></div>
  </div>
</section>

<hr class="div">

<!-- CERTS -->
<section id="certs" class="alt">
  <div class="stag" data-tr="Başarılar" data-en="Achievements">Başarılar</div>
  <h2 class="sh" data-tr="Sertifikalar &amp; Rozetler" data-en="Certifications &amp; Badges">Sertifikalar &amp; Rozetler</h2>
  <div class="certs-grid">
    <div class="cert-card fi"><div class="cert-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#f59e0b" stroke-width="1.8"><circle cx="12" cy="8" r="6"/><path d="M15.477 12.89L17 22l-5-3-5 3 1.523-9.11"/></svg></div><div><div class="cert-title" data-tr="Web Geliştirme Temelleri" data-en="Web Development Fundamentals">Web Geliştirme Temelleri</div><div class="cert-sub" data-tr="HTML, CSS, JS · Öz çalışma" data-en="HTML, CSS, JS · Self-taught">HTML, CSS, JS · Öz çalışma</div><span class="cert-badge badge-gold" data-tr="Tamamlandı" data-en="Completed">Tamamlandı</span></div></div>
    <div class="cert-card fi"><div class="cert-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#5865f2" stroke-width="1.8"><path d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 00-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 00-5.487 0 12.36 12.36 0 00-.617-1.23A.077.077 0 008.562 3c-1.714.29-3.354.8-4.885 1.491"/></svg></div><div><div class="cert-title">Discord Bot Development</div><div class="cert-sub" data-tr="discord.py &amp; discord.js · Aktif proje" data-en="discord.py &amp; discord.js · Active project">discord.py &amp; discord.js · Aktif proje</div><span class="cert-badge badge-blue" data-tr="Aktif" data-en="Active">Aktif</span></div></div>
    <div class="cert-card fi"><div class="cert-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#00aaff" stroke-width="1.8"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg></div><div><div class="cert-title" data-tr="MyBB Tema Geliştirme" data-en="MyBB Theme Development">MyBB Tema Geliştirme</div><div class="cert-sub" data-tr="Forum yazılımı özelleştirme uzmanı" data-en="Forum software customization expert">Forum yazılımı özelleştirme uzmanı</div><span class="cert-badge badge-blue" data-tr="Uzman" data-en="Expert">Uzman</span></div></div>
    <div class="cert-card fi"><div class="cert-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#10b981" stroke-width="1.8"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg></div><div><div class="cert-title" data-tr="UI/UX Dark Tema Tasarımı" data-en="UI/UX Dark Theme Design">UI/UX Dark Tema Tasarımı</div><div class="cert-sub" data-tr="Premium arayüz &amp; oyun odaklı tasarım" data-en="Premium interfaces &amp; game-focused design">Premium arayüz &amp; oyun odaklı tasarım</div><span class="cert-badge badge-green" data-tr="Uzman" data-en="Expert">Uzman</span></div></div>
    <div class="cert-card fi"><div class="cert-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#f97316" stroke-width="1.8"><path d="M21 16V8a2 2 0 00-1-1.73l-7-4a2 2 0 00-2 0l-7 4A2 2 0 003 8v8a2 2 0 001 1.73l7 4a2 2 0 002 0l7-4A2 2 0 0021 16z"/></svg></div><div><div class="cert-title" data-tr="Oyun Geliştirme Temelleri" data-en="Game Development Basics">Oyun Geliştirme Temelleri</div><div class="cert-sub" data-tr="Pixel Worlds &amp; Growtopia benzeri projeler" data-en="Pixel Worlds &amp; Growtopia-like projects">Pixel Worlds &amp; Growtopia benzeri projeler</div><span class="cert-badge badge-gold" data-tr="Devam Ediyor" data-en="In Progress">Devam Ediyor</span></div></div>
    <div class="cert-card fi"><svg viewBox="0 0 24 24" fill="none" stroke="#3776ab" stroke-width="1.8" style="width:18px;height:18px;flex-shrink:0;margin-top:.25rem"><path d="M14.31.18l.9.2.73.26.59.3.45.32.34.34.25.34.16.33.1.3.04.26.02.2-.01.13V8.5l-.05.63-.13.55-.21.46-.26.38-.3.31-.33.25-.35.19-.35.14-.33.1-.3.07-.26.04-.21.02H8.83"/></svg><div><div class="cert-title">Python / discord.py</div><div class="cert-sub" data-tr="Bot geliştirme &amp; otomasyon" data-en="Bot development &amp; automation">Bot geliştirme &amp; otomasyon</div><span class="cert-badge badge-blue" data-tr="Öğreniliyor" data-en="Learning">Öğreniliyor</span></div></div>
  </div>
</section>

<hr class="div">

<!-- CLIENTS -->
<section id="clients">
  <div class="stag" data-tr="Ne Dediler" data-en="What They Said">Ne Dediler</div>
  <h2 class="sh" data-tr="Müşteri Yorumları" data-en="Client Reviews">Müşteri Yorumları</h2>
  <div class="clients-grid">
    <div class="tcard fi"><div class="tcard-project" data-tr="Forum Projesi" data-en="Forum Project">Forum Projesi</div><div class="tcard-quote">"</div><p class="tcard-text"><span data-tr="Siteyi tam istediğimiz gibi yaptı." data-en="Built the site exactly as we wanted.">Siteyi tam istediğimiz gibi yaptı.</span> <b data-tr="Dark tema tasarımı gerçekten profesyonel" data-en="The dark theme design is truly professional">Dark tema tasarımı gerçekten profesyonel</b> <span data-tr="görünüyor. Hızlı teslim, sorunsuz iletişim." data-en="looking. Fast delivery, smooth communication.">görünüyor. Hızlı teslim, sorunsuz iletişim.</span></p><div class="tcard-footer"><div class="tcard-avatar">MK</div><div><div class="tcard-name">Murat K.</div><div class="tcard-role">Forum Sahibi</div><div class="tcard-stars"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div></div></div></div>
    <div class="tcard fi"><div class="tcard-project">Discord Bot</div><div class="tcard-quote">"</div><p class="tcard-text"><b data-tr="Özel komutlar ve otomasyon sistemleri" data-en="Custom commands and automation systems">Özel komutlar ve otomasyon sistemleri</b> <span data-tr="tam istediğim gibi çalışıyor. Sunucum artık çok daha aktif." data-en="work exactly as I wanted. My server is much more active now.">tam istediğim gibi çalışıyor. Sunucum artık çok daha aktif.</span></p><div class="tcard-footer"><div class="tcard-avatar">AY</div><div><div class="tcard-name">Ahmet Y.</div><div class="tcard-role">Discord Yöneticisi</div><div class="tcard-stars"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div></div></div></div>
    <div class="tcard fi"><div class="tcard-project" data-tr="Blogger Tema" data-en="Blogger Theme">Blogger Tema</div><div class="tcard-quote">"</div><p class="tcard-text"><span data-tr="Bloğum için yaptığı" data-en="The">Bloğum için yaptığı</span> <b data-tr="özel Blogger teması tam anlamıyla premium" data-en="custom Blogger theme is truly premium">özel Blogger teması tam anlamıyla premium</b> <span data-tr="görünüyor. SEO uyumlu ve hızlı." data-en="looking. SEO friendly and fast.">görünüyor. SEO uyumlu ve hızlı.</span></p><div class="tcard-footer"><div class="tcard-avatar">SÇ</div><div><div class="tcard-name">Selin Ç.</div><div class="tcard-role" data-tr="İçerik Üreticisi" data-en="Content Creator">İçerik Üreticisi</div><div class="tcard-stars"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div></div></div></div>
    <div class="tcard fi"><div class="tcard-project" data-tr="Web Sitesi" data-en="Website">Web Sitesi</div><div class="tcard-quote">"</div><p class="tcard-text"><span data-tr="Tasarım özgün, kod temiz." data-en="Original design, clean code.">Tasarım özgün, kod temiz.</span> <b data-tr="Revizyon taleplerime anında yanıt verdi" data-en="Responded to my revision requests instantly">Revizyon taleplerime anında yanıt verdi</b><span data-tr=", süreç çok rahat geçti." data-en=", the process was very smooth.">, süreç çok rahat geçti.</span></p><div class="tcard-footer"><div class="tcard-avatar">KT</div><div><div class="tcard-name">Kerem T.</div><div class="tcard-role" data-tr="Topluluk Yöneticisi" data-en="Community Manager">Topluluk Yöneticisi</div><div class="tcard-stars"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div></div></div></div>
    <div class="tcard fi"><div class="tcard-project" data-tr="MyBB Tema" data-en="MyBB Theme">MyBB Tema</div><div class="tcard-quote">"</div><p class="tcard-text"><b data-tr="Dark tema gerçekten efsane." data-en="The dark theme is truly legendary.">Dark tema gerçekten efsane.</b> <span data-tr="Üyelerimiz çok beğendi, kayıt oranımız arttı." data-en="Our members loved it, registration rate increased.">Üyelerimiz çok beğendi, kayıt oranımız arttı.</span></p><div class="tcard-footer"><div class="tcard-avatar">OD</div><div><div class="tcard-name">Okan D.</div><div class="tcard-role">Forum Admin</div><div class="tcard-stars"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div></div></div></div>
    <div class="tcard fi"><div class="tcard-project" data-tr="Proxy Hizmeti" data-en="Proxy Service">Proxy Hizmeti</div><div class="tcard-quote">"</div><p class="tcard-text"><span data-tr="TamProxy üzerinden aldığım hizmet" data-en="The service I received through TamProxy was">TamProxy üzerinden aldığım hizmet</span> <b data-tr="stabil ve hızlıydı." data-en="stable and fast.">stabil ve hızlıydı.</b> <span data-tr="Bir dahaki projemde de çalışmayı düşünüyorum." data-en="I plan to work together on my next project too.">Bir dahaki projemde de çalışmayı düşünüyorum.</span></p><div class="tcard-footer"><div class="tcard-avatar">EV</div><div><div class="tcard-name">Emre V.</div><div class="tcard-role" data-tr="Yazılım Geliştirici" data-en="Software Developer">Yazılım Geliştirici</div><div class="tcard-stars"><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg><svg viewBox="0 0 24 24"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg></div></div></div></div>
  </div>
</section>

<hr class="div">

<!-- FAQ -->
<section id="faq" class="alt">
  <div class="stag" data-tr="Merak Edilenler" data-en="Common Questions">Merak Edilenler</div>
  <h2 class="sh" data-tr="Sıkça Sorulan Sorular" data-en="FAQ">Sıkça Sorulan Sorular</h2>
  <div class="faq-list">
    <div class="faq-item fi" onclick="toggleFaq(this)"><div class="faq-q"><span class="faq-q-text" data-tr="Bir proje ne kadar sürede tamamlanır?" data-en="How long does a project take to complete?">Bir proje ne kadar sürede tamamlanır?</span><div class="faq-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div><div class="faq-a"><span data-tr="Projenin kapsamına göre değişir. Basit bir forum teması 1–3 gün, kapsamlı bir web sitesi 1–2 hafta alabilir. Başlamadan önce net bir zaman çizelgesi paylaşırım." data-en="It depends on the scope. A simple forum theme takes 1–3 days, a full website 1–2 weeks. I share a clear timeline before starting.">Projenin kapsamına göre değişir. Basit bir forum teması 1–3 gün, kapsamlı bir web sitesi 1–2 hafta alabilir. Başlamadan önce net bir zaman çizelgesi paylaşırım.</span></div></div>
    <div class="faq-item fi" onclick="toggleFaq(this)"><div class="faq-q"><span class="faq-q-text" data-tr="Revizyon hakkı var mı?" data-en="Are revisions included?">Revizyon hakkı var mı?</span><div class="faq-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div><div class="faq-a"><span data-tr="Evet, teslimattan sonra makul revizyon talepleri ücretsiz karşılanır. Temel düzeltmeler ve ayarlamalar için ek ücret talep etmiyorum." data-en="Yes, reasonable revision requests after delivery are free. I don't charge extra for basic fixes and adjustments.">Evet, teslimattan sonra makul revizyon talepleri ücretsiz karşılanır. Temel düzeltmeler ve ayarlamalar için ek ücret talep etmiyorum.</span></div></div>
    <div class="faq-item fi" onclick="toggleFaq(this)"><div class="faq-q"><span class="faq-q-text" data-tr="Ödeme nasıl yapılıyor?" data-en="How does payment work?">Ödeme nasıl yapılıyor?</span><div class="faq-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div><div class="faq-a"><span data-tr="Genellikle %50 peşin, %50 teslimatta şeklinde çalışırım. Küçük projeler için tam ödeme de kabul edilir. Detaylar için WhatsApp'tan yazabilirsin." data-en="I usually work with 50% upfront and 50% on delivery. Full payment is also accepted for small projects. Message me on WhatsApp for details.">Genellikle %50 peşin, %50 teslimatta şeklinde çalışırım. Küçük projeler için tam ödeme de kabul edilir. Detaylar için WhatsApp'tan yazabilirsin.</span></div></div>
    <div class="faq-item fi" onclick="toggleFaq(this)"><div class="faq-q"><span class="faq-q-text" data-tr="Hangi platformlarda tema geliştiriyorsun?" data-en="Which platforms do you develop themes for?">Hangi platformlarda tema geliştiriyorsun?</span><div class="faq-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div><div class="faq-a"><span data-tr="MyBB, Blogger ve özel HTML/CSS/JS projeleri için tema ve arayüz geliştiriyorum. WordPress ve diğer platformlar için de yardımcı olabilir." data-en="I develop themes and interfaces for MyBB, Blogger and custom HTML/CSS/JS projects. I can also help with WordPress and other platforms.">MyBB, Blogger ve özel HTML/CSS/JS projeleri için tema ve arayüz geliştiriyorum. WordPress ve diğer platformlar için de yardımcı olabilir.</span></div></div>
    <div class="faq-item fi" onclick="toggleFaq(this)"><div class="faq-q"><span class="faq-q-text" data-tr="Discord botu nasıl sipariş edebilirim?" data-en="How do I order a Discord bot?">Discord botu nasıl sipariş edebilirim?</span><div class="faq-icon"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg></div></div><div class="faq-a"><span data-tr="WhatsApp veya Discord üzerinden ulaşabilirsin. Ne tür komutlar ve özellikler istediğini anlat, sana en uygun çözümü birlikte belirleriz." data-en="You can reach me via WhatsApp or Discord. Tell me what commands and features you want, and we'll figure out the best solution together.">WhatsApp veya Discord üzerinden ulaşabilirsin. Ne tür komutlar ve özellikler istediğini anlat, sana en uygun çözümü birlikte belirleriz.</span></div></div>
  </div>
</section>

<hr class="div">

<!-- CONTACT -->
<section id="contact">
  <div class="stag" data-tr="Ulaşın" data-en="Get In Touch">Ulaşın</div>
  <h2 class="sh" data-tr="İletişim" data-en="Contact">İletişim</h2>
  <div style="max-width:540px" class="fi">
    <p style="color:var(--text2);line-height:1.85;font-size:.93rem;margin-bottom:2rem" data-tr="Bir proje fikriniz mi var? İş birliği yapmak mı istiyorsunuz? Her halükarda ulaşabilirsiniz." data-en="Have a project idea? Want to collaborate? Feel free to reach out anytime.">Bir proje fikriniz mi var? İş birliği yapmak mı istiyorsunuz? Her halükarda ulaşabilirsiniz.</p>
    <div style="display:flex;flex-direction:column;gap:1rem">
      <a href="https://wa.me/905000000000" target="_blank" rel="noopener" class="bp" style="max-width:240px;justify-content:center">
        <svg viewBox="0 0 24 24" fill="currentColor" width="13"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
        <span data-tr="WhatsApp ile Yaz" data-en="Message on WhatsApp">WhatsApp ile Yaz</span>
      </a>
      <a href="mailto:neleryokki@gmail.com" class="bo" style="max-width:240px;justify-content:center">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="13"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        <span data-tr="E-posta Gönder" data-en="Send Email">E-posta Gönder</span>
      </a>
      <div class="social-row" style="margin-top:.5rem">
        <a href="https://instagram.com/neleryokki" target="_blank" rel="noopener" class="soc-btn instagram" title="Instagram"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="2" width="20" height="20" rx="5"/><path d="M16 11.37A4 4 0 1112.63 8 4 4 0 0116 11.37z"/><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"/></svg></a>
        <a href="https://x.com/neleryokki" target="_blank" rel="noopener" class="soc-btn twitter" title="X / Twitter"><svg viewBox="0 0 24 24" fill="currentColor" stroke="none" width="16"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg></a>
        <a href="https://github.com/neleryokki" target="_blank" rel="noopener" class="soc-btn github" title="GitHub"><svg viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/></svg></a>
        <a href="https://discord.gg/neleryokki" target="_blank" rel="noopener" class="soc-btn discord" title="Discord"><svg viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M20.317 4.492c-1.53-.69-3.17-1.2-4.885-1.49a.075.075 0 00-.079.036c-.21.369-.444.85-.608 1.23a18.566 18.566 0 00-5.487 0 12.36 12.36 0 00-.617-1.23A.077.077 0 008.562 3c-1.714.29-3.354.8-4.885 1.491a.07.07 0 00-.032.027C.533 9.093-.32 13.555.099 17.961a.08.08 0 00.031.055 20.03 20.03 0 005.993 2.98.078.078 0 00.084-.026c.462-.62.874-1.275 1.226-1.963.021-.04.001-.088-.041-.104a13.2 13.2 0 01-1.872-.878.075.075 0 01-.008-.125c.126-.093.252-.19.372-.287a.075.075 0 01.078-.01c3.927 1.764 8.18 1.764 12.061 0a.075.075 0 01.079.009c.12.098.245.195.372.288a.075.075 0 01-.006.125c-.598.344-1.22.635-1.873.877a.075.075 0 00-.041.105c.36.687.772 1.341 1.225 1.962a.077.077 0 00.084.028 19.963 19.963 0 006.002-2.981.076.076 0 00.032-.054c.5-5.094-.838-9.52-3.549-13.442a.06.06 0 00-.031-.028z"/></svg></a>
      </div>
    </div>
  </div>
</section>

<footer>
  <div>
    <div class="fbrand">Neler<b>yokki</b></div>
    <div class="fcopy">© 2025 Neleryokki · Web Developer & İçerik Üreticisi</div>
  </div>
  <div class="flinks">
    <a href="#about" data-tr="Hakkımda" data-en="About">Hakkımda</a>
    <a href="#projects" data-tr="Projeler" data-en="Projects">Projeler</a>
    <a href="#certs" data-tr="Sertifikalar" data-en="Certs">Sertifikalar</a>
    <a href="#clients" data-tr="Müşteriler" data-en="Clients">Müşteriler</a>
    <a href="#faq" data-tr="SSS" data-en="FAQ">SSS</a>
    <a href="#contact" data-tr="İletişim" data-en="Contact">İletişim</a>
  </div>
</footer>

<!-- WA -->
<div class="wa-wrap">
  <div class="wa-tip" id="waTip" data-tr="💬 Benimle iletişime geçin" data-en="💬 Get in touch with me">💬 Benimle iletişime geçin</div>
  <a href="https://wa.me/905000000000" target="_blank" rel="noopener" class="wa-btn">
    <svg viewBox="0 0 24 24"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
  </a>
</div>
<button class="stbtn" id="stbtn" onclick="window.scrollTo({top:0,behavior:'smooth'})"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="18 15 12 9 6 15"/></svg></button>

<!-- COOKIE -->
<div id="cookie">
  <span class="cookie-text" data-tr="Bu site çerez kullanır. Daha fazla bilgi için <a href='#'>Gizlilik Politikası</a>'nı inceleyin." data-en="This site uses cookies. See our <a href='#'>Privacy Policy</a> for more info.">Bu site çerez kullanır. Daha fazla bilgi için <a href="#">Gizlilik Politikası</a>'nı inceleyin.</span>
  <div class="cookie-btns">
    <button class="cookie-ok" onclick="acceptCookie()">Kabul Et</button>
    <button class="cookie-no" onclick="document.getElementById('cookie').remove()">Reddet</button>
  </div>
</div>

<script>
/* CURSOR */
const ring=document.getElementById('cursor-ring'),dot=document.getElementById('cursor-dot');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;dot.style.left=mx+'px';dot.style.top=my+'px'});
(function tick(){rx+=(mx-rx)*.11;ry+=(my-ry)*.11;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(tick)})();
document.querySelectorAll('a,button,.pcard,.sbox,.spec-row,.cert-card,.tcard,.faq-item').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ring.style.width='50px';ring.style.height='50px';ring.style.borderColor='rgba(0,170,255,.85)'});
  el.addEventListener('mouseleave',()=>{ring.style.width='34px';ring.style.height='34px';ring.style.borderColor='rgba(0,170,255,.5)'});
});
document.addEventListener('mouseleave',()=>{dot.style.opacity='0';ring.style.opacity='0'});
document.addEventListener('mouseenter',()=>{dot.style.opacity='1';ring.style.opacity='1'});

/* PROGRESS BAR + SCROLL TOP */
const pbar=document.getElementById('pbar'),stbtn=document.getElementById('stbtn');
window.addEventListener('scroll',()=>{
  const d=document.documentElement;
  pbar.style.width=((window.scrollY/(d.scrollHeight-d.clientHeight))*100)+'%';
  if(window.scrollY>400)stbtn.classList.add('show');else stbtn.classList.remove('show');
});

/* THEME */
function toggleTheme(){
  const h=document.documentElement,n=h.getAttribute('data-theme')==='dark'?'light':'dark';
  h.setAttribute('data-theme',n);
  document.getElementById('ico-sun').style.display=n==='dark'?'block':'none';
  document.getElementById('ico-moon').style.display=n==='dark'?'none':'block';
}

/* MOBILE NAV */
function toggleMobileNav(){
  document.getElementById('hamburger').classList.toggle('open');
  document.getElementById('mobileNav').classList.toggle('open');
}
function closeMobileNav(){
  document.getElementById('hamburger').classList.remove('open');
  document.getElementById('mobileNav').classList.remove('open');
}

/* LANGUAGE */
let currentLang='tr';
function toggleLang(){
  currentLang=currentLang==='tr'?'en':'tr';
  document.getElementById('langBtn').textContent=currentLang==='tr'?'EN':'TR';
  document.querySelectorAll('[data-tr]').forEach(el=>{
    const val=el.getAttribute('data-'+currentLang);
    if(val)el.innerHTML=val;
  });
  document.documentElement.lang=currentLang;
}

/* WA TOOLTIP */
setTimeout(()=>{const t=document.getElementById('waTip');t.classList.add('show');setTimeout(()=>t.classList.remove('show'),4000)},2000);

/* STATS COUNTER */
let statsAnimated=false;
function animateStats(){
  if(statsAnimated)return;
  statsAnimated=true;
  document.querySelectorAll('.stn[data-target]').forEach(el=>{
    const target=parseInt(el.dataset.target);
    const suffix=el.dataset.target.includes('+')? '+':'';
    let current=0;
    const step=Math.ceil(target/30);
    const timer=setInterval(()=>{
      current=Math.min(current+step,target);
      el.textContent=current+'+';
      if(current>=target)clearInterval(timer);
    },40);
  });
  // infinity
  const inf=document.getElementById('inf-stat');
  let c=0;
  const t2=setInterval(()=>{c++;inf.textContent=c;if(c>=99){clearInterval(t2);inf.textContent='∞';}},20);
}
const statsObs=new IntersectionObserver(es=>{if(es[0].isIntersecting)animateStats()},{threshold:.3});
statsObs.observe(document.querySelector('.stats'));

/* GRID CANVAS */
const cv=document.getElementById('grid-canvas'),ctx=cv.getContext('2d');
let W,H,gx=-9999,gy=-9999;
const CELL=60;
function rsz(){W=cv.width=window.innerWidth;H=cv.height=window.innerHeight}
rsz();window.addEventListener('resize',rsz);
document.addEventListener('mousemove',e=>{gx=e.clientX;gy=e.clientY});
function drawGrid(){
  ctx.clearRect(0,0,W,H);
  const dark=document.documentElement.getAttribute('data-theme')!=='light';
  const cols=Math.ceil(W/CELL)+1,rows=Math.ceil(H/CELL)+1,MAX=200;
  for(let c=0;c<cols;c++)for(let r=0;r<rows;r++){
    const px=c*CELL,py=r*CELL,dx=gx-px,dy=gy-py,dist=Math.sqrt(dx*dx+dy*dy);
    ctx.beginPath();ctx.arc(px,py,.9,0,Math.PI*2);
    ctx.fillStyle=dark?'rgba(255,255,255,0.03)':'rgba(0,0,0,0.04)';ctx.fill();
    if(dist<MAX){
      const t=1-(dist/MAX),s=t*25,a=t*.65;
      ctx.save();ctx.strokeStyle=dark?`rgba(0,170,255,${a})`:`rgba(0,102,204,${a})`;
      ctx.lineWidth=1;ctx.shadowColor=dark?'rgba(0,170,255,0.5)':'rgba(0,102,204,0.4)';ctx.shadowBlur=s*.4;
      ctx.beginPath();ctx.moveTo(px,py+s);ctx.lineTo(px,py);ctx.lineTo(px+s,py);ctx.stroke();ctx.restore();
    }
  }
  requestAnimationFrame(drawGrid);
}
drawGrid();

/* FADE IN */
const obs=new IntersectionObserver(es=>es.forEach((e,i)=>{if(e.isIntersecting)setTimeout(()=>e.target.classList.add('vis'),i*65)}),{threshold:.08});
document.querySelectorAll('.fi').forEach(el=>obs.observe(el));

/* SKILL BARS */
const sobs=new IntersectionObserver(es=>es.forEach(e=>{if(e.isIntersecting){e.target.querySelectorAll('.sfill').forEach(f=>f.style.width=f.dataset.w+'%');sobs.unobserve(e.target)}}) ,{threshold:.25});
document.querySelectorAll('.sgrid').forEach(el=>sobs.observe(el));

/* FAQ */
function toggleFaq(el){
  const isOpen=el.classList.contains('open');
  document.querySelectorAll('.faq-item').forEach(i=>{i.classList.remove('open');i.querySelector('.faq-a').classList.remove('visible')});
  if(!isOpen){el.classList.add('open');el.querySelector('.faq-a').classList.add('visible');}
}

/* COOKIE */
function acceptCookie(){localStorage.setItem('cookie_ok','1');document.getElementById('cookie').remove()}
if(!localStorage.getItem('cookie_ok')){setTimeout(()=>document.getElementById('cookie').classList.add('show'),1500)}
</script>
</body>
</html>
