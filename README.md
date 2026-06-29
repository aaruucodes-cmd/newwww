<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Singh Electronics – Experience The Future</title>
<meta name="description" content="Singh Electronics – Premium gadgets from Apple, Samsung, Sony & more. Best prices, genuine products, official warranty."/>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
<style>
/* =========================================
   ROOT & RESET
========================================= */
:root {
  --black: #0A0A0A;
  --deep: #0D1117;
  --blue: #00BFFF;
  --blue-dim: rgba(0,191,255,0.15);
  --blue-mid: rgba(0,191,255,0.4);
  --silver: #C0C0C0;
  --white: #FFFFFF;
  --glass: rgba(255,255,255,0.04);
  --glass-border: rgba(255,255,255,0.08);
  --card-bg: rgba(13,17,23,0.8);
  --font-display: 'Space Grotesk', sans-serif;
  --font-body: 'Inter', sans-serif;
  --transition: 0.4s cubic-bezier(0.23,1,0.32,1);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
html{scroll-behavior:smooth;}
body{
  background:var(--black);
  color:var(--white);
  font-family:var(--font-body);
  overflow-x:hidden;
  cursor:none;
}
a{text-decoration:none;color:inherit;}
img{display:block;max-width:100%;}
ul{list-style:none;}
button{cursor:none;border:none;background:none;font-family:inherit;}

/* =========================================
   CUSTOM CURSOR
========================================= */
#cursor{
  position:fixed;width:12px;height:12px;
  background:var(--blue);border-radius:50%;
  pointer-events:none;z-index:9999;
  transform:translate(-50%,-50%);
  transition:width 0.2s,height 0.2s,background 0.2s;
  mix-blend-mode:screen;
}
#cursor-ring{
  position:fixed;width:36px;height:36px;
  border:1px solid var(--blue-mid);border-radius:50%;
  pointer-events:none;z-index:9998;
  transform:translate(-50%,-50%);
  transition:transform 0.12s ease,width 0.3s,height 0.3s,border-color 0.3s;
}
body:has(a:hover) #cursor,body:has(button:hover) #cursor{width:20px;height:20px;}
body:has(a:hover) #cursor-ring,body:has(button:hover) #cursor-ring{
  width:56px;height:56px;border-color:var(--blue);
}

/* =========================================
   PRELOADER
========================================= */
#preloader{
  position:fixed;inset:0;
  background:var(--black);
  z-index:10000;
  display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  gap:32px;
}
.preloader-logo{
  font-family:var(--font-display);
  font-size:2rem;font-weight:700;
  letter-spacing:0.2em;
  background:linear-gradient(135deg,var(--white),var(--blue),var(--silver));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  opacity:0;
}
.preloader-bar-wrap{
  width:260px;height:2px;
  background:rgba(255,255,255,0.08);
  border-radius:2px;overflow:hidden;
}
.preloader-bar{
  height:100%;width:0%;
  background:linear-gradient(90deg,var(--blue),var(--silver));
  border-radius:2px;
  box-shadow:0 0 16px var(--blue);
  transition:width 0.05s linear;
}
.preloader-text{
  font-size:0.75rem;letter-spacing:0.3em;
  color:var(--silver);opacity:0.5;
  font-family:var(--font-display);
}

/* =========================================
   NAVBAR
========================================= */
nav{
  position:fixed;top:0;left:0;right:0;
  z-index:1000;
  padding:20px 5%;
  display:flex;align-items:center;justify-content:space-between;
  transition:background var(--transition),padding var(--transition),backdrop-filter var(--transition);
}
nav.scrolled{
  background:rgba(10,10,10,0.92);
  backdrop-filter:blur(20px);
  -webkit-backdrop-filter:blur(20px);
  padding:14px 5%;
  border-bottom:1px solid var(--glass-border);
}
.nav-logo{
  font-family:var(--font-display);
  font-size:1.3rem;font-weight:700;
  letter-spacing:0.05em;
  display:flex;align-items:center;gap:10px;
}
.nav-logo-icon{
  width:36px;height:36px;
  background:linear-gradient(135deg,var(--blue),#0070ff);
  border-radius:8px;
  display:flex;align-items:center;justify-content:center;
  font-size:1rem;font-weight:700;
  box-shadow:0 0 20px var(--blue-mid);
}
.nav-links{
  display:flex;gap:36px;align-items:center;
}
.nav-links a{
  font-size:0.85rem;font-weight:500;
  letter-spacing:0.08em;color:var(--silver);
  position:relative;transition:color var(--transition);
}
.nav-links a::after{
  content:'';position:absolute;bottom:-4px;left:0;
  width:0;height:1px;background:var(--blue);
  transition:width var(--transition);
  box-shadow:0 0 8px var(--blue);
}
.nav-links a:hover{color:var(--white);}
.nav-links a:hover::after{width:100%;}
.nav-cta{
  padding:10px 22px;
  background:linear-gradient(135deg,var(--blue),#0070ff);
  border-radius:100px;
  font-size:0.82rem;font-weight:600;letter-spacing:0.06em;
  color:var(--white)!important;
  box-shadow:0 0 20px var(--blue-mid);
  transition:box-shadow var(--transition),transform var(--transition)!important;
}
.nav-cta:hover{
  box-shadow:0 0 40px var(--blue)!important;
  transform:translateY(-1px)!important;
}
.nav-cta::after{display:none!important;}
.hamburger{
  display:none;flex-direction:column;gap:5px;
  width:28px;cursor:none;
}
.hamburger span{
  height:1.5px;background:var(--white);border-radius:2px;
  transition:var(--transition);
}
.mobile-menu{
  display:none;
  position:fixed;inset:0;
  background:rgba(10,10,10,0.97);
  backdrop-filter:blur(30px);
  z-index:999;
  flex-direction:column;align-items:center;justify-content:center;
  gap:40px;
}
.mobile-menu.open{display:flex;}
.mobile-menu a{
  font-family:var(--font-display);
  font-size:2rem;font-weight:600;
  letter-spacing:0.05em;color:var(--silver);
  transition:color 0.3s;
}
.mobile-menu a:hover{color:var(--blue);}
.mobile-close{
  position:absolute;top:24px;right:5%;
  font-size:2rem;color:var(--silver);
  cursor:none;background:none;border:none;
  font-family:var(--font-display);
}

/* =========================================
   HERO
========================================= */
#hero{
  position:relative;height:100vh;min-height:700px;
  display:flex;align-items:center;
  overflow:hidden;
}
#hero-canvas{
  position:absolute;inset:0;
  width:100%;height:100%;
  z-index:0;
}
.hero-bg-glow{
  position:absolute;
  width:800px;height:800px;
  background:radial-gradient(ellipse,rgba(0,191,255,0.08) 0%,transparent 70%);
  border-radius:50%;
  top:50%;left:50%;transform:translate(-50%,-50%);
  pointer-events:none;z-index:1;
}
.hero-content{
  position:relative;z-index:2;
  padding:0 5%;
  max-width:750px;
}
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:10px;
  padding:8px 16px;
  background:var(--glass);
  border:1px solid var(--glass-border);
  border-radius:100px;
  font-size:0.72rem;font-weight:500;letter-spacing:0.2em;
  color:var(--blue);
  margin-bottom:28px;
  backdrop-filter:blur(10px);
}
.hero-eyebrow-dot{
  width:6px;height:6px;border-radius:50%;
  background:var(--blue);
  box-shadow:0 0 10px var(--blue);
  animation:pulse 2s ease-in-out infinite;
}
@keyframes pulse{0%,100%{opacity:1;}50%{opacity:0.3;}}
.hero-title{
  font-family:var(--font-display);
  font-size:clamp(2.5rem,5.5vw,4.5rem);
  font-weight:700;
  line-height:1.08;
  letter-spacing:-0.02em;
  margin-bottom:24px;
}
.hero-title .accent{
  background:linear-gradient(135deg,var(--blue),#60cfff,var(--silver));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.hero-sub{
  font-size:1.05rem;font-weight:300;
  color:rgba(255,255,255,0.55);
  line-height:1.7;
  max-width:500px;
  margin-bottom:44px;
}
.hero-actions{
  display:flex;gap:16px;flex-wrap:wrap;
}
.btn-primary{
  padding:15px 36px;
  background:linear-gradient(135deg,var(--blue),#0070ff);
  border-radius:100px;
  font-family:var(--font-display);
  font-size:0.9rem;font-weight:600;
  letter-spacing:0.06em;color:var(--white);
  box-shadow:0 0 30px var(--blue-mid),0 4px 24px rgba(0,112,255,0.3);
  transition:box-shadow var(--transition),transform var(--transition);
  position:relative;overflow:hidden;
}
.btn-primary::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(255,255,255,0.15),transparent);
  opacity:0;transition:opacity 0.3s;
}
.btn-primary:hover::before{opacity:1;}
.btn-primary:hover{
  box-shadow:0 0 60px var(--blue),0 8px 40px rgba(0,112,255,0.5);
  transform:translateY(-2px);
}
.btn-ghost{
  padding:14px 36px;
  background:transparent;
  border:1px solid var(--glass-border);
  border-radius:100px;
  font-family:var(--font-display);
  font-size:0.9rem;font-weight:500;
  letter-spacing:0.06em;color:var(--silver);
  backdrop-filter:blur(10px);
  transition:border-color var(--transition),color var(--transition),background var(--transition);
}
.btn-ghost:hover{
  border-color:var(--blue-mid);
  color:var(--white);
  background:var(--blue-dim);
}
.hero-scroll-hint{
  position:absolute;bottom:40px;left:50%;transform:translateX(-50%);
  z-index:2;display:flex;flex-direction:column;align-items:center;gap:10px;
}
.scroll-line{
  width:1px;height:60px;
  background:linear-gradient(180deg,transparent,var(--blue),transparent);
  animation:scrollLine 2s ease-in-out infinite;
}
@keyframes scrollLine{0%{opacity:0;transform:scaleY(0);transform-origin:top;}
50%{opacity:1;transform:scaleY(1);}100%{opacity:0;transform:scaleY(0);transform-origin:bottom;}}
.scroll-text{
  font-size:0.65rem;letter-spacing:0.2em;
  color:rgba(255,255,255,0.3);font-weight:500;
}

