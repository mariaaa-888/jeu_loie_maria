<!DOCTYPE html>
<html lang="fr"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Le jeu de l’oie de Maria</title>
<style>
:root{--bg1:#f3f0ff;--bg2:#e0f4ff;--card:#ffffffd9;--edge:#b9b3e6;--text:#1b1740;--muted:#5f5a85;--a:#7c3aed;--b:#06b6d4;--cell:#ffffff;--good:#118a52;--bad:#c62828;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg1:#120d2e;--bg2:#06243a;--card:#1b1647cc;--edge:#4b3fa0;--text:#f1eeff;--muted:#a9a3d6;--a:#a78bfa;--b:#22d3ee;--cell:#221c55;--good:#4ade80;--bad:#ff8a80}}
:root[data-theme="dark"]{--bg1:#120d2e;--bg2:#06243a;--card:#1b1647cc;--edge:#4b3fa0;--text:#f1eeff;--muted:#a9a3d6;--a:#a78bfa;--b:#22d3ee;--cell:#221c55;--good:#4ade80;--bad:#ff8a80}
html{height:100%;scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;min-height:100%;color:var(--text);font-family:"Avenir Next","Segoe UI",system-ui,sans-serif;line-height:1.4;background:linear-gradient(135deg,var(--bg1),var(--bg2)) fixed;overflow-x:hidden}
.orb{position:fixed;border-radius:50%;filter:blur(70px);opacity:.45;pointer-events:none;animation:float 14s ease-in-out infinite alternate}
.o1{width:300px;height:300px;background:var(--a);top:-80px;left:-80px}.o2{width:340px;height:340px;background:var(--b);bottom:-100px;right:-80px;animation-delay:-6s}
@keyframes float{to{transform:translate(60px,40px) scale(1.15)}}
main{position:relative;max-width:680px;margin:0 auto;padding:18px 14px 40px}
h1{font-family:"Trebuchet MS","Avenir Next",sans-serif;font-size:2.3rem;line-height:1.05;margin:.1em 0;font-weight:900;background:linear-gradient(90deg,var(--a),var(--b),var(--a));background-size:200% auto;-webkit-background-clip:text;background-clip:text;color:transparent;animation:shine 5s linear infinite}
@keyframes shine{to{background-position:200% center}}
.sub{color:var(--muted);margin:0 0 14px}
.panel{background:var(--card);border:1.5px solid var(--edge);border-radius:16px;padding:14px;margin-bottom:12px;backdrop-filter:blur(8px);box-shadow:0 8px 30px #7c3aed22}
.board{display:grid;grid-template-columns:repeat(6,1fr);gap:5px;margin-bottom:12px;padding:8px;border-radius:18px;background:var(--card);border:1.5px solid var(--edge);box-shadow:0 0 40px #7c3aed33}
.c{position:relative;aspect-ratio:1;background:var(--cell);border:1.5px solid var(--edge);border-radius:9px;padding:3px;font-size:.62rem;display:flex;flex-direction:column;justify-content:space-between;min-width:0;transition:box-shadow .3s}
.c b{color:var(--muted);font-size:.68rem}.c i{font-style:normal;font-size:1rem;text-align:center;line-height:1}
.c.oie{border-color:#f5b301;box-shadow:inset 0 0 12px #f5b30144}.c.q{border-color:var(--b);box-shadow:inset 0 0 12px #06b6d444}
.c.bad{border-color:var(--bad);box-shadow:inset 0 0 12px #ef444444}.c.fin{border:2.5px solid var(--good);box-shadow:0 0 16px var(--good)}
.c.pulse{animation:pulse .7s}@keyframes pulse{40%{transform:scale(1.14);box-shadow:0 0 22px var(--a)}}
.pawns{position:absolute;right:2px;bottom:2px;display:flex;flex-wrap:wrap;gap:2px;justify-content:flex-end;max-width:78%}
.p{width:13px;height:13px;border-radius:50%;border:2px solid #fff;box-shadow:0 0 8px var(--c),0 0 0 1px #0006;background:var(--c);animation:glow 1.6s ease-in-out infinite alternate}
.p.cur{width:17px;height:17px;box-shadow:0 0 14px 3px var(--c),0 0 0 1px #0006}
@keyframes glow{to{transform:scale(1.18)}}
.row{display:flex;align-items:center;gap:14px;flex-wrap:wrap}
button{font:inherit;cursor:pointer;border-radius:12px;border:0;background:linear-gradient(135deg,var(--a),var(--b));color:#fff;padding:11px 20px;font-weight:800;box-shadow:0 4px 16px #7c3aed55;transition:transform .15s}
button:hover:not(:disabled){transform:translateY(-2px) scale(1.03)}button.alt{background:transparent;color:var(--text);border:1.5px solid var(--edge);box-shadow:none}
button:disabled{opacity:.45;cursor:default}button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid var(--b);outline-offset:2px}
.die{width:64px;height:64px;border-radius:14px;display:grid;place-items:center;font-size:2.1rem;font-weight:900;color:#fff;background:linear-gradient(135deg,var(--a),var(--b));box-shadow:0 0 22px var(--a)}
.die.roll{animation:spin .6s}@keyframes spin{0%{transform:rotate(0) scale(.7)}60%{transform:rotate(540deg) scale(1.2)}100%{transform:rotate(720deg) scale(1)}}
.who{font-weight:800;font-size:1.1rem;margin-bottom:6px}.dot{display:inline-block;width:14px;height:14px;border-radius:50%;vertical-align:-2px;margin-right:6px;box-shadow:0 0 10px var(--c)}
#msg{min-height:2.8em;margin:10px 0 0}
.plist{display:grid;gap:8px;margin:12px 0}.pl{display:flex;gap:8px;align-items:center}
.pl input[type=text]{flex:1;min-width:0;font:inherit;padding:8px 10px;border-radius:10px;border:1.5px solid var(--edge);background:var(--cell);color:var(--text)}
.pl input[type=color]{width:46px;height:40px;border:1.5px solid var(--edge);border-radius:10px;background:var(--cell);padding:2px;cursor:pointer}
select{font:inherit;padding:7px 9px;border-radius:10px;border:1.5px solid var(--edge);background:var(--cell);color:var(--text)}
.opts{display:grid;gap:8px;margin-top:10px}.opts button{text-align:left;background:var(--cell);color:var(--text);border:1.5px solid var(--edge);box-shadow:none}
.opts button.ok{background:var(--good);color:#fff}.opts button.ko{background:var(--bad);color:#fff}
.legend{font-size:.85rem;color:var(--muted)}.legend span{white-space:nowrap;margin-right:10px}.hide{display:none}
.shake{animation:sh .5s}@keyframes sh{20%{transform:translateX(-8px)}40%{transform:translateX(8px)}60%{transform:translateX(-5px)}80%{transform:translateX(5px)}}
.fx{position:fixed;width:8px;height:8px;border-radius:50%;pointer-events:none;z-index:20}
#cv{position:fixed;inset:0;pointer-events:none;z-index:30}
@media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
</style></head><body>
<div class="orb o1"></div><div class="orb o2"></div><canvas id="cv"></canvas>
<main>
<h1>Le jeu de l’oie de Maria</h1>
<p class="sub">Arrive la première sur la case 36, pile. Les cases ❓ posent une question sur les limites.</p>
<section class="panel" id="setup">
 <label>Nombre de joueurs <select id="np"></select></label>
 <div class="plist" id="plist"></div>
 <button id="start">Lancer la partie</button>
</section>
<section id="game" class="hide">
 <div class="board" id="board"></div>
 <div class="panel"><div class="row"><div class="die" id="die">–</div>
 <div><div class="who" id="who"></div><button id="roll">Lancer le dé</button></div></div><p id="msg" aria-live="polite"></p></div>
 <div class="panel legend"><span>🪿 Oie : avance encore</span><span>🌉 6 → 12</span><span>🕳️ 19 : passe un tour</span><span>🌀 25 → 15</span><span>💀 34 → 1</span><span>❓ Faux = recule de 2</span></div>
 <button class="alt" id="again">Nouvelle partie</button> <button class="alt" id="mute" aria-pressed="false">🔊 Son activé</button>
</section>
<section class="panel hide" id="quiz"><div id="qtext" style="font-size:1.15rem;font-weight:800"></div><div class="opts" id="opts"></div><p id="qfb" style="margin:10px 0 0"></p></section>
</main>
<script>
const N=36,COLORS=["#ef4444","#3b82f6","#22c55e","#f59e0b","#a855f7","#ec4899","#14b8a6","#f97316","#84cc16","#06b6d4"];
const OIE=[5,9,14,18,23,27,32],Q=[3,8,11,16,21,29],JUMP={6:12,25:15,34:1},WELL=19;
const QS=[["lim 1/x quand x → +∞ vaut…",["0","+∞","1"],0],["lim x² quand x → +∞ vaut…",["0","+∞","−∞"],1],["lim 1/x² quand x → 0 vaut…",["0","−∞","+∞"],2],["lim 1/x quand x → 0⁻ vaut…",["−∞","+∞","0"],0],["lim 1/x quand x → 0⁺ vaut…",["−∞","0","+∞"],2],["lim x³ quand x → −∞ vaut…",["+∞","−∞","0"],1],["lim (3x + 1) quand x → +∞ vaut…",["3","+∞","0"],1],["Lequel est une forme indéterminée ?",["+∞ + ∞","+∞ − ∞","+∞ × 2"],1],["lim (2x − 5)/(x + 1) quand x → +∞ vaut…",["2","−5","+∞"],0],["lim 1/xⁿ quand x → +∞ (n ≥ 1) vaut…",["+∞","1","0"],2],["lim 1/x³ quand x → 0⁻ vaut…",["+∞","−∞","0"],1],["Asymptote verticale x = a si lim f(x) en a vaut…",["0","un réel","±∞"],2],["lim e^x quand x → −∞ vaut…",["0","+∞","−∞"],0],["lim √x quand x → +∞ vaut…",["0","+∞","1"],1]];
let P=[],turn=0,busy=false,qs=[];
let AC=null,muted=false;
function tone(f,d,t,v,w,e){try{if(muted)return;if(!AC)AC=new(window.AudioContext||window.webkitAudioContext)();if(AC.state==="suspended")AC.resume();w=w||0;e=e||f;const o=AC.createOscillator(),g=AC.createGain(),s=AC.currentTime+w;o.type=t||"sine";o.frequency.setValueAtTime(f,s);o.frequency.exponentialRampToValueAtTime(e,s+d);g.gain.setValueAtTime(v||.12,s);g.gain.exponentialRampToValueAtTime(.001,s+d);o.connect(g);g.connect(AC.destination);o.start(s);o.stop(s+d)}catch(x){}}
const sfx={step:()=>tone(520+Math.random()*80,.07,"triangle",.07),dice:()=>{for(let i=0;i<6;i++)tone(200+Math.random()*300,.06,"square",.05,i*.08)},oie:()=>[660,880,1100].forEach((f,i)=>tone(f,.15,"square",.07,i*.09)),jump:()=>tone(300,.4,"sine",.14,0,1200),death:()=>tone(400,.8,"sawtooth",.1,0,50),well:()=>tone(300,.6,"sine",.14,0,70),good:()=>[523,659,784].forEach((f,i)=>tone(f,.18,"triangle",.12,i*.1)),bad:()=>tone(220,.45,"sawtooth",.1,0,90),win:()=>[523,659,784,1047,784,1047,1319].forEach((f,i)=>tone(f,.25,"triangle",.13,i*.13))};
const $=id=>document.getElementById(id),sleep=ms=>new Promise(r=>setTimeout(r,ms)),cellOf=n=>document.querySelector('[data-n="'+n+'"]');
for(let i=1;i<=10;i++){const o=document.createElement("option");o.textContent=i;if(i===2)o.selected=true;$("np").appendChild(o);}
function fields(){const n=+$("np").value,old=[...document.querySelectorAll(".pl")].map(r=>[r.children[0].value,r.children[1].value]);$("plist").innerHTML="";
 for(let i=0;i<n;i++){const r=document.createElement("div");r.className="pl";r.innerHTML='<input type="text" maxlength="14" aria-label="Nom du joueur '+(i+1)+'"><input type="color" aria-label="Couleur du joueur '+(i+1)+'">';
  r.children[0].value=old[i]?old[i][0]:(i===0?"Maria":"Joueur "+(i+1));r.children[1].value=old[i]?old[i][1]:COLORS[i];$("plist").appendChild(r);}}
$("np").onchange=fields;fields();
function burst(el,color,n=14){const r=el.getBoundingClientRect(),cx=r.left+r.width/2,cy=r.top+r.height/2;
 for(let i=0;i<n;i++){const d=document.createElement("span");d.className="fx";d.style.cssText="left:"+cx+"px;top:"+cy+"px;background:"+color+";box-shadow:0 0 8px "+color;document.body.appendChild(d);
  const a=Math.random()*6.28,s=30+Math.random()*60;d.animate([{transform:"translate(0,0) scale(1)",opacity:1},{transform:"translate("+Math.cos(a)*s+"px,"+Math.sin(a)*s+"px) scale(0)",opacity:0}],{duration:700,easing:"ease-out"}).onfinish=()=>d.remove();}}
function flash(n,color){const c=cellOf(n);if(!c)return;c.classList.remove("pulse");void c.offsetWidth;c.classList.add("pulse");burst(c,color);}
function confetti(){const cv=$("cv"),x=cv.getContext("2d");cv.width=innerWidth;cv.height=innerHeight;
 const ps=[...Array(160)].map(()=>({x:Math.random()*cv.width,y:-20-Math.random()*cv.height*.5,vx:Math.random()*4-2,vy:2+Math.random()*4,s:5+Math.random()*7,c:COLORS[Math.floor(Math.random()*10)],r:Math.random()*6}));
 let t=0;(function f(){x.clearRect(0,0,cv.width,cv.height);ps.forEach(p=>{p.x+=p.vx;p.y+=p.vy;p.r+=.15;x.save();x.translate(p.x,p.y);x.rotate(p.r);x.fillStyle=p.c;x.fillRect(-p.s/2,-p.s/2,p.s,p.s*.6);x.restore();});if(++t<260)requestAnimationFrame(f);else x.clearRect(0,0,cv.width,cv.height);})();}
function buildBoard(){const b=$("board");b.innerHTML="";
 for(let r=5;r>=0;r--)for(let c=0;c<6;c++){const n=r*6+(r%2===0?c:5-c)+1,el=document.createElement("div");
  el.className="c"+(OIE.includes(n)?" oie":"")+(Q.includes(n)?" q":"")+([WELL,34,25].includes(n)?" bad":"")+(n===N?" fin":"");el.dataset.n=n;
  const ic=OIE.includes(n)?"🪿":Q.includes(n)?"❓":n===6?"🌉":n===WELL?"🕳️":n===25?"🌀":n===34?"💀":n===N?"🏁":n===1?"🚩":"";
  el.innerHTML="<b>"+n+"</b><i>"+ic+"</i><div class='pawns'></div>";b.appendChild(el);}}
function drawPawns(){document.querySelectorAll(".pawns").forEach(e=>e.innerHTML="");
 P.forEach((p,i)=>{const c=cellOf(p.pos);if(!c)return;const d=document.createElement("span");d.className="p"+(i===turn?" cur":"");d.style.setProperty("--c",p.color);d.title=p.name;c.querySelector(".pawns").appendChild(d);});}
function who(){const p=P[turn];$("who").innerHTML='<span class="dot" style="--c:'+p.color+';background:'+p.color+'"></span>'+esc(p.name);drawPawns();}
function esc(s){return s.replace(/[&<>"]/g,m=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[m]))}
function say(t){$("msg").textContent=t}
async function step(p,to){const d=to>p.pos?1:-1;while(p.pos!==to){p.pos+=d;drawPawns();const c=cellOf(p.pos);if(c)burst(c,p.color,3);sfx.step();await sleep(170);}flash(p.pos,p.color);}
function ask(){return new Promise(res=>{if(!qs.length)qs=QS.map((_,i)=>i).sort(()=>Math.random()-.5);
 const q=QS[qs.pop()],o=$("opts");$("qtext").textContent=q[0];$("qfb").textContent="";o.innerHTML="";$("quiz").classList.remove("hide");
 [0,1,2].sort(()=>Math.random()-.5).forEach(i=>{const b=document.createElement("button");b.textContent=q[1][i];
  b.onclick=async()=>{[...o.children].forEach(x=>x.disabled=true);const ok=i===q[2];b.classList.add(ok?"ok":"ko");
   if(!ok)[...o.children].forEach(x=>{if(x.textContent===q[1][q[2]])x.classList.add("ok")});
   if(ok){sfx.good();burst(b,"#22c55e",20);}else{sfx.bad();document.body.classList.add("shake");}
   $("qfb").textContent=ok?"Bonne réponse, tu restes sur la case.":"Raté : la bonne réponse est "+q[1][q[2]]+". Recule de 2 cases.";
   await sleep(1700);document.body.classList.remove("shake");$("quiz").classList.add("hide");res(ok);};o.appendChild(b);});});}
async function land(p,roll){for(;;){
 if(OIE.includes(p.pos)){say("Case oie ! Tu avances encore de "+roll+".");sfx.oie();burst(cellOf(p.pos),"#f5b301",24);await sleep(900);await step(p,Math.min(p.pos+roll,N));continue;}
 if(JUMP[p.pos]){const t=JUMP[p.pos];say(p.pos===6?"Le pont : direct case 12.":p.pos===25?"Le labyrinthe : retour case 15.":"Tête de mort : retour au départ.");if(p.pos===34){sfx.death();document.body.classList.add("shake");}else sfx.jump();await sleep(900);document.body.classList.remove("shake");await step(p,t);continue;}
 if(p.pos===WELL){p.skip=1;sfx.well();say("Dans le puits : tu passes ton prochain tour.");}
 else if(Q.includes(p.pos)){say("Question de cours !");if(!(await ask())){await step(p,Math.max(p.pos-2,1));continue;}}
 break;}}
function win(){say("🏁 "+P[turn].name+" gagne la partie !");$("who").textContent="Victoire !";sfx.win();confetti();burst(cellOf(N),P[turn].color,40);}
async function play(){if(busy)return;busy=true;$("roll").disabled=true;const p=P[turn];
 if(p.skip){p.skip=0;say(p.name+" sort du puits et passe son tour.");await sleep(1100);return next();}
 const d=1+Math.floor(Math.random()*6),D=$("die");D.classList.remove("roll");void D.offsetWidth;D.classList.add("roll");D.textContent=d;sfx.dice();await sleep(650);
 let t=p.pos+d;if(t>N){t=N-(t-N);say("Il faut tomber pile sur 36 : rebond jusqu’à la case "+t+".");}else say(p.name+" fait "+d+".");
 await step(p,t);if(p.pos===N)return win();await land(p,d);if(p.pos===N)return win();next();}
function next(){turn=(turn+1)%P.length;who();busy=false;$("roll").disabled=false;if(P.length>1)say("À "+P[turn].name+" de jouer.");}
$("start").onclick=()=>{P=[...document.querySelectorAll(".pl")].map((r,i)=>({name:r.children[0].value.trim()||"Joueur "+(i+1),color:r.children[1].value,pos:1,skip:0}));
 turn=0;busy=false;qs=[];$("setup").classList.add("hide");$("game").classList.remove("hide");$("quiz").classList.add("hide");buildBoard();who();$("die").textContent="–";$("roll").disabled=false;say("Lance le dé, "+P[0].name+" !");};
$("mute").onclick=()=>{muted=!muted;$("mute").textContent=muted?"🔇 Son coupé":"🔊 Son activé";$("mute").setAttribute("aria-pressed",muted);};$("roll").onclick=play;$("again").onclick=()=>{$("game").classList.add("hide");$("setup").classList.remove("hide");};
</script></body></html>
