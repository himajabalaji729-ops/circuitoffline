# circuitoffline
offline AI-assisted circuit tutor for biginner
index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Circuit Mentor</title>
<style>
:root{--bg:#f6f8fb;--fg:#14202e;--card:#fff;--line:#d5dde8;--accent:#1a6fd4;--ok:#17803d;--okbg:#e5f5ea;--bad:#b3261e;--badbg:#fdeceb;--mut:#5b6b7e;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1722;--fg:#e6edf5;--card:#18222f;--line:#2b394a;--accent:#5aa2f5;--ok:#5fd18a;--okbg:#14301f;--bad:#ff8a80;--badbg:#3a1a18;--mut:#9aabbd}}
:root[data-theme="dark"]{--bg:#0f1722;--fg:#e6edf5;--card:#18222f;--line:#2b394a;--accent:#5aa2f5;--ok:#5fd18a;--okbg:#14301f;--bad:#ff8a80;--badbg:#3a1a18;--mut:#9aabbd}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--fg);font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;line-height:1.5}
.wrap{max-width:720px;margin:0 auto;padding:16px}
h1{margin:8px 0 2px;font-size:1.6rem}
.sub{color:var(--mut);margin:0 0 14px}
.tabs{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:12px}
.tabs button{flex:1;min-width:120px;padding:10px;border:1px solid var(--line);background:var(--card);color:var(--fg);border-radius:8px;font-size:.95rem;cursor:pointer}
.tabs button.on{background:var(--accent);color:#fff;border-color:var(--accent)}
.card{background:var(--card);border:1px solid var(--line);border-radius:10px;padding:14px;margin-bottom:12px}
select,textarea,input{width:100%;box-sizing:border-box;padding:9px;border:1px solid var(--line);border-radius:8px;background:var(--bg);color:var(--fg);font:inherit}
textarea{font-family:ui-monospace,Consolas,monospace;min-height:110px}
label{display:block;margin:10px 0 4px;font-weight:600}
.btn{display:inline-block;margin-top:10px;padding:10px 16px;border:0;border-radius:8px;background:var(--accent);color:#fff;font-size:1rem;cursor:pointer;text-decoration:none}
.msg{padding:10px 12px;border-radius:8px;margin-top:10px}
.ok{background:var(--okbg);color:var(--ok)}.bad{background:var(--badbg);color:var(--bad)}
.err{border:1px solid var(--line);border-radius:8px;padding:10px;margin-top:10px}
.err b{display:block;margin-bottom:4px}
.hide{display:none}
.opt{display:block;width:100%;text-align:left;margin-top:6px;padding:9px;border:1px solid var(--line);background:var(--bg);color:var(--fg);border-radius:8px;font:inherit;cursor:pointer}
pre{background:var(--bg);border:1px solid var(--line);border-radius:8px;padding:8px;overflow-x:auto;margin:8px 0}
.big{font-size:1.5rem;font-weight:700}
small{color:var(--mut)}

:root{--teal:#0f766e;--violet:#6d3fd1;--amber:#b45309;--rose:#be185d;--on:#fff}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--teal:#2dd4bf;--violet:#b39dfa;--amber:#fbbf24;--rose:#f472b6;--on:#0b1220}}
:root[data-theme="dark"]{--teal:#2dd4bf;--violet:#b39dfa;--amber:#fbbf24;--rose:#f472b6;--on:#0b1220}
h1{background:linear-gradient(90deg,var(--teal),var(--violet),var(--rose));-webkit-background-clip:text;background-clip:text;color:transparent;-webkit-text-fill-color:transparent}
.tabs button.on,.btn{color:var(--on)}
.tabs button[data-t="a"].on{background:var(--teal);border-color:var(--teal)}
.tabs button[data-t="c"].on{background:var(--violet);border-color:var(--violet)}
.tabs button[data-t="r"].on{background:var(--amber);border-color:var(--amber)}
#a{border-top:5px solid var(--teal)}#c{border-top:5px solid var(--violet)}#r{border-top:5px solid var(--amber)}
#a .btn{background:var(--teal)}#a .btn.sim{background:var(--rose)}
#c h3{color:var(--violet)}#c .opt:hover{border-color:var(--violet)}
#r .big{color:var(--amber)}
.err{border-left:5px solid var(--rose)}
.tabs button[data-t="h"].on{background:var(--rose);border-color:var(--rose)}
#h{border-top:5px solid var(--rose)}#h h3{color:var(--rose);margin-bottom:4px}#h .btn{background:var(--rose)}
#h ol,#h ul{padding-left:22px;margin:6px 0}#h li{margin:4px 0}
.tabs button[data-t="s"].on{background:var(--accent);border-color:var(--accent)}
#s{border-top:5px solid var(--accent)}#s h3{color:var(--accent);margin-bottom:4px}#s ul{padding-left:22px;margin:6px 0}
.big2{font-weight:700;font-size:1.1rem;margin:8px 0}
.gen{border:1px dashed var(--violet);border-radius:10px;padding:12px;margin-bottom:14px}
.tabs button[data-t="p"].on{background:var(--teal);border-color:var(--teal)}
#p{border-top:5px solid var(--teal)}#p .btn{background:var(--teal)}#p ul{padding-left:22px;margin:6px 0}
.note{padding:10px 12px;border:1px solid var(--line);border-radius:8px;color:var(--mut)}
.tabs button[data-t="n"].on{background:var(--violet);border-color:var(--violet)}
#n{border-top:5px solid var(--violet)}#n h3{color:var(--violet);margin-bottom:4px}#n ul{padding-left:22px;margin:6px 0}#n li{margin:4px 0}
</style>
</head>
<body>
<div class="wrap">
<h1>&#9889; Circuit Mentor</h1>
<p class="sub">A free, beginner-friendly tutor that tells you WHY your circuit is wrong. New here? Open the <b>How to use</b> tab.</p>
<div class="tabs">
<button class="on" data-t="a">Analyze circuit</button>
<button data-t="p">Scan photo (online only)</button>
<button data-t="s">Standard circuits</button>
<button data-t="c">Challenge mode</button>
<button data-t="r">Resistor calculator</button>
<button data-t="h">How to use</button>
<button data-t="n">Project notes</button>
</div>

<div id="a" class="card">
<label for="tpl">Template</label>
<select id="tpl"></select>
<label for="net">Circuit (one component per line)</label>
<textarea id="net"></textarea>
<small>V1 VCC GND 5 (battery) &middot; R1 VCC N1 330 (resistor) &middot; D1 N1 GND (LED: anode, cathode)</small><br>
<button class="btn" id="go">Analyze</button>
<a class="btn sim" href="https://falstad.com/circuit/" target="_blank" rel="noopener">Open simulator (Falstad)</a>
<div id="out"></div>
</div>


<div id="h" class="card hide">
<h2>How to use Circuit Mentor</h2>
<p><b>What it does:</b> you write a simple LED circuit as text. Circuit Mentor finds wiring mistakes, explains <i>why</i> each one is a problem, and tells you how to fix it.</p>
<p><b>What it does not do:</b> it is a checker and tutor, not a simulator. To watch a circuit run, use the free <b>Falstad</b> simulator button on the first tab.</p>

<h3>Step by step</h3>
<ol>
<li>Open the <b>Analyze circuit</b> tab.</li>
<li>Choose a template, or type your own circuit in the box.</li>
<li>Press <b>Analyze</b>.</li>
<li>Read each problem. <b>Why it matters</b> explains the mistake. <b>How to fix</b> tells you what to change.</li>
<li>Change the circuit text and press Analyze again. Repeat until it says "Circuit looks good!"</li>
<li>Optional: press <b>Open simulator (Falstad)</b> and build the fixed circuit there to see it work.</li>
</ol>

<h3>How to write a circuit</h3>
<p>One component per line: <b>name, first node, second node, value</b>. A node is just a name for a connection point. Two pins with the same node name are joined by a wire.</p>
<pre>V1 VCC GND 5      battery: + side, - side, 5 volts
R1 VCC N1 330     resistor between VCC and N1, 330 ohm
D1 N1 GND         LED: anode to N1, cathode to GND</pre>
<p>The first letter of the name tells the tool what it is: <b>V</b> = battery, <b>R</b> = resistor, <b>D</b> = LED.</p>

<h3>Mistakes it can find</h3>
<ul>
<li><b>Short circuit:</b> both battery terminals are on the same node.</li>
<li><b>No resistor:</b> an LED has no resistor to limit the current.</li>
<li><b>Reversed LED:</b> the LED is connected the wrong way round.</li>
<li><b>Floating node:</b> a connection that goes nowhere, so the loop is open.</li>
</ul>

<h3>Try an example</h3>
<p>This circuit has no resistor. Press the button, then read the explanation.</p>
<pre>V1 VCC GND 5
D1 VCC GND</pre>
<button class="btn" id="tryit">Try this example</button>

<h3>The other tabs</h3>
<ul>
<li><b>Scan photo (online only):</b> needs internet and a Claude sign-in, and does not work in the offline file. Choose a photo of a circuit, press Scan, check the text it produces, then press Analyze.</li>
<li><b>Project notes:</b> a summary of the project and answers to likely questions.</li>
<li><b>Standard circuits:</b> 5 textbook circuits (voltage divider, transistor switch, RC filter, rectifier, op-amp). Pick one, type your values, and read the result and common mistakes.</li>
<li><b>Challenge mode:</b> a practice generator that makes a new random resistor question every time, plus  4 short puzzles. Tap an answer, and open the hint if you are stuck.</li>
<li><b>Resistor calculator:</b> enter supply voltage, LED voltage and current. It gives the resistor value and the next standard size.</li>
</ul>

<h3>Limits</h3>
<p>It understands batteries, resistors and LEDs only. It checks the wiring logic. It does not calculate voltages or simulate behaviour.</p>
</div>

<div id="p" class="card hide">
<p><b>Scan a circuit photo. Needs internet.</b> Take a clear photo of a printed or hand-drawn circuit. Claude reads it and fills in the circuit text for you to check.</p>
<div id="poff" class="note">Scanning does not work offline. To scan, open this page with an internet connection and sign in to Claude. Without internet, use the other tabs or type the circuit yourself.</div>
<div id="pctl" class="hide">
<label for="pfile">Photo of the circuit</label>
<input id="pfile" type="file" accept="image/*">
<img id="pprev" class="hide" alt="Preview of the circuit photo" style="max-width:100%;margin-top:10px;border-radius:8px;border:1px solid var(--line)">
<button class="btn" id="pgo">Scan circuit</button>
<div id="pmsg"></div>
</div>
<div id="pout"></div>
<small>It understands batteries, resistors and LEDs only. AI can misread a photo, so always check the text.</small>
</div>
<div id="s" class="card hide"><label for="lib">Choose a standard circuit</label><select id="lib"></select><div id="libbox"></div></div>
<div id="n" class="card hide">
<h2>Project notes</h2>
<p><b>Circuit Mentor</b> | Hack Sphere Hackathon, 10/10/2026 | P Himaja, ECE</p>

<h3>What it is</h3>
<p>A free, beginner-friendly tool for ECE students. You type a simple LED circuit as text, and it finds wiring mistakes, explains why each one is a problem, and shows the fix. It is a checker and tutor, not a simulator. For simulation it links to the free Falstad simulator.</p>

<h3>Features</h3>
<ul>
<li><b>4 error checks:</b> short circuit, missing resistor, reversed LED, open (floating) node.</li>
<li><b>Standard circuits:</b> voltage divider, transistor switch, RC filter, rectifier, inverting op-amp, each with a calculator and common mistakes.</li>
<li><b>Challenge mode:</b> a random practice generator plus 4 puzzles with hints.</li>
<li><b>Resistor calculator</b> with the next standard value.</li>
<li><b>Scan photo (online only):</b> reads a photo of a circuit and fills in the text for you to check. Needs internet and a Claude sign-in.</li>
<li><b>Works offline:</b> everything except Scan photo. One file, no install, no data collected.</li>
</ul>

<h3>How it works</h3>
<p>The text is read line by line into components and nodes. Four logic rules run on those nodes. An LED is flagged if there is a route from battery + to battery - through it with no resistor in the way, and a node that appears only once is an open end. Each error type has a stored explanation and fix. It is a rule-based expert system: reliable, instant, and every answer can be explained.</p>

<h3>How I built it</h3>
<p>I defined the problem from my ECE experience and chose the four common errors. I built the checker with an AI assistant, tested it in Google Colab with a correct circuit and wrong ones, then turned it into a single web page. After my brother reviewed it, I simplified the challenge wording, added colours and added the manual.</p>

<h3>Likely judge questions</h3>
<ul>
<li><b>Is it really AI?</b> The checker is rule-based. The rules copy how a teacher spots common mistakes. The photo scan uses an AI vision model online, and an AI chat layer is a next step.</li>
<li><b>Difference from Tinkercad or Falstad?</b> They simulate. This diagnoses and teaches why, and links to Falstad.</li>
<li><b>How accurate is it?</b> Accurate for the 4 error types it covers. It does not claim more.</li>
<li><b>How would you scale it?</b> More rules (transistor, capacitor polarity, op-amp), drawing input, an AI chat layer, a mobile app.</li>
<li><b>Why did you build it?</b> I faced these errors while troubleshooting circuits in my internship and my Arduino fire fighter robot project.</li>
</ul>

<h3>Limits (say these first)</h3>
<p>The checker understands only batteries, resistors and LEDs, and checks wiring logic, not voltages. The reversed-LED rule catches direct connections to the battery only. Scan is online only and can misread a photo, so the text must be checked.</p>
</div>
<div id="c" class="card hide"></div>

<div id="r" class="card hide">
<p>Find the resistor for an LED: <b>R = (Vsupply &minus; Vled) / I</b></p>
<label for="v">Supply voltage (V)</label><input id="v" type="number" value="5" step="0.1">
<label for="vf">LED voltage drop (V)</label><input id="vf" type="number" value="2" step="0.1">
<label for="ma">LED current (mA)</label><input id="ma" type="number" value="10" step="1">
<div id="res"></div>
</div>
</div>

<script>
var TEMPLATES={"Good LED circuit":"V1 VCC GND 5\nR1 VCC N1 330\nD1 N1 GND","LED without resistor":"V1 VCC GND 5\nD1 VCC GND","Reversed LED":"V1 VCC GND 5\nR1 VCC N1 330\nD1 GND N1","Floating connection":"V1 VCC GND 5\nR1 VCC N1 330\nD1 N2 GND"};
var EXPLAIN={
short_circuit:["Both battery terminals are on the same node, so current has an unlimited path and the battery can overheat.","Put a load (like a resistor + LED) between the two terminals."],
no_resistor:["Once an LED turns on, its resistance is very low. Without a resistor, the current rises too high and burns it out.","Add a resistor in series. R = (Vsupply - Vled) / I. For 5V, a 2V LED and 10 mA: (5-2)/0.01 = 300 ohm, so use 330 ohm."],
reversed_led:["An LED conducts only from anode to cathode. Connected backwards, it blocks the current and stays off.","Swap the LED so the anode faces the positive side."],
floating:["A node with only one connection is an open end, so no current can complete the loop.","Connect that pin to the rest of the circuit, or remove the dangling part."]};
var CH=[
{t:"Challenge 1: The LED burns out",c:"V1 VCC GND 5\nD1 VCC GND",q:"An LED is connected straight to a 5 V battery, and it burns out. Why?",o:["The LED was connected backwards","There is no resistor to limit the current","The battery was too weak"],a:1,h:"Think about what controls how much current flows through the LED.",w:"Without a resistor, too much current flows and the LED overheats."},
{t:"Challenge 2: The LED does not light",c:"V1 VCC GND 5\nR1 VCC N1 330\nD1 GND N1",q:"All the wires are connected, but the LED does not light up. Why?",o:["The battery is dead","The LED is connected the wrong way round","The resistor is too small"],a:1,h:"Check which LED leg is connected to the positive side.",w:"An LED works in only one direction (anode to cathode). Turn it around."},
{t:"Challenge 3: The broken loop",c:"V1 VCC GND 5\nR1 VCC N1 330\nD1 N2 GND",q:"The parts look fine, but no current flows. Why?",o:["There is a gap, so the loop is not closed","The resistor value is too high","The battery is only 5 V"],a:0,h:"Trace the path from the + side to the - side with your finger. Does it break anywhere?",w:"R1 ends at N1, but D1 starts at N2. They are not joined, so the loop is broken."},
{t:"Challenge 4: Choose the resistor",c:"Supply: 9 V | LED drop: 2 V | LED current: 20 mA",q:"Using the formula, which resistor value do you need?",o:["35 ohm","350 ohm","3500 ohm"],a:1,h:"Use R = (Vsupply - Vled) / I. Change mA to amps first (20 mA = 0.02 A).",w:"(9 - 2) / 0.02 = 350 ohm. In real life, use the next standard value: 390 ohm."}];
var E12=[10,12,15,18,22,27,33,39,47,56,68,82];

function parse(s){var o=[];s.trim().split(/\r?\n/).forEach(function(l){var p=l.trim().split(/\s+/);if(p.length<3||!p[0])return;o.push({name:p[0],type:p[0][0].toUpperCase(),nodes:[p[1],p[2]]});});return o;}
function ledUnprotected(d,v,D){
var plus=v.nodes[0],minus=v.nodes[1],others=D.filter(function(x){return x!==d});
function reach(from,to){var seen={};seen[from]=1;var q=[from];
while(q.length){var n=q.shift();if(n===to)return true;
others.forEach(function(x){var a=x.nodes[0],b=x.nodes[1];
if(a===n&&!seen[b]){seen[b]=1;q.push(b);}else if(b===n&&!seen[a]){seen[a]=1;q.push(a);}});}
return false;}
var a=d.nodes[0],b=d.nodes[1];
return (reach(plus,a)&&reach(b,minus))||(reach(plus,b)&&reach(a,minus));}
function check(s){
var cs=parse(s),e=[];
var B=cs.filter(function(c){return c.type==="V"}),R=cs.filter(function(c){return c.type==="R"}),D=cs.filter(function(c){return c.type==="D"});
B.forEach(function(v){if(v.nodes[0]===v.nodes[1])e.push(["short_circuit",v.name+" has both terminals on the same node."]);});
D.forEach(function(d){var bad;if(B.length){bad=B.some(function(v){return ledUnprotected(d,v,D)});}else{bad=!R.some(function(r){return r.nodes.some(function(n){return d.nodes.indexOf(n)>-1})});}if(bad)e.push(["no_resistor",d.name+" has no current-limiting resistor."]);});
D.forEach(function(d){B.forEach(function(v){if(d.nodes[0]===v.nodes[1]||d.nodes[1]===v.nodes[0])e.push(["reversed_led",d.name+" looks reversed (anode/cathode swapped)."]);});});
var cnt={};cs.forEach(function(c){c.nodes.forEach(function(n){cnt[n]=(cnt[n]||0)+1})});
Object.keys(cnt).forEach(function(n){if(cnt[n]===1)e.push(["floating","Node "+n+" is connected to only one pin (open circuit)."]);});
return e;}
function stdVal(r){if(r<=0)return 0;var dec=Math.pow(10,Math.floor(Math.log10(r)));var m=[dec/10,dec,dec*10];for(var i=0;i<3;i++)for(var j=0;j<E12.length;j++){if(E12[j]*m[i]>=r)return E12[j]*m[i];}return r;}
function el(tag,cls,txt){var x=document.createElement(tag);if(cls)x.className=cls;if(txt!==undefined)x.textContent=txt;return x;}

var tpl=document.getElementById("tpl"),net=document.getElementById("net"),out=document.getElementById("out");
Object.keys(TEMPLATES).forEach(function(k){var o=el("option","",k);o.value=k;tpl.appendChild(o);});
net.value=TEMPLATES[tpl.value];
tpl.onchange=function(){net.value=TEMPLATES[tpl.value];out.innerHTML="";};
document.getElementById("go").onclick=function(){
out.innerHTML="";var errs=check(net.value);
if(!errs.length){out.appendChild(el("div","msg ok","Circuit looks good! No errors found."));return;}
out.appendChild(el("div","msg bad",errs.length+" problem(s) found"));
errs.forEach(function(x){var b=el("div","err");b.appendChild(el("b","",x[1]));var w=el("div");w.appendChild(el("b","","Why it matters: "));w.appendChild(document.createTextNode(EXPLAIN[x[0]][0]));var f=el("div");f.style.marginTop="6px";f.appendChild(el("b","","How to fix: "));f.appendChild(document.createTextNode(EXPLAIN[x[0]][1]));b.appendChild(w);b.appendChild(f);out.appendChild(b);});};

var chBox=document.getElementById("c");
CH.forEach(function(ch){
var box=el("div");box.appendChild(el("h3","",ch.t));box.appendChild(el("pre","",ch.c));box.appendChild(el("p","",ch.q));
var fb=el("div");
ch.o.forEach(function(opt,i){var b=el("button","opt",opt);b.onclick=function(){fb.innerHTML="";if(i===ch.a)fb.appendChild(el("div","msg ok","Correct! "+ch.w));else fb.appendChild(el("div","msg bad","Not quite. Try again or read the hint."));};box.appendChild(b);});
var hb=el("button","opt","Need a hint?");var ht=el("small","hide",ch.h);hb.onclick=function(){ht.classList.toggle("hide");};
box.appendChild(hb);box.appendChild(ht);box.appendChild(fb);box.appendChild(el("hr"));chBox.appendChild(box);});

function calc(){
var v=parseFloat(document.getElementById("v").value),vf=parseFloat(document.getElementById("vf").value),ma=parseFloat(document.getElementById("ma").value),res=document.getElementById("res");
res.innerHTML="";
if(!(v>0)||!(vf>0)||!(ma>0)){res.appendChild(el("div",
