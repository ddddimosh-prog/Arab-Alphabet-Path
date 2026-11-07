# Arab-Alphabet-Path
App for learning to read in Arabic language
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>Quran Alphabet Path</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Amiri+Quran&family=Amiri:wght@400;700&family=PT+Sans:wght@400;700&family=PT+Serif:wght@400;700&display=swap">
<style>
:root{
  --bg:#EDF1EE; --surface:#FFFFFF; --surface2:#F5F8F6; --ink:#15251F; --muted:#586A63; --line:#D2DCD7;
  --green:#0F5A4E; --green-soft:#DCEBE5; --lapis:#2A4FA3; --lapis-soft:#E1E8F6; --brass:#A87414;
  --ok:#1D7648; --ok-soft:#DDF0E4; --bad:#B03A30; --bad-soft:#F7E1DE;
  --ar:'Amiri Quran','Amiri','Noto Naskh Arabic','Traditional Arabic',serif;
  --sans:'PT Sans','Noto Sans',system-ui,sans-serif; --serif:'PT Serif','Noto Serif',Georgia,serif;
}
@media (prefers-color-scheme: dark){:root:not([data-theme="light"]){
  --bg:#0D1613; --surface:#15221E; --surface2:#1A2924; --ink:#E4EEE9; --muted:#9BB0A8; --line:#2A3C36;
  --green:#5FC4AE; --green-soft:#1B3A33; --lapis:#8FAEF0; --lapis-soft:#1D2A4A; --brass:#E0AE4A;
  --ok:#6FD39B; --ok-soft:#1A3A29; --bad:#F08A80; --bad-soft:#412120; color-scheme:dark}}
:root[data-theme="dark"]{
  --bg:#0D1613; --surface:#15221E; --surface2:#1A2924; --ink:#E4EEE9; --muted:#9BB0A8; --line:#2A3C36;
  --green:#5FC4AE; --green-soft:#1B3A33; --lapis:#8FAEF0; --lapis-soft:#1D2A4A; --brass:#E0AE4A;
  --ok:#6FD39B; --ok-soft:#1A3A29; --bad:#F08A80; --bad-soft:#412120; color-scheme:dark}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:var(--sans);font-size:16px;line-height:1.5;
  padding-left:max(16px,env(safe-area-inset-left,0px));padding-right:max(16px,env(safe-area-inset-right,0px));padding-block:20px 40px}
.wrap{max-width:1120px;margin:0 auto}
h1,h2,h3{font-family:var(--serif);line-height:1.2;text-wrap:balance;margin:0}
h1{font-size:1.7rem} h2{font-size:1.35rem} h3{font-size:1.05rem}
p{margin:0 0 .7em}
.ar{font-family:var(--ar);direction:rtl;unicode-bidi:isolate;line-height:1.9}
header{display:flex;flex-wrap:wrap;gap:12px 28px;align-items:flex-end;justify-content:space-between;margin-bottom:14px}
header p{color:var(--muted);margin:4px 0 0}
.overall{min-width:220px;flex:0 1 280px}
.overall small,.note-small{color:var(--muted);display:block;margin-bottom:5px;font-variant-numeric:tabular-nums;font-size:.9rem}
.bar{height:8px;border-radius:4px;background:var(--line);overflow:hidden}
.bar i{display:block;height:100%;width:0;background:var(--brass);transition:width .4s}
.top{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:16px}
.top button{font:inherit;font-weight:700;background:var(--surface);border:1px solid var(--line);border-radius:999px;color:var(--ink);padding:7px 14px;cursor:pointer}
.top button[aria-current="true"]{background:var(--green);border-color:var(--green);color:var(--bg)}
.shell{display:grid;grid-template-columns:260px minmax(0,1fr);gap:20px;align-items:start}
nav ol{list-style:none;margin:0;padding:0;display:flex;flex-direction:column;gap:6px}
nav button{width:100%;display:flex;gap:10px;align-items:center;text-align:left;padding:9px 10px;background:var(--surface);
  border:1px solid var(--line);border-radius:8px;color:var(--ink);font:inherit;cursor:pointer}
nav button:hover{border-color:var(--green)}
nav button[aria-current="true"]{border-color:var(--green);background:var(--green-soft)}
.num{flex:none;width:28px;height:28px;border-radius:50%;display:grid;place-items:center;font-size:.85rem;font-weight:700;
  background:var(--surface2);border:1px solid var(--line);font-variant-numeric:tabular-nums}
.done .num{background:var(--green);color:var(--bg);border-color:var(--green)}
nav .t{min-width:0;display:flex;flex-direction:column;line-height:1.25}
nav .t b{font-weight:700;font-size:.95rem}
nav .t span{font-size:.8rem;color:var(--muted)}
main{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:20px;min-width:0}
.mhead{display:flex;flex-wrap:wrap;gap:6px 14px;justify-content:space-between;align-items:baseline;margin-bottom:14px}
.mhead small{color:var(--muted)}
.tabs{display:flex;gap:4px;border-bottom:1px solid var(--line);margin-bottom:18px;flex-wrap:wrap}
.tabs button{font:inherit;background:none;border:0;border-bottom:3px solid transparent;padding:8px 14px;color:var(--muted);cursor:pointer;font-weight:700}
.tabs button[aria-selected="true"]{color:var(--green);border-bottom-color:var(--green)}
button:focus-visible,input:focus-visible{outline:3px solid var(--lapis);outline-offset:2px}
.lead{color:var(--muted);max-width:65ch}
.lgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:12px;margin:14px 0}
.lcard{border:1px solid var(--line);border-radius:10px;padding:12px;background:var(--surface2);display:grid;gap:6px;min-width:0}
.lcard .big{font-size:3rem;text-align:center;color:var(--green);line-height:1.5}
.lcard .nm{display:flex;justify-content:space-between;gap:8px;font-weight:700;flex-wrap:wrap}
.lcard .nm span{color:var(--muted);font-weight:400}
.lcard p{font-size:.88rem;color:var(--muted);margin:0}
.forms{display:grid;grid-template-columns:repeat(4,1fr);gap:4px;text-align:center;border-top:1px dashed var(--line);padding-top:6px}
.forms div{font-size:.68rem;color:var(--muted);text-transform:uppercase;letter-spacing:.04em}
.forms span{display:block;font-size:1.7rem;color:var(--ink);line-height:1.6}
.forms .na{color:var(--line)}
.tbl{overflow-x:auto;margin:12px 0}
table{border-collapse:collapse;min-width:420px;width:100%}
th,td{border:1px solid var(--line);padding:8px 10px;text-align:left;vertical-align:middle}
th{background:var(--surface2);font-size:.8rem;text-transform:uppercase;letter-spacing:.04em;color:var(--muted)}
td .ar{font-size:1.9rem;display:inline-block}
.ex{display:flex;flex-wrap:wrap;gap:4px 16px;align-items:center;padding:8px 0;border-bottom:1px solid var(--line)}
.ex .ar{font-size:2rem;min-width:7rem}
.ex b{font-weight:700}
.ex span.m{color:var(--muted)}
.callout{background:var(--lapis-soft);border-radius:8px;padding:10px 14px;margin:12px 0;max-width:70ch}
.callout b{color:var(--lapis)}
.btn{font:inherit;font-weight:700;border-radius:8px;border:1px solid var(--lapis);background:var(--lapis);color:var(--bg);padding:9px 16px;cursor:pointer}
.btn.ghost{background:none;color:var(--lapis)}
.btn:hover{filter:brightness(1.1)}
.row{display:flex;flex-wrap:wrap;gap:10px;margin-top:16px;align-items:center}
.cards{display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:10px}
.card{min-height:130px;border:1px solid var(--line);border-radius:10px;background:var(--surface2);display:grid;place-items:center;padding:10px;
  text-align:center;cursor:pointer;font:inherit;color:var(--ink)}
.card .ar{font-size:2.6rem;color:var(--green)}
.card.flip{background:var(--green-soft);border-color:var(--green)}
.card small{color:var(--muted);display:block}
.qbox{max-width:640px}
.qmeta{display:flex;flex-wrap:wrap;justify-content:space-between;gap:4px 12px;color:var(--muted);font-size:.9rem;margin-bottom:8px;font-variant-numeric:tabular-nums}
.qprompt{font-size:1.05rem;margin-bottom:6px}
.qbig{font-size:4rem;text-align:center;color:var(--green);margin:6px 0 14px;line-height:1.5}
.opts{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}
.opt{font:inherit;font-size:1.05rem;padding:12px;border:1px solid var(--line);border-radius:8px;background:var(--surface);color:var(--ink);cursor:pointer;min-height:54px}
.opt.ar{font-family:var(--ar);font-size:2.2rem;line-height:1.5;padding:4px 12px}
.opt:hover:not(:disabled){border-color:var(--lapis)}
.opt.ok{background:var(--ok-soft);border-color:var(--ok);color:var(--ok)}
.opt.bad{background:var(--bad-soft);border-color:var(--bad);color:var(--bad)}
.opt:disabled{cursor:default}
.fb{min-height:1.6em;margin:12px 0 0;font-weight:700}
.fb.ok{color:var(--ok)} .fb.bad{color:var(--bad)}
.result .score{font-family:var(--serif);font-size:3rem;color:var(--green);font-variant-numeric:tabular-nums}
.reading{display:grid;gap:10px;margin:12px 0}
.line{display:flex;flex-wrap:wrap;justify-content:space-between;gap:6px 16px;align-items:center;padding:10px 12px;border:1px solid var(--line);border-radius:10px;background:var(--surface2)}
.line .ar{font-size:2.2rem}
.reveal{font:inherit;background:none;border:1px dashed var(--lapis);color:var(--lapis);border-radius:8px;padding:6px 12px;cursor:pointer}
.line .tr{color:var(--ink);font-style:italic;margin-left:8px}
.stats{display:grid;grid-template-columns:repeat(auto-fill,minmax(150px,1fr));gap:10px;margin:12px 0}
.stat{border:1px solid var(--line);border-radius:10px;padding:12px;background:var(--surface2)}
.stat b{display:block;font-size:1.4rem;font-variant-numeric:tabular-nums;color:var(--green)}
.stat span{font-size:.85rem;color:var(--muted)}
.week{display:flex;align-items:flex-end;gap:8px;height:110px;margin:12px 0 26px;padding:0 4px;border-bottom:1px solid var(--line)}
.week div{flex:1;background:var(--green-soft);border-radius:6px 6px 0 0;position:relative;min-height:3px}
.week div i{position:absolute;top:-20px;left:0;right:0;text-align:center;font-size:.75rem;color:var(--muted);font-style:normal;font-variant-numeric:tabular-nums}
.week div em{position:absolute;bottom:-22px;left:0;right:0;text-align:center;font-size:.72rem;color:var(--muted);font-style:normal}
.field{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.field label{color:var(--muted);font-size:.92rem}
input[type=number]{font:inherit;width:96px;padding:7px 9px;border:1px solid var(--line);border-radius:8px;background:var(--surface);color:var(--ink)}
.sub{font-family:var(--serif);font-size:1.05rem;margin:18px 0 6px}
.status{min-height:1.4em;color:var(--muted);font-size:.9rem;margin-top:8px}
.mrow{display:flex;justify-content:space-between;gap:10px;align-items:center;padding:8px 0;border-bottom:1px solid var(--line);flex-wrap:wrap}
.mrow .ar{font-size:1.8rem;min-width:4rem}
.mrow span.c{color:var(--muted);font-size:.9rem}
@media (max-width:760px){
  .shell{grid-template-columns:minmax(0,1fr)}
  nav ol{flex-direction:row;overflow-x:auto;padding-bottom:6px}
  nav li{flex:0 0 178px}
  nav p{display:none}
  main{padding:14px}
  .opts{grid-template-columns:1fr 1fr}
  .qbig{font-size:3.2rem}
  .week{gap:4px}
}
@media (prefers-reduced-motion:reduce){.bar i{transition:none}}
</style>
</head>
<body>
<div class="wrap">
  <header>
    <div>
      <h1>Quran Alphabet Path</h1>
      <p>From the first Arabic letter to reading a short surah, one module at a time.</p>
      <small class="note-small" id="soundNote"></small>
    </div>
    <div class="overall">
      <small id="barTxt"></small>
      <div class="bar" role="progressbar" aria-label="Course progress" aria-valuemin="0" aria-valuemax="11" id="barWrap"><i id="bar"></i></div>
    </div>
  </header>
  <div class="top" id="top" role="group" aria-label="Views"></div>
  <div class="shell">
    <nav aria-label="Modules">
      <ol id="rail"></ol>
    </nav>
    <main id="main" aria-live="polite"></main>
  </div>
</div>

<script>
(function(){
'use strict';
var FA='َ',KA='ِ',DA='ُ',SU='ْ',SH='ّ',FT='ً',KT='ٍ',DT='ٌ';
var J='‍';
var STORE_KEY='qap-v2';

/* ---------- Content ---------- */
var L=[
{c:'ا',n:'әлиф',lat:'ā',j:0,h:'Long ā. It holds vowels and is not a consonant by itself.'},
{c:'ب',n:'бә',lat:'b',j:1,h:'Like Kazakh б.'},
{c:'ت',n:'тә',lat:'t',j:1,h:'Like Kazakh т.'},
{c:'ث',n:'сә',lat:'th',j:1,h:'Like English "th" in "think". The tongue touches the teeth.'},
{c:'ج',n:'жим',lat:'j',j:1,h:'Like ж (or дж).'},
{c:'ح',n:'һа',lat:'ḥ',j:1,h:'Breathy һ from the throat, softer than خ.'},
{c:'خ',n:'хә',lat:'kh',j:1,h:'Like Kazakh х.'},
{c:'د',n:'дәл',lat:'d',j:0,h:'Like д. Does not join forward.'},
{c:'ذ',n:'зәл',lat:'dh',j:0,h:'Like English "th" in "this". Does not join forward.'},
{c:'ر',n:'ра',lat:'r',j:0,h:'Rolled р. Does not join forward.'},
{c:'ز',n:'зәй',lat:'z',j:0,h:'Like з. Does not join forward.'},
{c:'س',n:'сын',lat:'s',j:1,h:'Like с.'},
{c:'ش',n:'шын',lat:'sh',j:1,h:'Like ш.'},
{c:'ص',n:'сад',lat:'ṣ',j:1,h:'Heavy, full-mouth с.'},
{c:'ض',n:'дад',lat:'ḍ',j:1,h:'Heavy, full-mouth д.'},
{c:'ط',n:'тоы',lat:'ṭ',j:1,h:'Heavy, full-mouth т.'},
{c:'ظ',n:'зоы',lat:'ẓ',j:1,h:'Heavy, full-mouth з.'},
{c:'ع',n:'айн',lat:'ʿ',j:1,h:'Deep sound from the middle of the throat.'},
{c:'غ',n:'ғайн',lat:'gh',j:1,h:'Like Kazakh ғ.'},
{c:'ف',n:'фә',lat:'f',j:1,h:'Like ф.'},
{c:'ق',n:'қаф',lat:'q',j:1,h:'Deep қ from the back of the mouth.'},
{c:'ك',n:'кәф',lat:'k',j:1,h:'Like к.'},
{c:'ل',n:'лам',lat:'l',j:1,h:'Like л.'},
{c:'م',n:'мим',lat:'m',j:1,h:'Like м.'},
{c:'ن',n:'нун',lat:'n',j:1,h:'Like н.'},
{c:'ه',n:'һә',lat:'h',j:1,h:'Light breath, like Kazakh һ.'},
{c:'و',n:'уау',lat:'w',j:0,h:'Like у/w, also the long ū. Does not join forward.'},
{c:'ي',n:'йә',lat:'y',j:1,h:'Like й, also the long ī.'}
];
var GRP=[['ب','ت','ث','ن','ي'],['ج','ح','خ'],['د','ذ'],['ر','ز'],['س','ش'],['ص','ض'],['ط','ظ'],['ع','غ'],['ف','ق'],['ك','ل'],['م','ه','و'],['ا']];
var WORDS=[
{ar:'قَالَ',lat:'qāla',m:'he said'},{ar:'قِيلَ',lat:'qīla',m:'it was said'},{ar:'يَقُولُ',lat:'yaqūlu',m:'he says'},
{ar:'كِتَابٌ',lat:'kitābun',m:'a book'},{ar:'نُورٌ',lat:'nūrun',m:'light'},{ar:'بَابٌ',lat:'bābun',m:'a door'},
{ar:'رَبَّنَا',lat:'rabbanā',m:'our Lord'},{ar:'جَنَّةٌ',lat:'jannatun',m:'a garden'},{ar:'أُمٌّ',lat:'ummun',m:'a mother'},
{ar:'مُحَمَّدٌ',lat:'muḥammadun',m:'Muhammad'},{ar:'حَقٌّ',lat:'ḥaqqun',m:'truth'},
{ar:'كَتَبَ',lat:'kataba',m:'he wrote'},{ar:'قُلْ',lat:'qul',m:'say'},{ar:'عِلْمٌ',lat:'ʿilmun',m:'knowledge'}
];
var NOON=[
{ar:'مِنْ هَادٍ',lat:'min hādin',r:'Izhar',why:'Noon sakin followed by ه, a throat letter.'},
{ar:'مِنْ عِلْمٍ',lat:'min ʿilmin',r:'Izhar',why:'Noon sakin followed by ع, a throat letter.'},
{ar:'مَنْ يَقُولُ',lat:'man yaqūlu',r:'Idgham',why:'Noon sakin followed by ي merges into it.'},
{ar:'مِنْ رَبِّهِمْ',lat:'min rabbihim',r:'Idgham',why:'Noon sakin followed by ر merges into it.'},
{ar:'مِنْ مَالٍ',lat:'min mālin',r:'Idgham',why:'Noon sakin followed by م merges into it.'},
{ar:'سَمِيعٌ بَصِيرٌ',lat:'samīʿun baṣīrun',r:'Iqlab',why:'Tanween followed by ب turns into a hidden م.'},
{ar:'مِنْ بَعْدِ',lat:'min baʿdi',r:'Iqlab',why:'Noon sakin followed by ب turns into a hidden م.'},
{ar:'مِنْ قَبْلُ',lat:'min qablu',r:'Ikhfa',why:'Noon sakin followed by ق, one of the 15 hiding letters.'},
{ar:'كُنْتُمْ',lat:'kuntum',r:'Ikhfa',why:'Noon sakin followed by ت, one of the 15 hiding letters.'},
{ar:'أَنْتَ',lat:'anta',r:'Ikhfa',why:'Noon sakin followed by ت, one of the 15 hiding letters.'}
];
var MEEM=[
{ar:'هُمْ بِهِ',lat:'hum bihi',r:'Ikhfa shafawi',why:'Meem sakin followed by ب is hidden at the lips.'},
{ar:'لَهُمْ مَا',lat:'lahum mā',r:'Idgham shafawi',why:'Meem sakin followed by م merges into it.'},
{ar:'لَكُمْ مَا',lat:'lakum mā',r:'Idgham shafawi',why:'Meem sakin followed by م merges into it.'},
{ar:'أَمْ لَمْ',lat:'am lam',r:'Izhar shafawi',why:'Meem sakin followed by any other letter is read clearly.'},
{ar:'هُمْ فِيهَا',lat:'hum fīhā',r:'Izhar shafawi',why:'Meem sakin followed by any other letter is read clearly.'}
];
var SUN='تثدذرزسشصضطظلن'.split(''), MOON='ابجحخعغفقكمهوي'.split('');
var QAL='قطبجد'.split(''), HEAVY='خصضغطقظ'.split('');
var SURAH=[
{ar:'قُلْ هُوَ اللَّهُ أَحَدٌ',lat:'Qul huwa llāhu aḥad'},
{ar:'اللَّهُ الصَّمَدُ',lat:'Allāhu ṣ-ṣamad'},
{ar:'لَمْ يَلِدْ وَلَمْ يُولَدْ',lat:'Lam yalid wa-lam yūlad'},
{ar:'وَلَمْ يَكُنْ لَهُ كُفُوًا أَحَدٌ',lat:'Wa-lam yakun lahu kufuwan aḥad'}
];
var VOW=[{m:FA,s:'a'},{m:KA,s:'i'},{m:DA,s:'u'}];
var TAN=[{m:FT,s:'an'},{m:KT,s:'in'},{m:DT,s:'un'}];

function forms(l){return {iso:l.c,ini:l.j?l.c+J:null,med:l.j?J+l.c+J:null,fin:J+l.c}}
function nameOf(c){for(var i=0;i<L.length;i++)if(L[i].c===c)return L[i].n;return c}
function fam(c){for(var i=0;i<GRP.length;i++)if(GRP[i].indexOf(c)>=0)return GRP[i];return [c]}

/* ---------- Helpers ---------- */
function shuffle(a){a=a.slice();for(var i=a.length-1;i>0;i--){var j=Math.floor(Math.random()*(i+1));var t=a[i];a[i]=a[j];a[j]=t}return a}
function pick(a){return a[Math.floor(Math.random()*a.length)]}
function esc(s){return String(s==null?'':s).replace(/[&<>"']/g,function(c){return {'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]})}
function pct(t){return t&&t.q?Math.round(t.ok/t.q*100)+'%':'—'}
function keyOf(d){return d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0')}

/* Build one multiple-choice question. Callers pass distractors; fill() tops them up to three. */
function fill(wrong,pool,correct){var out=[];wrong.forEach(function(x){if(x!==correct&&out.indexOf(x)<0)out.push(x)});shuffle(pool).forEach(function(x){if(out.length<3&&x!==correct&&out.indexOf(x)<0)out.push(x)});return out}
function mkQ(o){
  var opts=[o.correct];o.wrong.forEach(function(x){if(x!==o.correct&&opts.indexOf(x)<0&&opts.length<4)opts.push(x)});
  return {prompt:o.prompt,big:o.big||'',ar:!!o.ar,correct:o.correct,opts:shuffle(opts),why:o.why,key:o.key,show:o.show||o.key,m:o.m}
}

/* ---------- Question generators: distractors come from look-alike letters and same-vowel or same-consonant variants ---------- */
var ALLC=L.map(function(x){return x.c});
var ALLN=L.map(function(x){return x.n});
function letterNameQ(a,b,m){
  var l=pick(L.slice(a,b));
  var wrong=shuffle(fam(l.c).filter(function(x){return x!==l.c})).slice(0,3).map(nameOf);
  wrong=fill(wrong,ALLN,l.n);
  return mkQ({prompt:'What is the name of this letter?',big:l.c,correct:l.n,wrong:wrong,
    why:l.c+' is called '+l.n+' ('+l.lat+'). '+l.h,key:'L:'+l.c,show:l.c,m:m});
}
function letterFromNameQ(a,b,m){
  var l=pick(L.slice(a,b));
  var wrong=shuffle(fam(l.c).filter(function(x){return x!==l.c})).slice(0,3);
  wrong=fill(wrong,ALLC,l.c);
  return mkQ({prompt:'Which letter is called «'+l.n+'»?',correct:l.c,ar:true,wrong:wrong,
    why:l.n+' is written '+l.c+'. '+l.h,key:'L:'+l.c,show:l.c,m:m});
}
function shapeQ(){
  var l=pick(L.slice(1));
  if(Math.random()<.3){
    var yes=l.j?'Yes':'No';
    return mkQ({prompt:'Does this letter join to the letter that comes after it?',big:l.c,correct:yes,wrong:[l.j?'No':'Yes'],
      why:l.j?l.c+' joins forward.':l.c+' is one of the six letters that never join forward: ا د ذ ر ز و.',key:'J:'+l.c,show:l.c,m:5});
  }
  var f=forms(l),keys=['iso','fin'].concat(l.j?['ini','med']:[]),k=pick(keys);
  var names={iso:'alone',ini:'at the start of a word',med:'in the middle of a word',fin:'at the end of a word'};
  var wrong=fill(shuffle(fam(l.c).filter(function(x){return x!==l.c})).slice(0,3),ALLC,l.c);
  return mkQ({prompt:'Which letter has this shape '+names[k]+'?',big:f[k],correct:l.c,ar:true,wrong:wrong,
    why:'This is the '+names[k]+' form of '+l.c+' ('+l.n+').',key:'S:'+l.c,show:f[k],m:5});
}
function vowelQ(){
  var l=pick(L.slice(1)),v=pick(VOW),correct=l.lat+v.s;
  var same=VOW.filter(function(x){return x!==v}).map(function(x){return l.lat+x.s});
  var o=pick(L.filter(function(x){return x.c!==l.c&&x.c!=='ا'&&x.lat!==l.lat}));
  var wrong=fill(same.concat([o.lat+v.s]),L.slice(1).map(function(x){return x.lat+pick(VOW).s}),correct);
  return mkQ({prompt:'How is this syllable read?',big:l.c+v.m,correct:correct,wrong:wrong,
    why:'The mark decides the vowel: fatha = a, kasra = i, damma = u.',key:'V:'+l.c,show:l.c+v.m,m:6});
}
function tanweenQ(){
  var l=pick(L.slice(1)),t=pick(TAN),correct=l.lat+t.s;
  var same=TAN.filter(function(x){return x!==t}).map(function(x){return l.lat+x.s});
  var o=pick(L.filter(function(x){return x.c!==l.c&&x.c!=='ا'&&x.lat!==l.lat}));
  var wrong=fill(same.concat([o.lat+t.s]),L.slice(1).map(function(x){return x.lat+pick(TAN).s}),correct);
  return mkQ({prompt:'Read this letter with tanween.',big:l.c+t.m,correct:correct,wrong:wrong,
    why:'Tanween adds an "n" sound: fathatan = an, kasratan = in, dammatan = un.',key:'T:'+l.c,show:l.c+t.m,m:7});
}
function sukunQ(){
  var a=pick(L.slice(1)),b=pick(L.slice(1)),v=pick(VOW),correct=a.lat+v.s+b.lat;
  var same=VOW.filter(function(x){return x!==v}).map(function(x){return a.lat+x.s+b.lat});
  var o=pick(L.slice(1).filter(function(x){return x.lat!==b.lat}));
  var wrong=fill(same.concat([a.lat+v.s+o.lat]),[],correct);
  return mkQ({prompt:'Sukun means no vowel. How is this read?',big:a.c+v.m+b.c+SU,correct:correct,wrong:wrong,
    why:'Read the first letter with its vowel, then stop on the second letter with no vowel.',key:'K:'+a.c+b.c,show:a.c+v.m+b.c+SU,m:7});
}
function wordQ(){
  var w=pick(WORDS);
  var wrong=shuffle(WORDS.filter(function(x){return x.lat!==w.lat})).slice(0,3).map(function(x){return x.ar});
  return mkQ({prompt:'Which word is read «'+w.lat+'»?',correct:w.ar,ar:true,wrong:wrong,
    why:w.lat+' means "'+w.m+'". '+(w.ar.indexOf(SH)>=0?'The letter with shadda is read twice.':'Long vowels are held for two beats.'),key:'W:'+w.lat,show:w.ar,m:8});
}
function sunMoonQ(){
  var sun=Math.random()<.5,group=sun?SUN:MOON,other=sun?MOON:SUN;
  var c=pick(group),wrong=shuffle(other).slice(0,3);
  return mkQ({prompt:'Which of these letters is a '+(sun?'SUN':'MOON')+' letter (after ال)?',correct:c,ar:true,wrong:wrong,
    why:sun?'After ال, the lam of ال is not pronounced and the sun letter is doubled.':'After ال, the lam is pronounced clearly before a moon letter.',key:'SM:'+c+(sun?'s':'m'),show:c,m:9});
}
function qalqalaQ(){
  var q=pick(QAL),others=shuffle(L.map(function(x){return x.c}).filter(function(c){return QAL.indexOf(c)<0&&c!=='ا'})).slice(0,3);
  return mkQ({prompt:'Which of these is a qalqala letter (it bounces)?',correct:q,ar:true,wrong:others,
    why:'The qalqala letters are ق ط ب ج د ("qutbu jadin"). They bounce when they have sukun.',key:'Q:'+q,show:q,m:9});
}
function heavyQ(){
  var h=pick(HEAVY),others=shuffle(L.map(function(x){return x.c}).filter(function(c){return HEAVY.indexOf(c)<0&&c!=='ا'})).slice(0,3);
  return mkQ({prompt:'Which of these is a heavy letter (read with a full mouth)?',correct:h,ar:true,wrong:others,
    why:'Heavy letters are خ ص ض غ ط ق ظ. They are read with a full mouth.',key:'H:'+h,show:h,m:9});
}
function noonQ(){
  var e=pick(NOON),rules=['Izhar','Idgham','Iqlab','Ikhfa'];
  return mkQ({prompt:'Which rule applies to the noon sakin or tanween here?',big:e.ar,correct:e.r,wrong:rules.filter(function(r){return r!==e.r}),
    why:e.lat+': '+e.why,key:'N:'+e.ar,show:e.ar,m:10});
}
function meemQ(){
  var e=pick(MEEM),rules=['Ikhfa shafawi','Idgham shafawi','Izhar shafawi','Izhar','Idgham','Iqlab'];
  return mkQ({prompt:'Which rule applies to the meem sakin here?',big:e.ar,correct:e.r,wrong:shuffle(rules.filter(function(r){return r!==e.r})).slice(0,3),
    why:e.lat+': '+e.why,key:'M:'+e.ar,show:e.ar,m:11});
}
var GEN={
 1:function(){return Math.random()<.5?letterNameQ(0,7,1):letterFromNameQ(0,7,1)},
 2:function(){return Math.random()<.5?letterNameQ(7,14,2):letterFromNameQ(7,14,2)},
 3:function(){return Math.random()<.5?letterNameQ(14,21,3):letterFromNameQ(14,21,3)},
 4:function(){return Math.random()<.5?letterNameQ(21,28,4):letterFromNameQ(21,28,4)},
 5:shapeQ, 6:vowelQ, 7:function(){return Math.random()<.5?tanweenQ():sukunQ()}, 8:wordQ,
 9:function(){var r=Math.random();return r<.4?sunMoonQ():r<.7?qalqalaQ():heavyQ()},
 10:noonQ, 11:function(){return Math.random()<.6?meemQ():noonQ()}
};

/*TEST_EXPORT*/

/* ---------- Lessons ---------- */
function ex(ar,lat,m){return '<div class="ex"><span class="ar">'+ar+'</span><b>'+esc(lat)+'</b><span class="m">'+esc(m)+'</span></div>'}
function cell(ar){return '<td><span class="ar">'+ar+'</span></td>'}
var M=[
{id:1,t:'Letters ا to خ',s:'Letters 1–7',kind:'letters',a:0,b:7},
{id:2,t:'Letters د to ص',s:'Letters 8–14',kind:'letters',a:7,b:14},
{id:3,t:'Letters ض to ق',s:'Letters 15–21',kind:'letters',a:14,b:21},
{id:4,t:'Letters ك to ي',s:'Letters 22–28',kind:'letters',a:21,b:28},
{id:5,t:'Letter shapes',s:'Joining and forms',kind:'x',
 teach:function(){
  var rows=L.map(function(l){var f=forms(l);
    return '<tr><td><b>'+l.n+'</b></td>'+cell(f.iso)+(f.ini?cell(f.ini):'<td>—</td>')+(f.med?cell(f.med):'<td>—</td>')+cell(f.fin)+'<td>'+(l.j?'Yes':'No')+'</td></tr>'}).join('');
  return '<p class="lead">Arabic is written right to left and letters join. Each letter changes shape by position: alone, at the start, in the middle, at the end.</p>'+
  '<div class="callout"><b>Six letters never join forward:</b> <span class="ar" style="font-size:1.6rem">ا د ذ ر ز و</span>. A gap always follows them, even inside a word.</div>'+
  '<div class="tbl"><table><thead><tr><th>Letter</th><th>Alone</th><th>Start</th><th>Middle</th><th>End</th><th>Joins forward</th></tr></thead><tbody>'+rows+'</tbody></table></div>';
 },
 cards:function(){return L.slice(1).map(function(l){var f=forms(l);return {f:'<span class="ar">'+f.iso+'</span>',b:'<b>'+l.n+'</b><small>'+(l.j?'Joins forward':'Does not join forward')+'</small>',say:l.c+FA}})}},
{id:6,t:'Three short vowels',s:'Fatha, kasra, damma',kind:'x',
 teach:function(){
  var rows=[1,2,3,4,5,6].map(function(i){var l=L[i];return '<tr><td><b>'+l.n+'</b></td>'+cell(l.c+FA)+cell(l.c+KA)+cell(l.c+DA)+'<td>'+esc(l.lat)+'a · '+esc(l.lat)+'i · '+esc(l.lat)+'u</td></tr>'}).join('');
  return '<p class="lead">Arabic letters are consonants. Small marks (harakat) above or below them add the short vowels.</p>'+
  '<div class="tbl"><table><thead><tr><th>Mark</th><th>Name</th><th>Sound</th><th>On a letter</th></tr></thead><tbody>'+
  '<tr><td><span class="ar">'+FA+'</span></td><td>Fatha</td><td>a (short, like а)</td>'+cell('بَ')+'</tr>'+
  '<tr><td><span class="ar">'+KA+'</span></td><td>Kasra</td><td>i (short, like і)</td>'+cell('بِ')+'</tr>'+
  '<tr><td><span class="ar">'+DA+'</span></td><td>Damma</td><td>u (short, like ұ)</td>'+cell('بُ')+'</tr></tbody></table></div>'+
  '<h3>Practice with six letters</h3><div class="tbl"><table><thead><tr><th>Letter</th><th>Fatha</th><th>Kasra</th><th>Damma</th><th>Reading</th></tr></thead><tbody>'+rows+'</tbody></table></div>'+
  '<h3>First words</h3>'+ex('كَتَبَ','kataba','he wrote')+ex('عِلْمٌ','ʿilmun','knowledge')+ex('قُلْ','qul','say')},
 cards:function(){var o=[];[1,2,3,11].forEach(function(i){VOW.forEach(function(v){o.push({f:'<span class="ar">'+L[i].c+v.m+'</span>',b:'<b>'+esc(L[i].lat+v.s)+'</b>',say:L[i].c+v.m})})});return o}},
{id:7,t:'Tanween and sukun',s:'Double marks, no vowel',kind:'x',
 teach:function(){
  return '<p class="lead">Tanween is a doubled vowel mark at the end of a word. It adds an "n" sound. Sukun is a small circle meaning the letter has no vowel.</p>'+
  '<div class="tbl"><table><thead><tr><th>Mark</th><th>Name</th><th>Sound</th><th>Example</th></tr></thead><tbody>'+
  '<tr><td><span class="ar">'+FT+'</span></td><td>Fathatan</td><td>an</td>'+cell('بًا')+'</tr>'+
  '<tr><td><span class="ar">'+KT+'</span></td><td>Kasratan</td><td>in</td>'+cell('بٍ')+'</tr>'+
  '<tr><td><span class="ar">'+DT+'</span></td><td>Dammatan</td><td>un</td>'+cell('بٌ')+'</tr>'+
  '<tr><td><span class="ar">'+SU+'</span></td><td>Sukun</td><td>stop, no vowel</td>'+cell('بَتْ')+'</tr></tbody></table></div>'+
  '<h3>Examples</h3>'+ex('كِتَابٌ','kitābun','a book')+ex('قَلَمٌ','qalamun','a pen')+ex('مِنْ','min','from')+ex('هَلْ','hal','is it? (question word)')},
 cards:function(){return [
  {f:'<span class="ar">بً</span>',b:'<b>ban</b><small>fathatan</small>',say:'بً'},{f:'<span class="ar">بٍ</span>',b:'<b>bin</b><small>kasratan</small>',say:'بٍ'},
  {f:'<span class="ar">بٌ</span>',b:'<b>bun</b><small>dammatan</small>',say:'بٌ'},{f:'<span class="ar">بَتْ</span>',b:'<b>bat</b><small>sukun on ت</small>',say:'بَتْ'},
  {f:'<span class="ar">مِنْ</span>',b:'<b>min</b>',say:'مِنْ'},{f:'<span class="ar">هَلْ</span>',b:'<b>hal</b>',say:'هَلْ'}]}},
{id:8,t:'Shadda and long vowels',s:'Doubling and madd',kind:'x',
 teach:function(){
  return '<h3>Shadda <span class="ar" style="font-size:1.6rem">'+SH+'</span></h3><p class="lead">Shadda doubles a letter: read it twice, first closed (sukun), then with its vowel.</p>'+
  WORDS.slice(6,11).map(function(w){return ex(w.ar,w.lat,w.m)}).join('')+
  '<h3 style="margin-top:20px">Madd: long vowels</h3><p class="lead">Three letters stretch a vowel to about two beats when they follow a matching vowel mark.</p>'+
  '<div class="tbl"><table><thead><tr><th>Pattern</th><th>Long sound</th><th>Example</th></tr></thead><tbody>'+
  '<tr><td>Fatha + ا</td><td>ā</td>'+cell('بَا')+'</tr>'+
  '<tr><td>Kasra + ي (no vowel)</td><td>ī</td>'+cell('بِي')+'</tr>'+
  '<tr><td>Damma + و (no vowel)</td><td>ū</td>'+cell('بُو')+'</tr></tbody></table></div>'+
  WORDS.slice(0,6).map(function(w){return ex(w.ar,w.lat,w.m)}).join('')},
 cards:function(){return WORDS.slice(0,11).map(function(w){return {f:'<span class="ar">'+w.ar+'</span>',b:'<b>'+esc(w.lat)+'</b><small>'+esc(w.m)+'</small>',say:w.ar}})}},
{id:9,t:'Sun, moon, heavy',s:'Lam, qalqala, heavy letters',kind:'x',
 teach:function(){
  function row(a){return a.map(function(c){return '<span class="ar" style="font-size:1.9rem;margin:0 6px">'+c+'</span>'}).join('')}
  return '<p class="lead">Three sound rules every reader needs before the main tajweed rules.</p>'+
  '<h3>1. The article ال: sun and moon letters</h3>'+
  '<p>Before 14 "sun" letters the lam of ال is silent and the next letter is doubled. Before 14 "moon" letters the lam is read clearly.</p>'+
  '<p><b>Sun:</b> '+row(SUN)+'</p><p><b>Moon:</b> '+row(MOON)+'</p>'+
  ex('الشَّمْسُ','ash-shamsu','the sun (lam silent)')+ex('الْقَمَرُ','al-qamaru','the moon (lam read)')+
  '<h3 style="margin-top:20px">2. Qalqala: the bounce</h3><p>These five letters bounce slightly when they have sukun or end a stop: <span class="ar" style="font-size:1.8rem">قطب جد</span></p>'+
  '<h3 style="margin-top:20px">3. Heavy letters</h3><p>Seven letters are read with a full, raised mouth: <span class="ar" style="font-size:1.8rem">خص ضغط قظ</span>. All other letters are light.</p>'},
 cards:function(){return [
  {f:'<span class="ar">ال + ش</span>',b:'<b>Sun</b><small>lam silent</small>',say:'الشَّمْسُ'},{f:'<span class="ar">ال + ق</span>',b:'<b>Moon</b><small>lam read</small>',say:'الْقَمَرُ'},
  {f:'<span class="ar">قطب جد</span>',b:'<b>Qalqala</b><small>bouncing letters</small>',say:'قُطْبُ جَدَ'},{f:'<span class="ar">خص ضغط قظ</span>',b:'<b>Heavy</b><small>full-mouth letters</small>',say:'خَصَّ ضَغَطَ قَظَ'}]}},
{id:10,t:'Noon sakin rules',s:'Izhar, idgham, iqlab, ikhfa',kind:'x',
 teach:function(){
  return '<p class="lead">When a noun ends with tanween or a noon has sukun, its sound depends on the next letter. Four rules cover every case.</p>'+
  '<div class="tbl"><table><thead><tr><th>Rule</th><th>Meaning</th><th>Next letters</th><th>Example</th></tr></thead><tbody>'+
  '<tr><td><b>Izhar</b></td><td>Clear</td><td><span class="ar" style="font-size:1.5rem">ء هـ ع ح غ خ</span></td>'+cell('مِنْ هَادٍ')+'</tr>'+
  '<tr><td><b>Idgham</b></td><td>Merge</td><td><span class="ar" style="font-size:1.5rem">ي ر م ل و ن</span></td>'+cell('مَنْ يَقُولُ')+'</tr>'+
  '<tr><td><b>Iqlab</b></td><td>Change to م</td><td><span class="ar" style="font-size:1.5rem">ب</span></td>'+cell('مِنْ بَعْدِ')+'</tr>'+
  '<tr><td><b>Ikhfa</b></td><td>Hide</td><td>the other 15 letters</td>'+cell('مِنْ قَبْلُ')+'</tr></tbody></table></div>'+
  '<div class="callout"><b>Tip:</b> Idgham before ي ن م و carries a nasal hum (ghunna). Before ل and ر it has none. Ikhfa has a nasal hum too.</div>'+
  NOON.map(function(e){return ex(e.ar,e.lat,e.r)}).join('')},
 cards:function(){return NOON.map(function(e){return {f:'<span class="ar">'+e.ar+'</span>',b:'<b>'+e.r+'</b><small>'+esc(e.lat)+'</small>',say:e.ar}})}},
{id:11,t:'Meem sakin and reading',s:'Last rules, then Surah al-Ikhlas',kind:'x',
 teach:function(){
  return '<p class="lead">Meem sakin has three rules, depending on the letter after it.</p>'+
  '<div class="tbl"><table><thead><tr><th>Rule</th><th>Next letter</th><th>What happens</th><th>Example</th></tr></thead><tbody>'+
  '<tr><td><b>Ikhfa shafawi</b></td><td><span class="ar" style="font-size:1.5rem">ب</span></td><td>Hidden at the lips with a hum</td>'+cell('هُمْ بِهِ')+'</tr>'+
  '<tr><td><b>Idgham shafawi</b></td><td><span class="ar" style="font-size:1.5rem">م</span></td><td>Two meems merge, with a hum</td>'+cell('لَهُمْ مَا')+'</tr>'+
  '<tr><td><b>Izhar shafawi</b></td><td>all others</td><td>Read clearly</td>'+cell('أَمْ لَمْ')+'</tr></tbody></table></div>'+
  '<h3 style="margin-top:20px">Reading practice: Surah al-Ikhlas</h3><p>Listen, read each line aloud, then show the reading to check.</p>'+
  '<div class="reading">'+SURAH.map(function(s,i){return '<div class="line"><span class="ar">'+s.ar+'</span><span><button class="btn ghost" data-say="'+s.ar+'">Listen</button> <button class="reveal" data-i="'+i+'">Show reading</button><span class="tr" hidden id="tr'+i+'">'+esc(s.lat)+'</span></span></div>'}).join('')+'</div>'},
 cards:function(){return MEEM.map(function(e){return {f:'<span class="ar">'+e.ar+'</span>',b:'<b>'+e.r+'</b><small>'+esc(e.lat)+'</small>',say:e.ar}}).concat(SURAH.map(function(s){return {f:'<span class="ar" style="font-size:1.6rem">'+s.ar+'</span>',b:'<b>'+esc(s.lat)+'</b>',say:s.ar}}))}}
];

/* ---------- Progress (saved in this browser only) ---------- */
function fresh(){return {v:2,cur:1,mods:{},goal:{min:15,q:20},mistakes:{},days:{},tot:{q:0,ok:0}}}
function norm(x){var s=fresh();if(x&&typeof x==='object'){Object.keys(s).forEach(function(k){if(x[k]!==undefined&&x[k]!==null)s[k]=x[k]})}s.cur=Math.min(Math.max(parseInt(s.cur,10)||1,1),11);return s}
var S=fresh();
try{var raw=localStorage.getItem(STORE_KEY);if(raw)S=norm(JSON.parse(raw))}catch(e){}

var view='course',tab='learn',cur=S.cur,sess=null,lastAct=Date.now();

function day(k){k=k||keyOf(new Date());S.days[k]=S.days[k]||{min:0,q:0,ok:0};return S.days[k]}
function streak(){var d=new Date(),n=0;if(!(S.days[keyOf(d)]&&S.days[keyOf(d)].min>0))d.setDate(d.getDate()-1);
  while(S.days[keyOf(d)]&&S.days[keyOf(d)].min>0){n++;d.setDate(d.getDate()-1)}return n}
function week(){var o=[];for(var i=6;i>=0;i--){var d=new Date();d.setDate(d.getDate()-i);var e=S.days[keyOf(d)];o.push({min:e?Math.round(e.min):0,d:d})}return o}
function passed(){var n=0;M.forEach(function(m){if(S.mods[m.id]&&S.mods[m.id].done)n++});return n}
function topMistakes(n){return Object.keys(S.mistakes).map(function(k){return {show:S.mistakes[k].show,n:S.mistakes[k].n}}).sort(function(a,b){return b.n-a.n}).slice(0,n)}
function persist(){try{localStorage.setItem(STORE_KEY,JSON.stringify(S))}catch(e){}}

/* ---------- Sound (uses the device's Arabic voice until recorded audio is added) ---------- */
function arVoice(){try{var vs=speechSynthesis.getVoices()||[];for(var i=0;i<vs.length;i++){if(/^ar/i.test(vs[i].lang))return vs[i]}}catch(e){}return null}
function updateSoundNote(){
  var el=document.getElementById('soundNote');if(!el)return;
  if(!('speechSynthesis' in window)){el.textContent='This browser cannot play sound, so letters are shown without audio.';return}
  var v=arVoice();
  el.textContent=v?'Arabic voice found on this device ('+v.name+'), so Listen should speak.':'No Arabic voice is installed on this device, so Listen may be silent. Add an Arabic voice in the device speech settings, then reload the page.';
}
function say(t){
  if(!('speechSynthesis' in window)){updateSoundNote();return}
  try{speechSynthesis.cancel();var u=new SpeechSynthesisUtterance(t);u.lang='ar';var v=arVoice();if(v)u.voice=v;u.rate=0.7;speechSynthesis.speak(u)}catch(e){}
  updateSoundNote();
}

/* ---------- Rendering ---------- */
function renderTop(){
  var b=[['course','Course'],['dash','My dashboard']],h='';
  b.forEach(function(x){h+='<button data-view="'+x[0]+'" aria-current="'+(view===x[0])+'">'+x[1]+'</button>'});
  document.getElementById('top').innerHTML=h;
}
function renderRail(){
  var done=passed();
  document.getElementById('rail').innerHTML=M.map(function(m){var p=S.mods[m.id]||{};var d=!!p.done;
    return '<li><button class="'+(d?'done':'')+'" data-m="'+m.id+'"'+(m.id===cur&&view==='course'?' aria-current="true"':'')+'><span class="num">'+(d?'✓':m.id)+'</span><span class="t"><b>'+m.t+'</b><span>'+(p.best!=null?'Best '+p.best+'/10':m.s)+'</span></span></button></li>'}).join('');
  document.getElementById('bar').style.width=(done/M.length*100)+'%';
  document.getElementById('barWrap').setAttribute('aria-valuenow',done);
  document.getElementById('barTxt').textContent=done+' of '+M.length+' modules passed';
}
function renderAll(){renderTop();renderRail();renderMain();updateSoundNote()}
function renderMain(){
  document.getElementById('main').innerHTML=view==='dash'?dashHtml():courseHtml();
  renderTop();
  if(view==='course'&&(tab==='drill'||tab==='quiz')){
    var want=tab==='quiz'?'quiz':'drill';
    if(!sess||sess.tab!==want)startSess(want);
    drawQ();
  }
}
function courseHtml(){
  var m=M[cur-1];
  var tabs=[['learn','Learn'],['cards','Cards'],['drill','Drill'],['quiz','Quiz']],th='';
  tabs.forEach(function(x){th+='<button role="tab" data-t="'+x[0]+'" aria-selected="'+(tab===x[0])+'">'+x[1]+'</button>'});
  var body='';
  if(tab==='learn'){
    body=(m.kind==='letters'?lettersLesson(m):m.teach())+
    '<div class="row"><button class="btn" data-t="cards">Practice with cards</button><button class="btn ghost" data-t="quiz">Go to quiz</button></div>';
  } else if(tab==='cards'){
    var items=m.kind==='letters'?lettersCards(m):m.cards();
    body='<p class="lead">Tap a card to flip it. The letter or word is read aloud when the card turns.</p><div class="cards">'+
      items.map(function(c){return '<button class="card" data-flip="1" data-say="'+esc(c.say)+'"><span class="front">'+c.f+'</span><span class="back" hidden>'+c.b+'</span></button>'}).join('')+'</div>';
  } else {
    body='<div id="qwrap"></div>';
  }
  return '<div class="mhead"><h2>'+m.id+'. '+m.t+'</h2><small>'+m.s+'</small></div><div class="tabs" role="tablist">'+th+'</div>'+body;
}
function lettersLesson(m){
  var cards=L.slice(m.a,m.b).map(function(l){var f=forms(l);
    function fm(k,lab){return '<div>'+lab+'<span class="ar'+(f[k]?'':' na')+'">'+(f[k]||'–')+'</span></div>'}
    return '<div class="lcard"><div class="ar big">'+l.c+'</div><div class="nm"><b>'+l.n+'</b><span>'+esc(l.lat)+'</span></div><p>'+l.h+'</p>'+
      '<div class="forms">'+fm('iso','Alone')+fm('ini','Start')+fm('med','Mid')+fm('fin','End')+'</div>'+
      '<div><button class="btn ghost" data-say="'+l.c+FA+'">Listen</button></div></div>'}).join('');
  return '<p class="lead">Learn the shape, the name and the sound together. Press Listen, then say the letter aloud.</p><div class="lgrid">'+cards+'</div>';
}
function lettersCards(m){return L.slice(m.a,m.b).map(function(l){return {f:'<span class="ar">'+l.c+'</span>',b:'<b>'+l.n+'</b><small>'+esc(l.lat)+'</small>',say:l.c+FA}})}

/* ---------- Drill, quiz and mistake practice ---------- */
function startSess(mode){
  sess={mode:mode,tab:mode==='quiz'?'quiz':'drill',n:0,ok:0,done:0,streak:0,recent:[],q:null,answered:false};
  newQ();
}
function mistakeModules(){var s={};Object.keys(S.mistakes).forEach(function(k){var r=S.mistakes[k];if(r.m)s[r.m]=1});return Object.keys(s).map(Number)}
function genMixed(){
  var m=1+Math.floor(Math.random()*cur);
  var mk=mistakeModules();
  if(mk.length&&Math.random()<.35)m=pick(mk);
  return GEN[m]();
}
function genMistake(){
  var keys=Object.keys(S.mistakes);
  if(!keys.length)return genMixed();
  var total=keys.reduce(function(a,k){return a+S.mistakes[k].n},0),r=Math.random()*total,pk=keys[0];
  for(var i=0;i<keys.length;i++){r-=S.mistakes[keys[i]].n;if(r<=0){pk=keys[i];break}}
  return GEN[S.mistakes[pk].m||1]();
}
function newQ(){
  var q,tries=0;
  do{
    if(sess.mode==='quiz')q=GEN[cur]();
    else if(sess.mode==='mistakes')q=genMistake();
    else q=genMixed();
    tries++;
  }while(sess.recent.indexOf(q.key)>=0&&tries<25);
  sess.recent.push(q.key);if(sess.recent.length>6)sess.recent.shift();
  sess.q=q;sess.answered=false;sess.pickedIdx=null;
}
function drawQ(){
  var w=document.getElementById('qwrap');if(!w||!sess)return;
  var q=sess.q,meta;
  if(sess.mode==='quiz')meta='<span>Question '+(sess.n+1)+' of 10</span><span>Score '+sess.ok+'</span>';
  else if(sess.mode==='mistakes')meta='<span>Practising your mistakes</span><span>'+sess.ok+' / '+sess.done+' correct</span>';
  else meta='<span>Mixed review, no limit</span><span>Streak '+sess.streak+' · '+sess.ok+' / '+sess.done+' correct</span>';
  w.innerHTML='<div class="qbox"><div class="qmeta">'+meta+'</div><div class="qprompt">'+esc(q.prompt)+'</div>'+
    (q.big?'<div class="ar qbig">'+esc(q.big)+'</div>':'')+
    '<div class="opts">'+q.opts.map(function(o,i){return '<button class="opt'+(q.ar?' ar':'')+'" data-o="'+i+'">'+esc(o)+'</button>'}).join('')+'</div>'+
    '<p class="fb" id="fb" aria-live="polite"></p><div class="row" id="nx"></div></div>';
  if(sess.answered)showAnswer(sess.lastOk);
}
function answer(i){
  if(!sess||sess.answered)return;
  var q=sess.q,ok=q.opts[i]===q.correct;
  sess.answered=true;sess.lastOk=ok;sess.pickedIdx=i;sess.done++;
  if(ok){sess.ok++;sess.streak++}else sess.streak=0;
  var d=day();d.q++;if(ok)d.ok++;
  S.tot.q++;if(ok)S.tot.ok++;
  if(ok){var r=S.mistakes[q.key];if(r){r.n--;if(r.n<=0)delete S.mistakes[q.key]}}
  else{var rr=S.mistakes[q.key]||{show:q.show,m:q.m||cur,n:0};rr.n++;S.mistakes[q.key]=rr;var keys=Object.keys(S.mistakes);if(keys.length>150)delete S.mistakes[keys[0]]}
  persist();
  showAnswer(ok);
}
function showAnswer(ok){
  var q=sess.q;
  document.querySelectorAll('.opt').forEach(function(b,k){b.disabled=true;if(q.opts[k]===q.correct)b.classList.add('ok');else if(k===sess.pickedIdx)b.classList.add('bad')});
  var fb=document.getElementById('fb');if(fb){fb.className='fb '+(ok?'ok':'bad');fb.textContent=(ok?'Correct. ':'Not quite. ')+q.why}
  var nx=document.getElementById('nx');if(nx)nx.innerHTML='<button class="btn" data-next="1">Alhamdulillah</button>';
}
function nextStep(){
  if(!sess)return;
  sess.n++;
  if(sess.mode==='quiz'&&sess.n>=10)return finish();
  newQ();drawQ();
}
function finish(){
  var p=S.mods[cur]||{},s=sess.ok,pass=s>=8;
  p.best=p.best==null?s:Math.max(p.best,s);if(pass)p.done=true;S.mods[cur]=p;persist();
  var nxt=cur<M.length;
  document.getElementById('qwrap').innerHTML='<div class="qbox result"><div class="score">'+s+' / 10</div>'+
    '<p>'+(pass?'Module passed. '+(nxt?'The next module is ready.':'You have finished the course. Keep reading aloud every day.'):'You need 8 of 10 to pass. Review the lesson and the cards, then try again.')+'</p>'+
    '<div class="row">'+(pass&&nxt?'<button class="btn" data-m="'+(cur+1)+'">Next module</button>':'')+
    '<button class="btn '+(pass&&nxt?'ghost':'')+'" data-act="retryquiz">Retry quiz</button><button class="btn ghost" data-t="learn">Review lesson</button></div></div>';
  renderRail();
}

/* ---------- Dashboard ---------- */
function dashHtml(){
  var d=day(),wk=week(),maxM=Math.max(S.goal.min,1);
  wk.forEach(function(w){if(w.min>maxM)maxM=w.min});
  var mist=topMistakes(12);
  return '<div class="mhead"><h2>My dashboard</h2><small>Progress is saved in this browser</small></div>'+
  '<div class="stats">'+
   '<div class="stat"><b>'+Math.round(d.min)+' / '+S.goal.min+' min</b><span>Today</span></div>'+
   '<div class="stat"><b>'+d.q+' / '+S.goal.q+'</b><span>Questions today</span></div>'+
   '<div class="stat"><b>'+pct(S.tot)+'</b><span>Accuracy overall</span></div>'+
   '<div class="stat"><b>'+passed()+' / '+M.length+'</b><span>Modules passed</span></div>'+
   '<div class="stat"><b>'+streak()+' days</b><span>Study streak</span></div>'+
  '</div>'+
  '<h3 class="sub">Daily minimum</h3>'+
  '<div class="field"><label for="gMin">Minutes a day</label><input type="number" id="gMin" min="1" max="600" value="'+S.goal.min+'"><label for="gQ">Questions a day</label><input type="number" id="gQ" min="1" max="500" value="'+S.goal.q+'"><button class="btn" data-act="goal">Save minimum</button></div>'+
  '<h3 class="sub">Last 7 days (minutes)</h3>'+
  '<div class="week" aria-label="Minutes per day">'+wk.map(function(w){return '<div style="height:'+Math.max(3,Math.round(w.min/maxM*100))+'%"><i>'+w.min+'</i><em>'+w.d.getDate()+'</em></div>'}).join('')+'</div>'+
  '<h3 class="sub">Mistakes to review</h3>'+
  (mist.length?'<div>'+mist.map(function(x){return '<div class="mrow"><span class="ar">'+esc(x.show)+'</span><span class="c">missed '+x.n+' time'+(x.n>1?'s':'')+'</span></div>'}).join('')+'</div>'+
    '<div class="row"><button class="btn" data-act="mistakes">Practise my mistakes</button></div>':'<p class="lead">No mistakes to review yet. Missed answers appear here.</p>')+
  '<h3 class="sub">Reset</h3>'+
  '<div class="row"><button class="btn ghost" data-act="reset" id="resetBtn">Erase my progress</button></div>'+
  '<div class="status" id="status" aria-live="polite"></div>';
}

/* ---------- Actions ---------- */
function setStatus(m){var el=document.getElementById('status');if(el)el.textContent=m||''}
function act(t){
  var a=t.dataset.act;
  if(a==='goal'){
    var g=parseInt(document.getElementById('gMin').value,10),q=parseInt(document.getElementById('gQ').value,10);
    if(!(g>0&&g<=600)||!(q>0&&q<=500)){setStatus('Enter minutes from 1 to 600 and questions from 1 to 500.');return}
    S.goal={min:g,q:q};persist();renderMain();setStatus('Saved.');
  }
  else if(a==='mistakes'){view='course';tab='drill';sess=null;startSess('mistakes');renderAll()}
  else if(a==='retryquiz'){tab='quiz';startSess('quiz');renderAll()}
  else if(a==='reset'){
    var b=document.getElementById('resetBtn');
    if(!t.dataset.armed){t.dataset.armed='1';t.textContent='Click again to erase everything';setStatus('This removes all progress in this browser.');return}
    S=fresh();cur=1;persist();view='course';tab='learn';sess=null;renderAll();
  }
}
function flip(t){
  var back=t.querySelector('.back'),front=t.querySelector('.front');
  var show=back.hidden;back.hidden=!show;front.hidden=show;t.classList.toggle('flip',show);
  if(show&&t.dataset.say)say(t.dataset.say);
}

document.addEventListener('click',function(e){
  lastAct=Date.now();
  var t=e.target.closest('button');if(!t)return;
  if(t.dataset.view){view=t.dataset.view;renderAll();return}
  if(t.dataset.m){cur=parseInt(t.dataset.m,10);S.cur=cur;view='course';tab='learn';sess=null;persist();renderAll();window.scrollTo(0,0);return}
  if(t.dataset.t){tab=t.dataset.t;view='course';renderMain();return}
  if(t.dataset.o!=null){answer(parseInt(t.dataset.o,10));return}
  if(t.dataset.next){nextStep();return}
  if(t.dataset.flip!=null){flip(t);return}
  if(t.dataset.say){say(t.dataset.say);return}
  if(t.dataset.act){act(t);return}
  if(t.classList.contains('reveal')){var el=document.getElementById('tr'+t.dataset.i);if(el)el.hidden=false;t.hidden=true;return}
});

/* Minutes count only while the person is working in a course tab. */
setInterval(function(){
  if(view==='course'&&['learn','cards','drill','quiz'].indexOf(tab)>=0&&document.visibilityState!=='hidden'&&Date.now()-lastAct<180000){
    day().min+=0.5;persist();
  }
},30000);

/* ---------- Start ---------- */
renderAll();
try{if('speechSynthesis' in window)speechSynthesis.onvoiceschanged=updateSoundNote}catch(e){}
})();
</script>
</body>
</html>