/* =========================================
   SECTIONS COMMON
========================================= */
section{padding:100px 5%;}
.section-label{
  display:inline-flex;align-items:center;gap:10px;
  margin-bottom:16px;
  font-size:0.7rem;font-weight:600;letter-spacing:0.3em;
  color:var(--blue);text-transform:uppercase;
}
.section-label::before{
  content:'';width:30px;height:1px;
  background:var(--blue);
  box-shadow:0 0 8px var(--blue);
}
.section-title{
  font-family:var(--font-display);
  font-size:clamp(1.8rem,3.5vw,3rem);
  font-weight:700;letter-spacing:-0.02em;
  line-height:1.1;
  margin-bottom:60px;
}
.section-title span{
  background:linear-gradient(135deg,var(--blue),var(--silver));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}

/* =========================================
   CATEGORIES
========================================= */
#categories{background:var(--deep);}
.categories-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
  gap:20px;
}
.cat-card{
  position:relative;
  padding:36px 28px;
  background:var(--glass);
  border:1px solid var(--glass-border);
  border-radius:20px;
  overflow:hidden;
  cursor:none;
  transition:transform var(--transition),box-shadow var(--transition),border-color var(--transition);
  backdrop-filter:blur(10px);
}
.cat-card::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(ellipse at top left,rgba(0,191,255,0.1),transparent 70%);
  opacity:0;transition:opacity var(--transition);
}
.cat-card:hover{
  transform:translateY(-8px) scale(1.01);
  box-shadow:0 20px 60px rgba(0,0,0,0.5),0 0 30px var(--blue-dim);
  border-color:var(--blue-mid);
}
.cat-card:hover::before{opacity:1;}
.cat-icon{
  font-size:2.8rem;margin-bottom:20px;
  display:block;
  transition:transform var(--transition);
}
.cat-card:hover .cat-icon{transform:scale(1.15) rotate(-5deg);}
.cat-name{
  font-family:var(--font-display);
  font-size:1.1rem;font-weight:600;
  margin-bottom:8px;
}
.cat-count{
  font-size:0.78rem;color:rgba(255,255,255,0.4);
  letter-spacing:0.05em;
}
.cat-arrow{
  position:absolute;right:24px;top:50%;transform:translateY(-50%);
  font-size:1.5rem;color:var(--blue);opacity:0;
  transition:opacity var(--transition),transform var(--transition);
}
.cat-card:hover .cat-arrow{opacity:1;transform:translateY(-50%) translateX(4px);}

