<html lang="ja"><head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>中3理科・物理クイズ</title>
<style>
  body{
    font-family: "Noto Sans JP", system-ui, sans-serif;
    background: #f3f4f6;
    margin: 0;
    padding: 24px;
    color: #111827;
  }
  .container{max-width:800px;margin:0 auto;}
  .card{background:#fff;padding:16px;margin-bottom:12px;border-radius:10px;box-shadow:0 2px 8px rgba(0,0,0,0.1);}
  h1{margin-bottom:10px;}
  .btn{background:#2563eb;color:#fff;border:none;padding:8px 12px;border-radius:6px;cursor:pointer;}
  .btn.ghost{background:#fff;color:#2563eb;border:1px solid #2563eb;}
  .hidden-text{
    cursor:pointer;
    background:rgba(0,0,0,0.05);
    border-radius:6px;
    padding:2px 6px;
  }
  .hidden-text[data-revealed="false"]{
    color:transparent;
    text-shadow:0 0 8px rgba(0,0,0,0.5);
  }
  input[type="text"]{padding:6px;border-radius:4px;border:1px solid #ccc;}
  .feedback{margin-left:8px;font-weight:700;}
  .score{font-weight:700;}
</style>
</head>
<body>
  <div class="container">
    <h1>中3理科・物理クイズ！</h1>
    <p>🔹 隠れている文字をタップして表示！<br>
       🔹 答えを入力して採点してみよう！</p>
 
    <div id="quiz"><div class="card" data-qid="q1">
      <h3>第1問</h3>
      <p>1Nの力で2m動かしたときの仕事は？（単位も）<br>→ <span class="hidden-text" data-key="ans1">公式：仕事＝力×距離</span></p>
      <p><input type="text" id="input-q1" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q1')">採点</button>
      <span class="feedback" id="fb-q1"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q1')">解説表示</button></p>
      <p id="sol-q1" style="display:none">1×2=2J（ジュール）！</p>
      <p><small>ヒント：仕事＝力×距離！</small></p>
    </div><div class="card" data-qid="q2">
      <h3>第2問</h3>
      <p>100Nの力で1mの高さまで持ち上げた時の仕事は？</p>
      <p><input type="text" id="input-q2" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q2')">採点</button>
      <span class="feedback" id="fb-q2"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q2')">解説表示</button></p>
      <p id="sol-q2" style="display: none;">100×1＝100J！</p>
      <p><small>ヒント：仕事＝力×距離！</small></p>
    </div><div class="card" data-qid="q3">
      <h3>第3問</h3>
      <p>1Wの仕事を1秒間に行うエネルギーを何という？<br>→ <span class="hidden-text" data-key="ans2">単位：J/s</span></p>
      <p><input type="text" id="input-q3" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q3')">採点</button>
      <span class="feedback" id="fb-q3"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q3')">解説表示</button></p>
      <p id="sol-q3" style="display:none">仕事率の単位はW（ワット）！</p>
      <p><small>ヒント：仕事率＝仕事÷時間！</small></p>
    </div><div class="card" data-qid="q4">
      <h3>第4問</h3>
      <p>電流が2A、電圧が6Vのとき、抵抗値はいくつ？</p>
      <p><input type="text" id="input-q4" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q4')">採点</button>
      <span class="feedback" id="fb-q4"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q4')">解説表示</button></p>
      <p id="sol-q4" style="display:none">6＝2×R → R＝3Ω！</p>
      <p><small>ヒント：オームの法則 V＝IR！</small></p>
    </div><div class="card" data-qid="q5">
      <h3>第5問</h3>
      <p>1Ωの抵抗に1Aの電流を1秒流したときの電気量は？</p>
      <p><input type="text" id="input-q5" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q5')">採点</button>
      <span class="feedback" id="fb-q5"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q5')">解説表示</button></p>
      <p id="sol-q5" style="display:none">1×1＝1クーロン！</p>
      <p><small>ヒント：電気量＝電流×時間！</small></p>
    </div><div class="card" data-qid="q6">
      <h3>第6問</h3>
      <p>電力P＝V×I。このとき、6V・2Aのときの電力は？</p>
      <p><input type="text" id="input-q6" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q6')">採点</button>
      <span class="feedback" id="fb-q6"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q6')">解説表示</button></p>
      <p id="sol-q6" style="display:none">6×2＝12W（ワット）！</p>
      <p><small>ヒント：P＝VI！</small></p>
    </div><div class="card" data-qid="q7">
      <h3>第7問</h3>
      <p>滑車を使っても仕事の大きさは変わらない理由は？<br><span class="hidden-text" data-key="ans3">力が小さくなった分、距離が長くなるから</span></p>
      <p><input type="text" id="input-q7" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q7')">採点</button>
      <span class="feedback" id="fb-q7"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q7')">解説表示</button></p>
      <p id="sol-q7" style="display:none">力が半分になると動かす距離は2倍になる→仕事（力×距離）は同じ！</p>
      <p><small>ヒント：滑車の原理！</small></p>
    </div><div class="card" data-qid="q8">
      <h3>第8問</h3>
      <p>位置エネルギーの公式は？<br>（ヒント：重力・高さ）</p>
      <p><input type="text" id="input-q8" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q8')">採点</button>
      <span class="feedback" id="fb-q8"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q8')">解説表示</button></p>
      <p id="sol-q8" style="display:none">位置エネルギー＝mgh（質量×重力加速度×高さ）！</p>
      <p><small>ヒント：重力の記号はg！</small></p>
    </div><div class="card" data-qid="q9">
      <h3>第9問</h3>
      <p>運動エネルギーの公式は？</p>
      <p><input type="text" id="input-q9" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q9')">採点</button>
      <span class="feedback" id="fb-q9"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q9')">解説表示</button></p>
      <p id="sol-q9" style="display:none">運動エネルギー＝1/2mv²！</p>
      <p><small>ヒント：質量×速度²×1/2！</small></p>
    </div><div class="card" data-qid="q10">
      <h3>第10問</h3>
      <p>エネルギー保存の法則とは？<br><span class="hidden-text" data-key="ans4" data-revealed="false">エネルギーの総量は変わらない</span></p>
      <p><input type="text" id="input-q10" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('q10')">採点</button>
      <span class="feedback" id="fb-q10"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('q10')">解説表示</button></p>
      <p id="sol-q10" style="display:none">形は変わっても、全体のエネルギーの量は一定に保たれる！</p>
      <p><small>ヒント：運動・位置エネルギーの関係！</small></p>
    </div></div>
    <div class="card">
      <span class="score" id="score">0 / 10</span>
    </div>
 
    <p>このページはあなたのPCやスマホで開けるローカルHTMLです！<br>
    <strong>GitHub Pages</strong>や<strong>Netlify</strong>で公開すればURLでアクセスできます！</p>
  </div>
 
<script>
const QUESTIONS = [
  {
    id:"q1",
    prompt:"1Nの力で2m動かしたときの仕事は？（単位も）<br>→ <span class='hidden-text' data-key='ans1'>公式：仕事＝力×距離</span>",
    answer:"2j",
    hint:"仕事＝力×距離！",
    solution:"1×2=2J（ジュール）！"
  },
  {
    id:"q2",
    prompt:"100Nの力で1mの高さまで持ち上げた時の仕事は？",
    answer:"100j",
    hint:"仕事＝力×距離！",
    solution:"100×1＝100J！"
  },
  {
    id:"q3",
    prompt:"1Wの仕事を1秒間に行うエネルギーを何という？<br>→ <span class='hidden-text' data-key='ans2'>単位：J/s</span>",
    answer:"ワット",
    hint:"仕事率＝仕事÷時間！",
    solution:"仕事率の単位はW（ワット）！"
  },
  {
    id:"q4",
    prompt:"電流が2A、電圧が6Vのとき、抵抗値はいくつ？",
    answer:"3ω",
    hint:"オームの法則 V＝IR！",
    solution:"6＝2×R → R＝3Ω！"
  },
  {
    id:"q5",
    prompt:"1Ωの抵抗に1Aの電流を1秒流したときの電気量は？",
    answer:"1c",
    hint:"電気量＝電流×時間！",
    solution:"1×1＝1クーロン！"
  },
  {
    id:"q6",
    prompt:"電力P＝V×I。このとき、6V・2Aのときの電力は？",
    answer:"12w",
    hint:"P＝VI！",
    solution:"6×2＝12W（ワット）！"
  },
  {
    id:"q7",
    prompt:"滑車を使っても仕事の大きさは変わらない理由は？<br><span class='hidden-text' data-key='ans3'>力が小さくなった分、距離が長くなるから</span>",
    answer:"力が小さくなった分距離が長くなる",
    hint:"滑車の原理！",
    solution:"力が半分になると動かす距離は2倍になる→仕事（力×距離）は同じ！"
  },
  {
    id:"q8",
    prompt:"位置エネルギーの公式は？<br>（ヒント：重力・高さ）",
    answer:"mgh",
    hint:"重力の記号はg！",
    solution:"位置エネルギー＝mgh（質量×重力加速度×高さ）！"
  },
  {
    id:"q9",
    prompt:"運動エネルギーの公式は？",
    answer:"1/2mv^2",
    hint:"質量×速度²×1/2！",
    solution:"運動エネルギー＝1/2mv²！"
  },
  {
    id:"q10",
    prompt:"エネルギー保存の法則とは？<br><span class='hidden-text' data-key='ans4'>エネルギーの総量は変わらない</span>",
    answer:"エネルギーの総量は変わらない",
    hint:"運動・位置エネルギーの関係！",
    solution:"形は変わっても、全体のエネルギーの量は一定に保たれる！"
  }
];
 
const quizEl=document.getElementById('quiz');
const scoreEl=document.getElementById('score');
let state={total:QUESTIONS.length,correct:0,perQ:{}};
 
function mount(){
  QUESTIONS.forEach((q,i)=>{
    state.perQ[q.id]={correct:false};
    const card=document.createElement('div');
    card.className='card';
    card.dataset.qid=q.id;
    card.innerHTML=`
      <h3>第${i+1}問</h3>
      <p>${q.prompt}</p>
      <p><input type="text" id="input-${q.id}" placeholder="答えを入力">
      <button class="btn" onclick="checkAnswer('${q.id}')">採点</button>
      <span class="feedback" id="fb-${q.id}"></span></p>
      <p><button class="btn ghost" onclick="toggleSolution('${q.id}')">解説表示</button></p>
      <p id="sol-${q.id}" style="display:none">${q.solution}</p>
      <p><small>ヒント：${q.hint}</small></p>
    `;
    quizEl.appendChild(card);
  });
  updateScore();
  document.addEventListener('click',e=>{
    const ht=e.target.closest('.hidden-text');
    if(ht) toggleHidden(ht);
  });
}
 
function toggleHidden(el){
  const now=el.getAttribute('data-revealed')==="true";
  el.setAttribute('data-revealed',!now);
}
 
function toggleSolution(qid){
  const sol=document.getElementById(`sol-${qid}`);
  sol.style.display=sol.style.display==="none"?"block":"none";
}
 
function checkAnswer(qid){
  const input=document.getElementById(`input-${qid}`);
  const fb=document.getElementById(`fb-${qid}`);
  const q=QUESTIONS.find(x=>x.id===qid);
  const user=input.value.trim().toLowerCase();
  const correct=q.answer.trim().toLowerCase();
  if(user===correct){
    fb.textContent="正解！";
    fb.style.color="#16a34a";
    state.perQ[qid].correct=true;
  }else{
    fb.textContent=`不正解（答え：${q.answer}）`;
    fb.style.color="#dc2626";
    state.perQ[qid].correct=false;
  }
  updateScore();
}
 
function updateScore(){
  const correct=Object.values(state.perQ).filter(x=>x.correct).length;
  scoreEl.textContent=`${correct} / ${state.total}`;
}
 
mount();
</script>
 
</body></html>