/* =========================================
   PRODUCTS
========================================= */
#products{background:var(--black);}
.products-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(280px,1fr));
  gap:24px;
}
.product-card{
  background:var(--card-bg);
  border:1px solid var(--glass-border);
  border-radius:20px;overflow:hidden;
  cursor:none;
  transition:transform var(--transition),box-shadow var(--transition),border-color var(--transition);
  position:relative;
}
.product-card::after{
  content:'';position:absolute;inset:0;border-radius:20px;
  background:linear-gradient(135deg,rgba(0,191,255,0.05),transparent);
  opacity:0;transition:opacity var(--transition);pointer-events:none;
}
.product-card:hover{
  transform:translateY(-10px) rotateX(2deg);
  box-shadow:0 30px 80px rgba(0,0,0,0.6),0 0 40px var(--blue-dim);
  border-color:rgba(0,191,255,0.25);
}
.product-card:hover::after{opacity:1;}
.product-image-wrap{
  position:relative;
  background:linear-gradient(135deg,#0D1117,#111820);
  padding:36px 24px;
  overflow:hidden;
  min-height:200px;display:flex;align-items:center;justify-content:center;
}
.product-image-wrap::before{
  content:'';position:absolute;
  width:150px;height:150px;border-radius:50%;
  background:radial-gradient(ellipse,var(--blue-dim),transparent);
  top:50%;left:50%;transform:translate(-50%,-50%);
  animation:productGlow 3s ease-in-out infinite alternate;
}
@keyframes productGlow{from{opacity:0.5;transform:translate(-50%,-50%) scale(0.8);}to{opacity:1;transform:translate(-50%,-50%) scale(1.2);}}
.product-emoji{
  font-size:4rem;
  position:relative;z-index:1;
  filter:drop-shadow(0 0 20px var(--blue-mid));
  transition:transform var(--transition);
  animation:float 4s ease-in-out infinite;
}
.product-card:hover .product-emoji{
  transform:scale(1.1) translateY(-6px);
  animation-play-state:paused;
}
@keyframes float{0%,100%{transform:translateY(0);}50%{transform:translateY(-8px);}}
.product-badge{
  position:absolute;top:16px;left:16px;
  padding:4px 12px;border-radius:100px;
  font-size:0.65rem;font-weight:700;letter-spacing:0.1em;
  text-transform:uppercase;
}
.badge-new{background:linear-gradient(135deg,#00ff88,#00cc66);color:#000;}
.badge-hot{background:linear-gradient(135deg,#ff4444,#ff0000);color:#fff;}
.badge-sale{background:linear-gradient(135deg,var(--blue),#0070ff);color:#fff;}
.product-info{padding:24px;}
.product-brand{
  font-size:0.7rem;font-weight:600;letter-spacing:0.15em;
  color:var(--blue);text-transform:uppercase;margin-bottom:6px;
}
.product-name{
  font-family:var(--font-display);
  font-size:1rem;font-weight:600;
  margin-bottom:12px;line-height:1.4;
}
.product-rating{
  display:flex;align-items:center;gap:6px;margin-bottom:16px;
}
.stars{color:#FFD700;font-size:0.75rem;letter-spacing:1px;}
.rating-count{font-size:0.72rem;color:rgba(255,255,255,0.35);}
.product-price{
  display:flex;align-items:baseline;gap:10px;margin-bottom:20px;
}
.price-current{
  font-family:var(--font-display);
  font-size:1.4rem;font-weight:700;color:var(--white);
}
.price-old{
  font-size:0.85rem;color:rgba(255,255,255,0.3);
  text-decoration:line-through;
}
.price-save{
  font-size:0.7rem;color:#00ff88;
  font-weight:600;
}
.product-actions{display:flex;gap:10px;}
.btn-cart{
  flex:1;padding:11px;
  background:var(--glass);
  border:1px solid var(--glass-border);
  border-radius:10px;
  font-size:0.78rem;font-weight:600;letter-spacing:0.06em;
  color:var(--silver);
  transition:background var(--transition),border-color var(--transition),color var(--transition);
}
.btn-cart:hover{
  background:rgba(0,191,255,0.1);
  border-color:var(--blue-mid);color:var(--blue);
}
.btn-buy{
  flex:1.2;padding:11px;
  background:linear-gradient(135deg,var(--blue),#0070ff);
  border-radius:10px;
  font-size:0.78rem;font-weight:600;letter-spacing:0.06em;
  color:var(--white);
  box-shadow:0 0 20px var(--blue-dim);
  transition:box-shadow var(--transition),transform var(--transition);
}
.btn-buy:hover{
  box-shadow:0 0 40px var(--blue-mid);
  transform:translateY(-1px);
}

/* =========================================
   BRANDS
========================================= */
#brands{
  background:var(--deep);
  overflow:hidden;
}
.brands-track-wrap{
  overflow:hidden;
  -webkit-mask:linear-gradient(90deg,transparent,black 10%,black 90%,transparent);
  mask:linear-gradient(90deg,transparent,black 10%,black 90%,transparent);
}
.brands-track{
  display:flex;gap:60px;align-items:center;
  animation:brandsScroll 20s linear infinite;
  width:max-content;
}
.brands-track:hover{animation-play-state:paused;}
@keyframes brandsScroll{from{transform:translateX(0);}to{transform:translateX(-50%)}}
.brand-item{
  display:flex;flex-direction:column;align-items:center;gap:10px;
  cursor:none;
  filter:grayscale(1) opacity(0.35);
  transition:filter var(--transition),transform var(--transition);
  white-space:nowrap;
  min-width:100px;
}
.brand-item:hover{
  filter:grayscale(0) opacity(1);
  transform:scale(1.1);
}
.brand-logo-icon{
  width:54px;height:54px;border-radius:14px;
  display:flex;align-items:center;justify-content:center;
  font-size:1.8rem;
  background:var(--glass);border:1px solid var(--glass-border);
  transition:box-shadow var(--transition),border-color var(--transition);
}
.brand-item:hover .brand-logo-icon{
  box-shadow:0 0 30px var(--blue-dim);
  border-color:var(--blue-mid);
}
.brand-name{
  font-size:0.72rem;font-weight:600;
  letter-spacing:0.12em;color:var(--silver);
}

/* =========================================
   WHY US
========================================= */
#why{background:var(--black);}
.why-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:24px;
}
.why-card{
  padding:36px 28px;
  background:var(--glass);
  border:1px solid var(--glass-border);
  border-radius:20px;
  text-align:center;
  transition:transform var(--transition),box-shadow var(--transition),border-color var(--transition);
  cursor:none;
}
.why-card:hover{
  transform:translateY(-8px);
  box-shadow:0 20px 60px rgba(0,0,0,0.4),0 0 30px var(--blue-dim);
  border-color:var(--blue-mid);
}
.why-icon{
  width:64px;height:64px;border-radius:18px;
  background:linear-gradient(135deg,var(--blue-dim),rgba(0,112,255,0.1));
  border:1px solid var(--blue-mid);
  display:flex;align-items:center;justify-content:center;
  font-size:1.6rem;margin:0 auto 20px;
  box-shadow:0 0 20px var(--blue-dim);
  transition:transform var(--transition),box-shadow var(--transition);
}
.why-card:hover .why-icon{
  transform:scale(1.1);
  box-shadow:0 0 40px var(--blue-mid);
}
.why-title{
  font-family:var(--font-display);
  font-size:0.95rem;font-weight:600;
  margin-bottom:10px;
}
.why-desc{font-size:0.78rem;color:rgba(255,255,255,0.4);line-height:1.7;}

/* =========================================
   OFFERS
========================================= */
#offers{
  background:var(--deep);
}
.offers-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(320px,1fr));
  gap:24px;
}
.offer-card{
  border-radius:20px;overflow:hidden;
  border:1px solid var(--glass-border);
  position:relative;cursor:none;
  transition:transform var(--transition),box-shadow var(--transition);
}
.offer-card:hover{
  transform:translateY(-6px);
  box-shadow:0 20px 60px rgba(0,0,0,0.5);
}
.offer-inner{
  padding:40px 32px;
  background:linear-gradient(135deg,#0D1117,#111820);
  position:relative;overflow:hidden;
}
.offer-glow{
  position:absolute;width:200px;height:200px;border-radius:50%;
  top:-40px;right:-40px;
  background:radial-gradient(ellipse,rgba(0,191,255,0.15),transparent);
  animation:pulseGlow 3s ease-in-out infinite alternate;
}
@keyframes pulseGlow{from{transform:scale(1);opacity:0.7;}to{transform:scale(1.3);opacity:1;}}
.offer-card.gold .offer-glow{background:radial-gradient(ellipse,rgba(255,200,0,0.15),transparent);}
.offer-card.red .offer-glow{background:radial-gradient(ellipse,rgba(255,50,50,0.15),transparent);}
.offer-tag{
  display:inline-block;
  padding:4px 12px;border-radius:100px;
  font-size:0.65rem;font-weight:700;letter-spacing:0.15em;
  text-transform:uppercase;margin-bottom:20px;
  background:var(--blue-dim);color:var(--blue);
  border:1px solid var(--blue-mid);
}
.offer-card.gold .offer-tag{background:rgba(255,200,0,0.1);color:#FFD700;border-color:rgba(255,200,0,0.3);}
.offer-card.red .offer-tag{background:rgba(255,50,50,0.1);color:#ff4444;border-color:rgba(255,50,50,0.3);}
.offer-title{
  font-family:var(--font-display);
  font-size:1.5rem;font-weight:700;
  margin-bottom:8px;
}
.offer-desc{font-size:0.83rem;color:rgba(255,255,255,0.45);margin-bottom:24px;}
.countdown{display:flex;gap:16px;margin-bottom:28px;}
.countdown-block{text-align:center;}
.countdown-num{
  font-family:var(--font-display);
  font-size:1.8rem;font-weight:700;
  display:block;
  background:linear-gradient(135deg,var(--white),var(--silver));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
}
.countdown-label{font-size:0.6rem;color:rgba(255,255,255,0.3);letter-spacing:0.15em;display:block;}
.countdown-sep{
  font-size:1.5rem;color:var(--blue);
  align-self:flex-start;padding-top:4px;
}
.offer-border-animated{
  position:absolute;inset:0;border-radius:20px;
  background:linear-gradient(var(--angle,0deg),var(--blue),transparent,var(--blue));
  -webkit-mask:linear-gradient(#fff 0 0) content-box,linear-gradient(#fff 0 0);
  -webkit-mask-composite:xor;mask-composite:exclude;
  padding:1px;
  animation:rotateBorder 4s linear infinite;
  opacity:0.4;
}
@keyframes rotateBorder{to{--angle:360deg;}}

/* =========================================
   REVIEWS
========================================= */
#reviews{background:var(--black);}
.reviews-carousel{
  overflow:hidden;
  -webkit-mask:linear-gradient(90deg,transparent,black 8%,black 92%,transparent);
  mask:linear-gradient(90deg,transparent,black 8%,black 92%,transparent);
}
.reviews-track{
  display:flex;gap:24px;
  animation:reviewsScroll 30s linear infinite;
  width:max-content;
}
.reviews-track:hover{animation-play-state:paused;}
@keyframes reviewsScroll{from{transform:translateX(0);}to{transform:translateX(-50%)}}
.review-card{
  width:340px;
  padding:32px;
  background:var(--glass);
  border:1px solid var(--glass-border);
  border-radius:20px;
  backdrop-filter:blur(10px);
  flex-shrink:0;
  transition:border-color var(--transition),transform var(--transition);
}
.review-card:hover{
  border-color:var(--blue-mid);
  transform:translateY(-4px);
}
.review-stars{color:#FFD700;font-size:1rem;letter-spacing:2px;margin-bottom:16px;}
.review-text{
  font-size:0.85rem;line-height:1.7;
  color:rgba(255,255,255,0.65);margin-bottom:20px;
  font-style:italic;
}
.review-author{display:flex;align-items:center;gap:14px;}
.review-avatar{
  width:42px;height:42px;border-radius:50%;
  background:linear-gradient(135deg,var(--blue),#0070ff);
  display:flex;align-items:center;justify-content:center;
  font-weight:700;font-family:var(--font-display);
  box-shadow:0 0 16px var(--blue-dim);
  flex-shrink:0;
}
.review-name{
  font-weight:600;font-size:0.85rem;
  font-family:var(--font-display);
}
.review-meta{font-size:0.7rem;color:rgba(255,255,255,0.35);margin-top:2px;}

/* =========================================
   CONTACT
========================================= */
#contact{
  background:var(--deep);
}
.contact-grid{
  display:grid;grid-template-columns:1fr 1fr;gap:60px;
  align-items:start;
}
.contact-info{display:flex;flex-direction:column;gap:28px;}
.contact-info-title{
  font-family:var(--font-display);
  font-size:clamp(1.5rem,2.5vw,2.2rem);
  font-weight:700;letter-spacing:-0.02em;
  line-height:1.2;margin-bottom:4px;
}
.contact-detail{
  display:flex;align-items:flex-start;gap:16px;
  padding:20px;background:var(--glass);
  border:1px solid var(--glass-border);border-radius:14px;
  transition:border-color var(--transition);cursor:none;
}
.contact-detail:hover{border-color:var(--blue-mid);}
.contact-detail-icon{
  width:42px;height:42px;border-radius:10px;
  background:var(--blue-dim);border:1px solid var(--blue-mid);
  display:flex;align-items:center;justify-content:center;
  font-size:1.1rem;flex-shrink:0;
}
.contact-detail-label{font-size:0.7rem;color:rgba(255,255,255,0.35);margin-bottom:4px;letter-spacing:0.1em;}
.contact-detail-value{font-size:0.9rem;font-weight:500;}
.whatsapp-btn{
  display:inline-flex;align-items:center;gap:10px;
  padding:14px 28px;
  background:linear-gradient(135deg,#25D366,#128C7E);
  border-radius:100px;
  font-size:0.85rem;font-weight:600;color:var(--white);
  box-shadow:0 0 24px rgba(37,211,102,0.3);
  transition:box-shadow var(--transition),transform var(--transition);
  width:fit-content;
}
.whatsapp-btn:hover{
  box-shadow:0 0 40px rgba(37,211,102,0.5);
  transform:translateY(-2px);
}
.map-placeholder{
  border-radius:16px;overflow:hidden;
  border:1px solid var(--glass-border);
  background:linear-gradient(135deg,#0D1117,#111820);
  height:200px;
  display:flex;align-items:center;justify-content:center;
  flex-direction:column;gap:10px;
  color:rgba(255,255,255,0.2);font-size:0.8rem;
}
.contact-form{display:flex;flex-direction:column;gap:16px;}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:16px;}
.form-field{
  display:flex;flex-direction:column;gap:8px;
}
.form-field label{font-size:0.75rem;font-weight:500;color:rgba(255,255,255,0.4);letter-spacing:0.08em;}
.form-field input,.form-field textarea,.form-field select{
  background:var(--glass);
  border:1px solid var(--glass-border);
  border-radius:10px;
  padding:13px 16px;
  color:var(--white);
  font-family:var(--font-body);
  font-size:0.85rem;
  transition:border-color var(--transition),box-shadow var(--transition);
  outline:none;
  width:100%;
}
.form-field input:focus,.form-field textarea:focus,.form-field select:focus{
  border-color:var(--blue-mid);
  box-shadow:0 0 0 3px var(--blue-dim);
}
.form-field textarea{resize:vertical;min-height:120px;}
.form-field select option{background:#0D1117;color:var(--white);}

/* =========================================
   FOOTER
========================================= */
footer{
  background:#050505;
  border-top:1px solid var(--glass-border);
  padding:60px 5% 30px;
}
.footer-top{
  display:grid;
  grid-template-columns:2fr 1fr 1fr 1fr;
  gap:48px;margin-bottom:48px;
}
.footer-brand .nav-logo{margin-bottom:16px;}
.footer-tagline{font-size:0.82rem;color:rgba(255,255,255,0.35);line-height:1.7;max-width:280px;margin-bottom:24px;}
.newsletter{display:flex;gap:0;border:1px solid var(--glass-border);border-radius:10px;overflow:hidden;}
.newsletter input{
  flex:1;background:transparent;
  border:none;padding:12px 16px;
  color:var(--white);font-family:var(--font-body);font-size:0.8rem;outline:none;
}
.newsletter input::placeholder{color:rgba(255,255,255,0.25);}
.newsletter-btn{
  padding:12px 18px;
  background:linear-gradient(135deg,var(--blue),#0070ff);
  color:var(--white);font-size:0.75rem;font-weight:600;
  letter-spacing:0.08em;white-space:nowrap;
  transition:opacity 0.3s;
}
.newsletter-btn:hover{opacity:0.85;}
.footer-col h4{
  font-family:var(--font-display);
  font-size:0.85rem;font-weight:600;
  letter-spacing:0.05em;margin-bottom:20px;
  color:var(--white);
}
.footer-col ul{display:flex;flex-direction:column;gap:12px;}
.footer-col ul a{
  font-size:0.78rem;color:rgba(255,255,255,0.35);
  transition:color var(--transition);
}
.footer-col ul a:hover{color:var(--blue);}
.footer-bottom{
  display:flex;align-items:center;justify-content:space-between;
  padding-top:28px;border-top:1px solid var(--glass-border);
  flex-wrap:wrap;gap:16px;
}
.footer-copy{font-size:0.75rem;color:rgba(255,255,255,0.25);}
.social-icons{display:flex;gap:12px;}
.social-icon{
  width:38px;height:38px;border-radius:10px;
  background:var(--glass);border:1px solid var(--glass-border);
  display:flex;align-items:center;justify-content:center;
  font-size:1rem;color:var(--silver);
  transition:border-color var(--transition),color var(--transition),box-shadow var(--transition);
  cursor:none;
}
.social-icon:hover{
  border-color:var(--blue-mid);color:var(--blue);
  box-shadow:0 0 20px var(--blue-dim);
}

/* =========================================
   PARTICLES OVERLAY
========================================= */
#particles-canvas{
  position:fixed;inset:0;pointer-events:none;z-index:1;
  opacity:0.4;
}

/* =========================================
   REVEAL ANIMATIONS
========================================= */
.reveal{
  opacity:0;transform:translateY(30px);
  transition:opacity 0.8s cubic-bezier(0.23,1,0.32,1),transform 0.8s cubic-bezier(0.23,1,0.32,1);
}
.reveal.visible{opacity:1;transform:translateY(0);}
.reveal-delay-1{transition-delay:0.1s;}
.reveal-delay-2{transition-delay:0.2s;}
.reveal-delay-3{transition-delay:0.3s;}
.reveal-delay-4{transition-delay:0.4s;}
.reveal-delay-5{transition-delay:0.5s;}

/* =========================================
   RESPONSIVE
========================================= */
@media(max-width:900px){
  .nav-links{display:none;}
  .hamburger{display:flex;}
  .contact-grid{grid-template-columns:1fr;}
  .footer-top{grid-template-columns:1fr 1fr;}
  .form-row{grid-template-columns:1fr;}
}
@media(max-width:600px){
  section{padding:70px 5%;}
  .footer-top{grid-template-columns:1fr;}
  .hero-actions{flex-direction:column;}
  .btn-primary,.btn-ghost{text-align:center;}
}

/* =========================================
   SPOTLIGHT / GLOW CURSOR EFFECT
========================================= */
.spotlight{
  position:fixed;
  width:500px;height:500px;
  border-radius:50%;
  background:radial-gradient(ellipse,rgba(0,191,255,0.04) 0%,transparent 70%);
  pointer-events:none;z-index:0;
  transform:translate(-50%,-50%);
  transition:transform 0.05s;
}
</style>
</head>
<body>

<!-- Cursor -->
<div id="cursor"></div>
<div id="cursor-ring"></div>
<div class="spotlight" id="spotlight"></div>

<!-- Preloader -->
<div id="preloader">
  <div class="preloader-logo">SINGH ELECTRONICS</div>
  <div class="preloader-bar-wrap">
    <div class="preloader-bar" id="preloader-bar"></div>
  </div>
  <div class="preloader-text">LOADING EXPERIENCE</div>
</div>

<!-- Particles Background -->
<canvas id="particles-canvas"></canvas>

<!-- NAVBAR -->
<nav id="navbar">
  <a href="#" class="nav-logo">
    <div class="nav-logo-icon">S</div>
    Singh Electronics
  </a>
  <ul class="nav-links">
    <li><a href="#hero">Home</a></li>
    <li><a href="#products">Products</a></li>
    <li><a href="#brands">Brands</a></li>
    <li><a href="#offers">Offers</a></li>
    <li><a href="#reviews">Reviews</a></li>
    <li><a href="#contact" class="nav-cta">Contact Us</a></li>
  </ul>
  <div class="hamburger" id="hamburger">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- Mobile Menu -->
<div class="mobile-menu" id="mobileMenu">
  <button class="mobile-close" id="mobileClose">✕</button>
  <a href="#hero" onclick="closeMobile()">Home</a>
  <a href="#products" onclick="closeMobile()">Products</a>
  <a href="#brands" onclick="closeMobile()">Brands</a>
  <a href="#offers" onclick="closeMobile()">Offers</a>
  <a href="#reviews" onclick="closeMobile()">Reviews</a>
  <a href="#contact" onclick="closeMobile()">Contact</a>
</div>

<!-- HERO -->
<section id="hero">
  <canvas id="hero-canvas"></canvas>
  <div class="hero-bg-glow"></div>
  <div class="hero-content">
    <div class="hero-eyebrow">
      <div class="hero-eyebrow-dot"></div>
      New Arrivals 2025 — Just Landed
    </div>
    <h1 class="hero-title">
      Experience The<br>
      <span class="accent">Future of</span><br>
      Electronics
    </h1>
    <p class="hero-sub">
      World-class gadgets. Official warranty. Unbeatable prices.
      Step into tomorrow's technology, today.
    </p>
    <div class="hero-actions">
      <a href="#products" class="btn-primary">Shop Now →</a>
      <a href="#categories" class="btn-ghost">Explore Products</a>
    </div>
  </div>
  <div class="hero-scroll-hint">
    <div class="scroll-line"></div>
    <span class="scroll-text">SCROLL</span>
  </div>
</section>

<!-- CATEGORIES -->
<section id="categories">
  <div class="section-label">Browse By Category</div>
  <h2 class="section-title reveal">Find What You're<br>Looking For <span>Instantly</span></h2>
  <div class="categories-grid">
    <div class="cat-card reveal reveal-delay-1">
      <span class="cat-icon">📱</span>
      <div class="cat-name">Smartphones</div>
      <div class="cat-count">240+ Models</div>
      <div class="cat-arrow">→</div>
    </div>
    <div class="cat-card reveal reveal-delay-2">
      <span class="cat-icon">💻</span>
      <div class="cat-name">Laptops</div>
      <div class="cat-count">180+ Models</div>
      <div class="cat-arrow">→</div>
    </div>
    <div class="cat-card reveal reveal-delay-3">
      <span class="cat-icon">📺</span>
      <div class="cat-name">Smart TVs</div>
      <div class="cat-count">90+ Models</div>
      <div class="cat-arrow">→</div>
    </div>
    <div class="cat-card reveal reveal-delay-4">
      <span class="cat-icon">🏠</span>
      <div class="cat-name">Home Appliances</div>
      <div class="cat-count">350+ Products</div>
      <div class="cat-arrow">→</div>
    </div>
    <div class="cat-card reveal reveal-delay-5">
      <span class="cat-icon">🎧</span>
      <div class="cat-name">Audio</div>
      <div class="cat-count">120+ Products</div>
      <div class="cat-arrow">→</div>
    </div>
    <div class="cat-card reveal reveal-delay-3">
      <span class="cat-icon">🎮</span>
      <div class="cat-name">Gaming</div>
      <div class="cat-count">200+ Products</div>
      <div class="cat-arrow">→</div>
    </div>
  </div>
</section>

<!-- PRODUCTS -->
<section id="products">
  <div class="section-label">Featured Products</div>
  <h2 class="section-title reveal">Bestsellers &amp;<br><span>Top Picks</span></h2>
  <div class="products-grid">

    <div class="product-card reveal reveal-delay-1">
      <div class="product-image-wrap">
        <div class="product-badge badge-new">New</div>
        <div class="product-emoji">📱</div>
      </div>
      <div class="product-info">
        <div class="product-brand">Apple</div>
        <div class="product-name">iPhone 16 Pro Max — 256GB</div>
        <div class="product-rating"><span class="stars">★★★★★</span><span class="rating-count">(2,847)</span></div>
        <div class="product-price">
          <span class="price-current">₹1,34,900</span>
          <span class="price-old">₹1,59,900</span>
          <span class="price-save">Save ₹25K</span>
        </div>
        <div class="product-actions">
          <button class="btn-cart">+ Cart</button>
          <button class="btn-buy">Buy Now</button>
        </div>
      </div>
    </div>

    <div class="product-card reveal reveal-delay-2">
      <div class="product-image-wrap">
        <div class="product-badge badge-hot">Hot</div>
        <div class="product-emoji">💻</div>
      </div>
      <div class="product-info">
        <div class="product-brand">Apple</div>
        <div class="product-name">MacBook Pro M4 — 14"</div>
        <div class="product-rating"><span class="stars">★★★★★</span><span class="rating-count">(1,203)</span></div>
        <div class="product-price">
          <span class="price-current">₹1,99,900</span>
          <span class="price-old">₹2,14,900</span>
          <span class="price-save">Save ₹15K</span>
        </div>
        <div class="product-actions">
          <button class="btn-cart">+ Cart</button>
          <button class="btn-buy">Buy Now</button>
        </div>
      </div>
    </div>

    <div class="product-card reveal reveal-delay-3">
      <div class="product-image-wrap">
        <div class="product-badge badge-sale">Sale</div>
        <div class="product-emoji">🎧</div>
      </div>
      <div class="product-info">
        <div class="product-brand">Sony</div>
        <div class="product-name">WH-1000XM6 Noise Cancelling</div>
        <div class="product-rating"><span class="stars">★★★★★</span><span class="rating-count">(4,521)</span></div>
        <div class="product-price">
          <span class="price-current">₹28,990</span>
          <span class="price-old">₹34,990</span>
          <span class="price-save">17% Off</span>
        </div>
        <div class="product-actions">
          <button class="btn-cart">+ Cart</button>
          <button class="btn-buy">Buy Now</button>
        </div>
      </div>
    </div>

    <div class="product-card reveal reveal-delay-4">
      <div class="product-image-wrap">
        <div class="product-badge badge-new">New</div>
        <div class="product-emoji">📺</div>
      </div>
      <div class="product-info">
        <div class="product-brand">Samsung</div>
        <div class="product-name">Galaxy Neo QLED 8K — 65"</div>
        <div class="product-rating"><span class="stars">★★★★☆</span><span class="rating-count">(876)</span></div>
        <div class="product-price">
          <span class="price-current">₹2,49,990</span>
          <span class="price-old">₹2,99,990</span>
          <span class="price-save">Save ₹50K</span>
        </div>
        <div class="product-actions">
          <button class="btn-cart">+ Cart</button>
          <button class="btn-buy">Buy Now</button>
        </div>
      </div>
    </div>

    <div class="product-card reveal reveal-delay-2">
      <div class="product-image-wrap">
        <div class="product-badge badge-hot">Hot</div>
        <div class="product-emoji">🎮</div>
      </div>
      <div class="product-info">
        <div class="product-brand">Sony</div>
        <div class="product-name">PlayStation 5 Slim — Digital</div>
        <div class="product-rating"><span class="stars">★★★★★</span><span class="rating-count">(9,102)</span></div>
        <div class="product-price">
          <span class="price-current">₹44,990</span>
          <span class="price-old">₹49,990</span>
          <span class="price-save">Save ₹5K</span>
        </div>
        <div class="product-actions">
          <button class="btn-cart">+ Cart</button>
          <button class="btn-buy">Buy Now</button>
        </div>
      </div>
    </div>

    <div class="product-card reveal reveal-delay-3">
      <div class="product-image-wrap">
        <div class="product-badge badge-sale">Sale</div>
        <div class="product-emoji">⌚</div>
      </div>
      <div class="product-info">
        <div class="product-brand">Samsung</div>
        <div class="product-name">Galaxy Watch Ultra — 47mm</div>
        <div class="product-rating"><span class="stars">★★★★☆</span><span class="rating-count">(1,654)</span></div>
        <div class="product-price">
          <span class="price-current">₹59,999</span>
          <span class="price-old">₹74,999</span>
          <span class="price-save">20% Off</span>
        </div>
        <div class="product-actions">
          <button class="btn-cart">+ Cart</button>
          <button class="btn-buy">Buy Now</button>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- BRANDS -->
<section id="brands">
  <div class="section-label">Our Partners</div>
  <h2 class="section-title reveal">Authorised Dealer for<br><span>World's Best Brands</span></h2>
  <div class="brands-track-wrap">
    <div class="brands-track" id="brandsTrack">
      <!-- duplicated for infinite scroll -->
      <div class="brand-item"><div class="brand-logo-icon">🍎</div><div class="brand-name">Apple</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🔷</div><div class="brand-name">Samsung</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🎵</div><div class="brand-name">Sony</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🌀</div><div class="brand-name">LG</div></div>
      <div class="brand-item"><div class="brand-logo-icon">💠</div><div class="brand-name">Dell</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🖥️</div><div class="brand-name">HP</div></div>
      <div class="brand-item"><div class="brand-logo-icon">💻</div><div class="brand-name">Lenovo</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🔮</div><div class="brand-name">ASUS</div></div>
      <div class="brand-item"><div class="brand-logo-icon">📡</div><div class="brand-name">Xiaomi</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🎧</div><div class="brand-name">boAt</div></div>
      <!-- Duplicate -->
      <div class="brand-item"><div class="brand-logo-icon">🍎</div><div class="brand-name">Apple</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🔷</div><div class="brand-name">Samsung</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🎵</div><div class="brand-name">Sony</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🌀</div><div class="brand-name">LG</div></div>
      <div class="brand-item"><div class="brand-logo-icon">💠</div><div class="brand-name">Dell</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🖥️</div><div class="brand-name">HP</div></div>
      <div class="brand-item"><div class="brand-logo-icon">💻</div><div class="brand-name">Lenovo</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🔮</div><div class="brand-name">ASUS</div></div>
      <div class="brand-item"><div class="brand-logo-icon">📡</div><div class="brand-name">Xiaomi</div></div>
      <div class="brand-item"><div class="brand-logo-icon">🎧</div><div class="brand-name">boAt</div></div>
    </div>
  </div>
</section>

<!-- WHY CHOOSE US -->
<section id="why">
  <div class="section-label">Why Singh Electronics</div>
  <h2 class="section-title reveal">6 Reasons Customers<br><span>Trust Us</span></h2>
  <div class="why-grid">
    <div class="why-card reveal reveal-delay-1">
      <div class="why-icon">✅</div>
      <div class="why-title">100% Genuine Products</div>
      <div class="why-desc">Every product is sourced directly from brand-authorised distributors. Zero counterfeits, ever.</div>
    </div>
    <div class="why-card reveal reveal-delay-2">
      <div class="why-icon">💰</div>
      <div class="why-title">Best Price Guaranteed</div>
      <div class="why-desc">Found it cheaper? We'll match it. Our price-beat promise has never failed a customer.</div>
    </div>
    <div class="why-card reveal reveal-delay-3">
      <div class="why-icon">🛡️</div>
      <div class="why-title">Official Warranty</div>
      <div class="why-desc">Full manufacturer warranty on every product. We also provide extended care plans.</div>
    </div>
    <div class="why-card reveal reveal-delay-4">
      <div class="why-icon">⚡</div>
      <div class="why-title">Fast Delivery</div>
      <div class="why-desc">Same-day delivery within city. Pan-India shipping in 2-4 business days.</div>
    </div>
    <div class="why-card reveal reveal-delay-2">
      <div class="why-icon">💳</div>
      <div class="why-title">Easy EMI</div>
      <div class="why-desc">No-cost EMI up to 24 months on all major credit/debit cards and buy-now-pay-later options.</div>
    </div>
    <div class="why-card reveal reveal-delay-3">
      <div class="why-icon">🎓</div>
      <div class="why-title">Expert Support</div>
      <div class="why-desc">Trained tech advisors help you choose, setup, and get the most from your devices.</div>
    </div>
  </div>
</section>

<!-- OFFERS -->
<section id="offers">
  <div class="section-label">Limited Time</div>
  <h2 class="section-title reveal">Deals That Won't<br><span>Wait for You</span></h2>
  <div class="offers-grid">
    <div class="offer-card reveal reveal-delay-1">
      <div class="offer-inner">
        <div class="offer-glow"></div>
        <div class="offer-tag">⚡ Flash Sale</div>
        <div class="offer-title">Smartphones up to 35% Off</div>
        <div class="offer-desc">Limited stock. Top brands. Crazy prices. This weekend only.</div>
        <div class="countdown" id="countdown1">
          <div class="countdown-block"><span class="countdown-num" data-type="hours">08</span><span class="countdown-label">HRS</span></div>
          <div class="countdown-sep">:</div>
          <div class="countdown-block"><span class="countdown-num" data-type="minutes">45</span><span class="countdown-label">MIN</span></div>
          <div class="countdown-sep">:</div>
          <div class="countdown-block"><span class="countdown-num" data-type="seconds">30</span><span class="countdown-label">SEC</span></div>
        </div>
        <a href="#products" class="btn-primary" style="display:inline-block;margin-top:4px;">Grab The Deal →</a>
      </div>
    </div>
    <div class="offer-card gold reveal reveal-delay-2">
      <div class="offer-inner">
        <div class="offer-glow"></div>
        <div class="offer-tag" style="background:rgba(255,200,0,0.1);color:#FFD700;border-color:rgba(255,200,0,0.3);">🏅 Festival Offer</div>
        <div class="offer-title">Exchange &amp; Save ₹20,000</div>
        <div class="offer-desc">Trade in your old device. Get guaranteed best value. No questions asked.</div>
        <div class="countdown" id="countdown2">
          <div class="countdown-block"><span class="countdown-num" data-type="days">04</span><span class="countdown-label">DAYS</span></div>
          <div class="countdown-sep">:</div>
          <div class="countdown-block"><span class="countdown-num" data-type="hours">12</span><span class="countdown-label">HRS</span></div>
          <div class="countdown-sep">:</div>
          <div class="countdown-block"><span class="countdown-num" data-type="minutes">00</span><span class="countdown-label">MIN</span></div>
        </div>
        <a href="#contact" class="btn-primary" style="display:inline-block;margin-top:4px;background:linear-gradient(135deg,#FFD700,#cc9900);box-shadow:0 0 30px rgba(255,200,0,0.3);">Know More →</a>
      </div>
    </div>
    <div class="offer-card red reveal reveal-delay-3">
      <div class="offer-inner">
        <div class="offer-glow"></div>
        <div class="offer-tag" style="background:rgba(255,50,50,0.1);color:#ff4444;border-color:rgba(255,50,50,0.3);">🔥 Clearance Sale</div>
        <div class="offer-title">Last Units — Flat 40% Off</div>
        <div class="offer-desc">Display models, open-box items in mint condition. Certified and tested. Hurry!</div>
        <div style="display:flex;gap:12px;flex-wrap:wrap;margin-top:24px;">
          <span style="padding:6px 14px;background:rgba(255,50,50,0.1);border:1px solid rgba(255,50,50,0.3);border-radius:8px;font-size:0.75rem;color:#ff4444;">Laptops</span>
          <span style="padding:6px 14px;background:rgba(255,50,50,0.1);border:1px solid rgba(255,50,50,0.3);border-radius:8px;font-size:0.75rem;color:#ff4444;">TVs</span>
          <span style="padding:6px 14px;background:rgba(255,50,50,0.1);border:1px solid rgba(255,50,50,0.3);border-radius:8px;font-size:0.75rem;color:#ff4444;">Audio</span>
        </div>
        <a href="#products" class="btn-primary" style="display:inline-block;margin-top:20px;background:linear-gradient(135deg,#ff4444,#cc0000);box-shadow:0 0 30px rgba(255,50,50,0.3);">Shop Clearance →</a>
      </div>
    </div>
  </div>
</section>

<!-- REVIEWS -->
<section id="reviews">
  <div class="section-label">Customer Stories</div>
  <h2 class="section-title reveal">What Our Customers<br><span>Say About Us</span></h2>
  <div class="reviews-carousel">
    <div class="reviews-track" id="reviewsTrack">
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Bought an iPhone 16 Pro here. Price was ₹8,000 cheaper than the official Apple store. Delivery in 4 hours. Cannot ask for more."</div>
        <div class="review-author"><div class="review-avatar">R</div><div><div class="review-name">Ravi Sharma</div><div class="review-meta">Raipur • iPhone 16 Pro</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"The staff actually took time to explain every MacBook model. Felt like talking to an Apple Genius. Bought the M4 Pro and loving it."</div>
        <div class="review-author"><div class="review-avatar">P</div><div><div class="review-name">Priya Verma</div><div class="review-meta">Bilaspur • MacBook Pro M4</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Got my PS5 during the flash sale. The packaging was perfect, product sealed. No-cost EMI on 12 months made it effortless."</div>
        <div class="review-author"><div class="review-avatar">A</div><div><div class="review-name">Arjun Patel</div><div class="review-meta">Durg • PlayStation 5</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Exchange offer gave me ₹18,000 for my old phone. Walked out with a brand new Samsung Galaxy S25 Ultra at half price. Mind-blowing!"</div>
        <div class="review-author"><div class="review-avatar">S</div><div><div class="review-name">Sunita Yadav</div><div class="review-meta">Raipur • Galaxy S25 Ultra</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Sony WH-1000XM6 headphones at a discount I didn't believe was real. Called to confirm, they delivered same-day. Five stars isn't enough."</div>
        <div class="review-author"><div class="review-avatar">M</div><div><div class="review-name">Mohit Gupta</div><div class="review-meta">Bhilai • Sony WH-1000XM6</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"I've been buying from Singh Electronics for 6 years. Never once had an issue. The team knows every product inside out. Truly the best in CG."</div>
        <div class="review-author"><div class="review-avatar">K</div><div><div class="review-name">Kavita Singh</div><div class="review-meta">Raipur • Loyal Customer</div></div></div>
      </div>
      <!-- Duplicate -->
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Bought an iPhone 16 Pro here. Price was ₹8,000 cheaper than the official Apple store. Delivery in 4 hours. Cannot ask for more."</div>
        <div class="review-author"><div class="review-avatar">R</div><div><div class="review-name">Ravi Sharma</div><div class="review-meta">Raipur • iPhone 16 Pro</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"The staff actually took time to explain every MacBook model. Felt like talking to an Apple Genius. Bought the M4 Pro and loving it."</div>
        <div class="review-author"><div class="review-avatar">P</div><div><div class="review-name">Priya Verma</div><div class="review-meta">Bilaspur • MacBook Pro M4</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Got my PS5 during the flash sale. The packaging was perfect, product sealed. No-cost EMI on 12 months made it effortless."</div>
        <div class="review-author"><div class="review-avatar">A</div><div><div class="review-name">Arjun Patel</div><div class="review-meta">Durg • PlayStation 5</div></div></div>
      </div>
      <div class="review-card">
        <div class="review-stars">★★★★★</div>
        <div class="review-text">"Exchange offer gave me ₹18,000 for my old phone. Walked out with a brand new Samsung Galaxy S25 Ultra at half price. Mind-blowing!"</div>
        <div class="review-author"><div class="review-avatar">S</div><div><div class="review-name">Sunita Yadav</div><div class="review-meta">Raipur • Galaxy S25 Ultra</div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-label">Get In Touch</div>
  <h2 class="section-title reveal">We're Here to<br><span>Help You</span></h2>
  <div class="contact-grid">
    <div class="contact-info">
      <div>
        <div class="contact-info-title reveal">Visit Our Showroom</div>
        <p style="color:rgba(255,255,255,0.4);font-size:0.85rem;line-height:1.7;margin-top:8px;" class="reveal reveal-delay-1">
          Chhattisgarh's most trusted electronics destination since 2008.
          Come experience products in person — our team will guide you.
        </p>
      </div>
      <div class="contact-detail reveal reveal-delay-1">
        <div class="contact-detail-icon">📍</div>
        <div>
          <div class="contact-detail-label">Address</div>
          <div class="contact-detail-value">Main Market, GE Road, Raipur, CG — 492001</div>
        </div>
      </div>
      <div class="contact-detail reveal reveal-delay-2">
        <div class="contact-detail-icon">📞</div>
        <div>
          <div class="contact-detail-label">Phone</div>
          <div class="contact-detail-value">+91 98765 43210</div>
        </div>
      </div>
      <div class="contact-detail reveal reveal-delay-3">
        <div class="contact-detail-icon">📧</div>
        <div>
          <div class="contact-detail-label">Email</div>
          <div class="contact-detail-value">hello@singhelectronics.in</div>
        </div>
      </div>
      <a href="https://wa.me/919876543210" class="whatsapp-btn reveal reveal-delay-4">
        <span>💬</span> Chat on WhatsApp
      </a>
      <div class="map-placeholder reveal">
        <span style="font-size:2rem;">🗺️</span>
        <span>Open in Google Maps →</span>
      </div>
    </div>
    <div class="reveal reveal-delay-2">
      <form class="contact-form" onsubmit="handleForm(event)">
        <div class="form-row">
          <div class="form-field">
            <label>Full Name</label>
            <input type="text" placeholder="Rahul Singh" required/>
          </div>
          <div class="form-field">
            <label>Phone Number</label>
            <input type="tel" placeholder="+91 98765 43210"/>
          </div>
        </div>
        <div class="form-field">
          <label>Email Address</label>
          <input type="email" placeholder="rahul@email.com"/>
        </div>
        <div class="form-field">
          <label>I'm Interested In</label>
          <select>
            <option>Smartphones</option>
            <option>Laptops</option>
            <option>Smart TVs</option>
            <option>Audio</option>
            <option>Gaming</option>
            <option>Home Appliances</option>
            <option>Other</option>
          </select>
        </div>
        <div class="form-field">
          <label>Message</label>
          <textarea placeholder="Tell us what you're looking for or any questions you have..."></textarea>
        </div>
        <button type="submit" class="btn-primary" style="width:100%;border-radius:12px;font-size:0.9rem;">
          Send Message →
        </button>
      </form>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <div class="nav-logo" style="font-family:var(--font-display);font-size:1.2rem;font-weight:700;display:flex;align-items:center;gap:10px;margin-bottom:16px;">
        <div class="nav-logo-icon">S</div> Singh Electronics
      </div>
      <p class="footer-tagline">Chhattisgarh's most trusted destination for premium electronics since 2008. Official dealer for 30+ global brands.</p>
      <div class="newsletter">
        <input type="email" placeholder="Get exclusive offers..."/>
        <button class="newsletter-btn">Subscribe</button>
      </div>
    </div>
    <div class="footer-col">
      <h4>Quick Links</h4>
      <ul>
        <li><a href="#hero">Home</a></li>
        <li><a href="#categories">Categories</a></li>
        <li><a href="#products">Products</a></li>
        <li><a href="#brands">Brands</a></li>
        <li><a href="#offers">Offers</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Services</h4>
      <ul>
        <li><a href="#">Exchange</a></li>
        <li><a href="#">EMI Options</a></li>
        <li><a href="#">Warranty Claims</a></li>
        <li><a href="#">Bulk Orders</a></li>
        <li><a href="#">Repair Services</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Support</h4>
      <ul>
        <li><a href="#contact">Contact Us</a></li>
        <li><a href="#">Track Order</a></li>
        <li><a href="#">Return Policy</a></li>
        <li><a href="#">Privacy Policy</a></li>
        <li><a href="#">Terms of Use</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <div class="footer-copy">© 2025 Singh Electronics. All rights reserved. Made with ❤️ in Chhattisgarh.</div>
    <div class="social-icons">
      <a href="#" class="social-icon" title="Instagram">📸</a>
      <a href="#" class="social-icon" title="Facebook">👤</a>
      <a href="#" class="social-icon" title="YouTube">▶️</a>
      <a href="#" class="social-icon" title="Twitter">🐦</a>
    </div>
  </div>
</footer>

<!-- =========================================
   SCRIPTS
========================================= -->
<script>
/* ---- CURSOR ---- */
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
const spotlight = document.getElementById('spotlight');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX;my=e.clientY;
  cursor.style.left=mx+'px';cursor.style.top=my+'px';
  spotlight.style.left=mx+'px';spotlight.style.top=my+'px';
});
function animateRing(){
  rx+=(mx-rx)*0.12;ry+=(my-ry)*0.12;
  ring.style.left=rx+'px';ring.style.top=ry+'px';
  requestAnimationFrame(animateRing);
}animateRing();

/* ---- PRELOADER ---- */
const bar=document.getElementById('preloader-bar');
const logo=document.querySelector('.preloader-logo');
gsap.to(logo,{opacity:1,duration:0.8,delay:0.3});
let prog=0;
const interval=setInterval(()=>{
  prog+=Math.random()*8+2;
  if(prog>=100){prog=100;clearInterval(interval);
    setTimeout(()=>{
      gsap.to('#preloader',{opacity:0,duration:0.8,onComplete:()=>{
        document.getElementById('preloader').style.display='none';
        animateHero();
      }});
    },400);
  }
  bar.style.width=prog+'%';
},80);

/* ---- THREE.JS HERO ---- */
function initHero(){
  const canvas=document.getElementById('hero-canvas');
  const renderer=new THREE.WebGLRenderer({canvas,alpha:true,antialias:true});
  renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));
  renderer.setSize(canvas.offsetWidth,canvas.offsetHeight);
  renderer.setClearColor(0x000000,0);
  const scene=new THREE.Scene();
  const camera=new THREE.PerspectiveCamera(60,canvas.offsetWidth/canvas.offsetHeight,0.1,100);
  camera.position.set(0,0,5);

  // Lighting
  const ambLight=new THREE.AmbientLight(0x111133,3);
  scene.add(ambLight);
  const blueLight=new THREE.PointLight(0x00bfff,8,20);
  blueLight.position.set(3,3,3);scene.add(blueLight);
  const purpleLight=new THREE.PointLight(0x7700ff,4,20);
  purpleLight.position.set(-3,-2,2);scene.add(purpleLight);
  const whiteLight=new THREE.DirectionalLight(0xffffff,2);
  whiteLight.position.set(0,5,5);scene.add(whiteLight);

  // Create floating shapes representing devices
  const objects=[];
  const materials=[
    new THREE.MeshPhysicalMaterial({color:0x1a1a2e,metalness:0.9,roughness:0.1,reflectivity:1}),
    new THREE.MeshPhysicalMaterial({color:0x0a1628,metalness:0.8,roughness:0.15,reflectivity:1}),
    new THREE.MeshPhysicalMaterial({color:0x1a0a28,metalness:0.85,roughness:0.1,reflectivity:1}),
    new THREE.MeshPhysicalMaterial({color:0x0a2818,metalness:0.9,roughness:0.08,reflectivity:1}),
    new THREE.MeshPhysicalMaterial({color:0x28180a,metalness:0.85,roughness:0.12,reflectivity:1}),
  ];

  // Phone shape
  const phone=new THREE.Group();
  const phoneBody=new THREE.Mesh(new THREE.BoxGeometry(0.45,0.9,0.06,1,1,1),materials[0]);
  const phoneScreen=new THREE.Mesh(new THREE.PlaneGeometry(0.38,0.75),
    new THREE.MeshBasicMaterial({color:0x00bfff,opacity:0.15,transparent:true}));
  phoneScreen.position.z=0.035;
  phone.add(phoneBody);phone.add(phoneScreen);
  phone.position.set(-2.5,0.3,-1);phone.rotation.set(0.2,-0.3,0.1);
  scene.add(phone);objects.push({mesh:phone,speed:0.003,float:0,floatSpeed:0.8});

  // Laptop shape
  const laptop=new THREE.Group();
  const base=new THREE.Mesh(new THREE.BoxGeometry(1.2,0.06,0.8),materials[1]);
  const screen=new THREE.Mesh(new THREE.BoxGeometry(1.2,0.8,0.04),materials[1]);
  screen.position.set(0,0.43,-0.38);screen.rotation.x=-1.2;
  const screenFace=new THREE.Mesh(new THREE.PlaneGeometry(1.05,0.68),
    new THREE.MeshBasicMaterial({color:0x00bfff,opacity:0.1,transparent:true}));
  screenFace.position.set(0,0.43,-0.37);screenFace.rotation.x=-1.2;
  laptop.add(base);laptop.add(screen);laptop.add(screenFace);
  laptop.position.set(2.2,-0.4,-0.5);laptop.rotation.set(0.1,0.4,-0.05);
  scene.add(laptop);objects.push({mesh:laptop,speed:0.002,float:1,floatSpeed:0.6});

  // Headphones shape
  const hpGroup=new THREE.Group();
  const hpBand=new THREE.Mesh(new THREE.TorusGeometry(0.35,0.04,8,30,Math.PI),materials[2]);
  hpBand.rotation.z=Math.PI;
  const earL=new THREE.Mesh(new THREE.CylinderGeometry(0.14,0.14,0.1,16),materials[2]);
  earL.position.set(-0.35,0,0);earL.rotation.z=Math.PI/2;
  const earR=earL.clone();earR.position.set(0.35,0,0);
  hpGroup.add(hpBand);hpGroup.add(earL);hpGroup.add(earR);
  hpGroup.position.set(-1.5,-1.2,-1);hpGroup.rotation.set(0.3,0.5,0.2);
  scene.add(hpGroup);objects.push({mesh:hpGroup,speed:0.004,float:2,floatSpeed:1});

  // Watch shape
  const watchGroup=new THREE.Group();
  const watchBody=new THREE.Mesh(new THREE.BoxGeometry(0.35,0.4,0.1),materials[3]);
  const watchFace=new THREE.Mesh(new THREE.PlaneGeometry(0.28,0.32),
    new THREE.MeshBasicMaterial({color:0x00bfff,opacity:0.12,transparent:true}));
  watchFace.position.z=0.055;
  const strapT=new THREE.Mesh(new THREE.BoxGeometry(0.28,0.2,0.04),materials[3]);
  strapT.position.y=0.3;
  const strapB=strapT.clone();strapB.position.y=-0.3;
  watchGroup.add(watchBody);watchGroup.add(watchFace);watchGroup.add(strapT);watchGroup.add(strapB);
  watchGroup.position.set(1.5,1.2,-1.5);watchGroup.rotation.set(-0.3,0.2,0.4);
  scene.add(watchGroup);objects.push({mesh:watchGroup,speed:0.0025,float:3,floatSpeed:0.9});

  // TV shape
  const tvGroup=new THREE.Group();
  const tvBody=new THREE.Mesh(new THREE.BoxGeometry(1.6,0.95,0.06),materials[4]);
  const tvScreen=new THREE.Mesh(new THREE.PlaneGeometry(1.4,0.78),
    new THREE.MeshBasicMaterial({color:0x00bfff,opacity:0.08,transparent:true}));
  tvScreen.position.z=0.035;
  const tvStand=new THREE.Mesh(new THREE.CylinderGeometry(0.04,0.08,0.3,8),materials[4]);
  tvStand.position.y=-0.62;
  const tvBase=new THREE.Mesh(new THREE.BoxGeometry(0.5,0.04,0.2),materials[4]);
  tvBase.position.y=-0.77;
  tvGroup.add(tvBody);tvGroup.add(tvScreen);tvGroup.add(tvStand);tvGroup.add(tvBase);
  tvGroup.position.set(0.5,-0.8,-2.5);tvGroup.rotation.set(0.1,-0.2,0.05);
  scene.add(tvGroup);objects.push({mesh:tvGroup,speed:0.0015,float:4,floatSpeed:0.5});

  // Particles
  const particleGeo=new THREE.BufferGeometry();
  const pCount=200;const pPos=new Float32Array(pCount*3);
  for(let i=0;i<pCount*3;i++) pPos[i]=(Math.random()-0.5)*16;
  particleGeo.setAttribute('position',new THREE.BufferAttribute(pPos,3));
  const pMat=new THREE.PointsMaterial({color:0x00bfff,size:0.03,transparent:true,opacity:0.5});
  scene.add(new THREE.Points(particleGeo,pMat));

  // Mouse parallax
  let targetX=0,targetY=0;
  document.addEventListener('mousemove',e=>{
    targetX=(e.clientX/window.innerWidth-0.5)*2;
    targetY=-(e.clientY/window.innerHeight-0.5)*2;
  });

  let t=0;
  function render(){
    requestAnimationFrame(render);
    t+=0.01;
    camera.position.x+=(targetX*0.5-camera.position.x)*0.04;
    camera.position.y+=(targetY*0.3-camera.position.y)*0.04;
    camera.lookAt(scene.position);
    objects.forEach((o,i)=>{
      o.mesh.rotation.y+=o.speed;
      o.mesh.rotation.x+=o.speed*0.5;
      o.mesh.position.y+=Math.sin(t*o.floatSpeed+o.float)*0.002;
    });
    blueLight.position.x=Math.sin(t*0.5)*4;
    blueLight.position.y=Math.cos(t*0.3)*3;
    renderer.render(scene,camera);
  }render();

  window.addEventListener('resize',()=>{
    const w=canvas.offsetWidth,h=canvas.offsetHeight;
    renderer.setSize(w,h);camera.aspect=w/h;camera.updateProjectionMatrix();
  });
}

function animateHero(){
  initHero();
  gsap.from('.hero-eyebrow',{opacity:0,y:20,duration:0.8,delay:0.2});
  gsap.from('.hero-title',{opacity:0,y:40,duration:1,delay:0.4,ease:'power3.out'});
  gsap.from('.hero-sub',{opacity:0,y:30,duration:0.8,delay:0.7});
  gsap.from('.hero-actions',{opacity:0,y:20,duration:0.8,delay:0.9});
  gsap.from('.hero-scroll-hint',{opacity:0,duration:1,delay:1.5});
}

/* ---- NAVBAR SCROLL ---- */
const navbar=document.getElementById('navbar');
window.addEventListener('scroll',()=>{
  navbar.classList.toggle('scrolled',window.scrollY>60);
});

/* ---- MOBILE MENU ---- */
const ham=document.getElementById('hamburger');
const mMenu=document.getElementById('mobileMenu');
const mClose=document.getElementById('mobileClose');
ham.addEventListener('click',()=>mMenu.classList.add('open'));
mClose.addEventListener('click',()=>mMenu.classList.remove('open'));
function closeMobile(){mMenu.classList.remove('open');}

/* ---- REVEAL ON SCROLL ---- */
const reveals=document.querySelectorAll('.reveal');
const revealObs=new IntersectionObserver((entries)=>{
  entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('visible');}});
},{threshold:0.12,rootMargin:'0px 0px -40px 0px'});
reveals.forEach(r=>revealObs.observe(r));

/* ---- CARD TILT ---- */
document.querySelectorAll('.product-card,.cat-card,.why-card').forEach(card=>{
  card.addEventListener('mousemove',e=>{
    const rect=card.getBoundingClientRect();
    const x=((e.clientX-rect.left)/rect.width-0.5)*16;
    const y=-((e.clientY-rect.top)/rect.height-0.5)*16;
    card.style.transform=`perspective(800px) rotateX(${y}deg) rotateY(${x}deg) translateY(-8px)`;
  });
  card.addEventListener('mouseleave',()=>{
    card.style.transform='';
  });
});

/* ---- COUNTDOWN ---- */
function setCountdown(id,endMs){
  const el=document.getElementById(id);
  if(!el)return;
  function tick(){
    const now=Date.now();const diff=endMs-now;
    if(diff<=0){el.querySelectorAll('.countdown-num').forEach(n=>n.textContent='00');return;}
    const d=Math.floor(diff/86400000);
    const h=Math.floor((diff%86400000)/3600000);
    const m=Math.floor((diff%3600000)/60000);
    const s=Math.floor((diff%60000)/1000);
    const nums=el.querySelectorAll('.countdown-num');
    const types=Array.from(el.querySelectorAll('[data-type]')).map(n=>n.dataset.type);
    types.forEach((t,i)=>{
      const val={days:d,hours:h,minutes:m,seconds:s}[t];
      if(nums[i*2!==undefined?i*2:i]) nums[i].textContent=String(val).padStart(2,'0');
    });
    el.querySelectorAll('[data-type]').forEach(n=>{
      const val={days:d,hours:h,minutes:m,seconds:s}[n.dataset.type];
      n.textContent=String(val).padStart(2,'0');
    });
    setTimeout(tick,1000);
  }tick();
}
setCountdown('countdown1',Date.now()+8*3600000+45*60000+30000);
setCountdown('countdown2',Date.now()+4*86400000+12*3600000);

/* ---- BACKGROUND PARTICLES CANVAS ---- */
const pCanvas=document.getElementById('particles-canvas');
const pCtx=pCanvas.getContext('2d');
let particles=[];
function resizeParticles(){pCanvas.width=window.innerWidth;pCanvas.height=window.innerHeight;}
resizeParticles();window.addEventListener('resize',resizeParticles);
for(let i=0;i<80;i++){
  particles.push({
    x:Math.random()*window.innerWidth,y:Math.random()*window.innerHeight,
    r:Math.random()*1.5+0.3,speed:Math.random()*0.3+0.1,
    opacity:Math.random()*0.4+0.1,dir:Math.random()*Math.PI*2
  });
}
function animParticles(){
  pCtx.clearRect(0,0,pCanvas.width,pCanvas.height);
  particles.forEach(p=>{
    p.x+=Math.cos(p.dir)*p.speed;p.y+=Math.sin(p.dir)*p.speed;
    if(p.x<0)p.x=pCanvas.width;if(p.x>pCanvas.width)p.x=0;
    if(p.y<0)p.y=pCanvas.height;if(p.y>pCanvas.height)p.y=0;
    pCtx.beginPath();pCtx.arc(p.x,p.y,p.r,0,Math.PI*2);
    pCtx.fillStyle=`rgba(0,191,255,${p.opacity})`;pCtx.fill();
  });
  requestAnimationFrame(animParticles);
}animParticles();

/* ---- FORM SUBMIT ---- */
function handleForm(e){
  e.preventDefault();
  const btn=e.target.querySelector('button[type=submit]');
  const orig=btn.textContent;
  btn.textContent='✅ Message Sent!';
  btn.style.background='linear-gradient(135deg,#00cc66,#008844)';
  setTimeout(()=>{btn.textContent=orig;btn.style.background='';},3000);
}

/* ---- GSAP ScrollTrigger (for section headings) ---- */
gsap.registerPlugin(ScrollTrigger);
document.querySelectorAll('.section-title').forEach(el=>{
  gsap.from(el,{
    scrollTrigger:{trigger:el,start:'top 85%',once:true},
    opacity:0,y:50,duration:1,ease:'power3.out'
  });
});
</script>
</body>
</html>
