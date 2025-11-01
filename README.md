<!doctype html>
<html lang="ja">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>中3理科・物理（運動〜浮力）50問クイズ</title>
  <meta name="description" content="中学3年生向けの理科（物理：運動・等速直線運動・等加速度運動・作用反作用・浮力）の選択式50問クイズです！">
  <meta name="keywords" content="中3,理科,物理,運動,等速直線運動,等加速度運動,作用反作用,浮力,クイズ">
  <meta property="og:title" content="中3理科・物理 50問クイズ" />
  <meta property="og:description" content="運動・力・浮力を学ぶ選択式50問！学習用に作られたクイズだ！" />
  <style>
    :root{
      --accent:#1e40af;
      --bg:#f8fafc;
      --card:#ffffff;
      --ok:#16a34a;
      --ng:#dc2626;
      --muted:#6b7280;
    }
    *{box-sizing:border-box}
    body{
      background:var(--bg);
      font-family:"Noto Sans JP", system-ui, sans-serif;
      margin:0;padding:24px;color:#0f172a;
      -webkit-font-smoothing:antialiased;
    }
    .container{max-width:980px;margin:0 auto;}
    header{text-align:center;margin-bottom:18px;}
    h1{color:var(--accent);margin:6px 0;font-size:1.5rem;}
    p.lead{color:var(--muted);margin-top:0;}
    .controls{display:flex;gap:8px;flex-wrap:wrap;justify-content:center;margin:12px 0;}
    button.btn{
      background:var(--accent);color:#fff;border:0;padding:8px 12px;border-radius:8px;cursor:pointer;font-weight:700;
    }
    button.ghost{background:#fff;color:var(--accent);border:1px solid rgba(30,64,175,0.12);}
    .card{background:var(--card);padding:14px;border-radius:10px;box-shadow:0 4px 14px rgba(2,6,23,0.06);margin-bottom:12px;}
    .meta{font-size:0.88rem;color:var(--muted);margin-bottom:8px;}
    .q-head{display:flex;justify-content:space-between;align-items:center;gap:8px;}
    .q-title{font-weight:800;}
    .difficulty{font-size:0.85rem;color:var(--muted);}
    .choices{display:flex;flex-direction:column;gap:8px;margin-top:10px;}
    .choice{
      display:flex;align-items:center;gap:10px;padding:8px;border-radius:8px;border:1px solid #eef2ff;cursor:pointer;
      user-select:none;background:#fbfdff;
    }
    .choice input{display:none;}
    .choice.selected{background:linear-gradient(90deg, rgba(30,64,175,0.06), rgba(99,102,241,0.03));border-color:rgba(30,64,175,0.12);}
    .footer-note{font-size:0.9rem;color:var(--muted);text-align:center;margin-top:14px;}
    #resultBox{display:none;margin-top:16px;padding:14px;border-radius:10px;}
    #breakdown{margin-top:12px;}
    .correct-mark{color:var(--ok);font-weight:800;}
    .wrong-mark{color:var(--ng);font-weight:800;}
    .reveal{margin-top:8px;}
    .small{font-size:0.85rem;color:var(--muted);}
    @media (max-width:700px){
      .q-head{flex-direction:column;align-items:flex-start;gap:6px;}
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <h1>中3理科・物理 50問クイズ！</h1>
      <p class="lead">分野：運動の速度 / 等速直線運動 / 等加速度運動 / 作用・反作用 / 浮力！全問回答後に合計点を表示する！</p>
      <div class="meta">問題ごとに難易度（★〜★★★）と配点（1〜5点）を設定！高配点の問題は点数が大きいぞ！</div>
    </header>

    <div id="quiz"></div>

    <div class="controls">
      <button id="submitAll" class="btn" disabled>全問を採点してスコアを表示する！</button>
      <button id="revealAll" class="btn ghost">正解をすべて表示する（採点後に）</button>
    </div>

    <div id="resultBox" class="card">
      <div id="summary"></div>
      <div id="breakdown"></div>
      <div class="small">※復習用に各問の正解・解説を後から表示できます！</div>
    </div>

    <div class="footer-note">このファイルを <code>index.html</code> として保存して、GitHubにアップすれば GitHub Pagesで公開できる！</div>
  </div>

<script>
/*
  仕様：
   - QUESTIONS 配列に50問を定義！
   - 各問題: id, prompt, choices(array), correct (index), points (int), difficulty (★ string), explanation (string)
   - 選択はクリックで選択、全問回答後に採点ボタンが有効になる！
*/

const QUESTIONS = [
/* 運動の速度（1〜10） */
{ id:"q01", prompt:"平均の速さの定義はどれか！？", choices:["単位時間あたりに進む距離！","ある瞬間の速さ！","移動方向付きの速度！"], correct:0, points:1, difficulty:"★", explanation:"平均の速さは移動した総距離をかかった時間で割ったものだ！"},
{ id:"q02", prompt:"速さの単位で正しいのはどれか！？", choices:["m/s（メートル毎秒）","N（ニュートン）","J（ジュール）","Ω（オーム）"], correct:0, points:1, difficulty:"★", explanation:"速さのSI単位はm/sだ！"},
{ id:"q03", prompt:"秒速3mは時速何km/hか！？", choices:["10.8km/h","3.0km/h","108km/h"], correct:0, points:2, difficulty:"★★", explanation:"3 (m/s) × 3600 s/h ÷ 1000 = 10.8 km/h！"},
{ id:"q04", prompt:"等速直線運動とはどれか！？", choices:["速さが一定で直線上を動く運動！","速度が変化する円運動！","停止している状態！"], correct:0, points:1, difficulty:"★", explanation:"等速直線運動は速さが一定で直線状を動く運動だ！"},
{ id:"q05", prompt:"瞬間の速さを測りたいときに適しているものはどれか！?", choices:["速度計や瞬時速度の測定法！","平均速度のみで十分！","移動距離だけでよい！","力学的エネルギー"], correct:0, points:2, difficulty:"★★", explanation:"瞬間の速さは瞬時の速度を測る必要がある！"},
{ id:"q06", prompt:"車が一定の速さで直進しているとき、速度ベクトルはどうなる！？", choices:["大きさと向きが変わらない！","大きさだけ変わる！","向きだけ変わる！","大きさも向きも変わる！"], correct:0, points:1, difficulty:"★", explanation:"等速直線運動では速度の大きさも向きも変わらない！"},
{ id:"q07", prompt:"速さが0でも速度が0でない場合はあるか！？", choices:["いいや、速さ0＝速度0！","ある！向きの概念で非ゼロになる！","ある！ただし回転運動のみ"], correct:0, points:1, difficulty:"★", explanation:"速さは速度の大きさなので0なら速度も0だ！"},
{ id:"q08", prompt:"速さと速度の違いで正しいものはどれ！？", choices:["速さは大きさのみ、速度は大きさと向きを持つ！","速度はスカラー、速さはベクトル！","同じ意味で使う！"], correct:0, points:1, difficulty:"★", explanation:"速さはスカラー、速度はベクトル（向きを持つ）だ！"},
{ id:"q09", prompt:"物体が同じ距離を同じ時間で動くなら、その速さはどうか！？", choices:["一定だ！","刻々と変わる！","分からない！"], correct:0, points:1, difficulty:"★", explanation:"同じ距離を同じ時間で進むなら速さは一定だ！"},
{ id:"q10", prompt:"速度の平均を求める公式として正しいのはどれ！？", choices:["平均速度＝変位÷時間！","平均速度＝距離÷時間！","平均速度＝力÷時間！","平均速度＝速さ×時間！"], correct:0, points:2, difficulty:"★★", explanation:"平均速度は変位（始点と終点の差）を時間で割った値だ！"},

/* 等速直線運動（11〜20） */
{ id:"q11", prompt:"等速直線運動での位置xと時間tの関係はどれか！？", choices:["x = x0 + vt！","x = x0 + 1/2 at^2！","v = at + v0！"], correct:0, points:2, difficulty:"★★", explanation:"等速直線運動は x = 初期位置 + 速度×時間 の直線関係だ！"},
{ id:"q12", prompt:"等速直線運動のグラフ（位置−時間）はどんな形か！？", choices:["直線！","放物線！","水平線！","指数曲線！"], correct:0, points:1, difficulty:"★", explanation:"位置−時間グラフは直線になる！傾きが速度だ！"},
{ id:"q13", prompt:"ある車が等速で10sに50m進んだ！速度は！？", choices:["5.0m/s","0.2m/s","50m/s"], correct:0, points:2, difficulty:"★★", explanation:"50 ÷ 10 = 5.0 m/s！"},
{ id:"q14", prompt:"等速直線運動中の速度の時間変化はどうか！？", choices:["変化しない！","一定の割合で増える！","不規則に変わる！"], correct:0, points:1, difficulty:"★", explanation:"等速だから時間に対して速度は一定だ！"},
{ id:"q15", prompt:"等速直線運動で速度vを二倍にすると位置−時間グラフの傾きはどうなる！？", choices:["2倍になる！","半分になる！","変わらない！"], correct:0, points:2, difficulty:"★★", explanation:"傾き＝速度だから2倍になる！"},
{ id:"q16", prompt:"等速で移動する物体の加速度は？", choices:["0！","一定の正の値！","速度に比例して増える！"], correct:0, points:1, difficulty:"★", explanation:"等速では速度の変化がないため加速度は0だ！"},
{ id:"q17", prompt:"等速直線運動で速度を0にするには？", choices:["外部から力を働かせて速度を変える！","何もしなくても自然に0になる！","速度は突然変わる事ができない"], correct:0, points:2, difficulty:"★★", explanation:"慣性により何もしないと速度は保たれるので、力が必要だ！"},
{ id:"q18", prompt:"等速直線運動の物体に働く合力はどうなる！？", choices:["0に等しい！","常に一定の非ゼロ値！","時間で増加する！"], correct:0, points:2, difficulty:"★★", explanation:"合力=0のとき等速直線運動が成り立つ！"},
{ id:"q19", prompt:"水平な摩擦がない台上で静止していた物体に一定の水平力を与え続けたら？", choices:["等加速度運動になる！","等速運動になる！","停止したまま！"], correct:0, points:2, difficulty:"★★", explanation:"一定力だと一定の加速度が生じ、等加速度運動になる！"},
{ id:"q20", prompt:"等速直線運動の例として正しいものはどれ！？", choices:["アイス上で摩擦が非常に小さく滑るソリ！","自転車でブレーキをかけて停止する！","自由落下する物体！"], correct:0, points:1, difficulty:"★", explanation:"摩擦が無視できる条件で一定の速度なら等速直線運動の近似例だ！"},

/* 等加速度運動（21〜30） */
{ id:"q21", prompt:"等加速度運動に関する式として正しいのはどれ！？", choices:["v = v0 + at！","x = x0 + vt（等速）！","F = ma！"], correct:0, points:2, difficulty:"★★", explanation:"等加速度運動の速度-Time関係は v = v0 + at だ！"},
{ id:"q22", prompt:"等加速度運動の位置変化を表す式はどれか！？", choices:["x = x0 + v0 t + 1/2 a t^2！","x = x0 + vt！","W = F s！"], correct:0, points:2, difficulty:"★★", explanation:"位置は初速度項と加速度項を含む放物線的変化をする！"},
{ id:"q23", prompt:"自由落下は理想的にどんな運動か！？", choices:["等加速度運動（加速度＝g）！","等速直線運動！","円運動！"], correct:0, points:2, difficulty:"★★", explanation:"空気抵抗無しなら重力で等加速度運動になる（加速度g）！"},
{ id:"q24", prompt:"初速度が0で加速度aでt秒運動したときの速度は？", choices:["v = a t！","v = 0！","v = at^2！"], correct:0, points:1, difficulty:"★", explanation:"初速度0なら v = 0 + a t となる！"},
{ id:"q25", prompt:"初速度v0、加速度aのとき速度vと位置xの関係で正しいのは！？", choices:["v^2 = v0^2 + 2aΔx！","x = v0 t！","v = v0 + 1/2 a t^2！"], correct:0, points:2, difficulty:"★★", explanation:"運動方程式のひとつでエネルギー的にもしばしば用いる式だ！"},
{ id:"q26", prompt:"一定の加速度aで速度が時間とともに直線的に変化するのはなぜか！？", choices:["加速度が一定だから！","速度に比例する力が働くから！","摩擦が支配しているから！"], correct:0, points:1, difficulty:"★", explanation:"加速度が一定なら速度は時間に比例して増減する（直線）！"},
{ id:"q27", prompt:"等加速度運動の速度−時間グラフの面積は何を表す！？", choices:["変位（位置の変化）！","力の大きさ！","加速度の時間積分！"], correct:0, points:2, difficulty:"★★", explanation:"面積（速度×時間）は移動した変位を表す！"},
{ id:"q28", prompt:"物体を投げ上げた時、最高点での速度は？", choices:["0！","最大値！","負の値！"], correct:0, points:1, difficulty:"★", explanation:"上向きの速度が0になった時が最高点だ！"},
{ id:"q29", prompt:"自由落下で物体が落ちるときの加速度gは地球上で約いくつか！？", choices:["9.8 m/s^2！","1.6 m/s^2！","3.7 m/s^2！","0 m/s^2！"], correct:0, points:1, difficulty:"★", explanation:"地球表面近くでは g ≒ 9.8 m/s² だ！"},
{ id:"q30", prompt:"等加速度運動での加速度の単位は何か！？", choices:["m/s^2（メートル毎秒毎秒）！","m/s（メートル毎秒）！","N（ニュートン）！"], correct:0, points:1, difficulty:"★", explanation:"加速度の単位は m/s² だ！"},

/* 作用・反作用（31〜40） */
{ id:"q31", prompt:"作用・反作用の法則（第3法則）を述べるとどれか！？", choices:["ある物体AがBに力を加えるとBはAに等しい大きさで逆向きの力を加える！","物体は力が働かないと静止する！","力は質量に比例する！"], correct:0, points:2, difficulty:"★★", explanation:"作用と反作用は必ず同時に生じ、向きが逆、大小が等しい！"},
{ id:"q32", prompt:"ロケットが噴射で前に進むのは作用・反作用のどの仕組みか！？", choices:["燃料の排出（後方への作用）が燃焼ガスの反作用で前進させる！","重力の反作用！","慣性が反作用となる！"], correct:0, points:2, difficulty:"★★★", explanation:"後方へガスを強く押し出す作用に対する反作用でロケットが前進する！"},
{ id:"q33", prompt:"つり合っている2つの力はどう表される！？", choices:["大きさが等しく向きが逆！","どちらも同方向に働く！","一方が他方の2倍！"], correct:0, points:1, difficulty:"★", explanation:"釣り合いは合力が0、つまり同じ大きさで逆向きだ！"},
{ id:"q34", prompt:"人が床を押すと床が人を押し返す。これらは何にあたる！？", choices:["作用と反作用！","摩擦と静止力！","重力と浮力！"], correct:0, points:1, difficulty:"★", explanation:"床を押すのが作用、床が押し返すのが反作用だ！"},
{ id:"q35", prompt:"作用・反作用の力は同一物体に働くか！?", choices:["いいや、常に異なる2つの物体に働く！","同じ物体にだけ働く！","片方だけ物体に働く！"], correct:0, points:2, difficulty:"★★", explanation:"作用と反作用は必ず相互作用している2物体にそれぞれ作用する！"},
{ id:"q36", prompt:"スケボーに乗って壁を押すと反対方向に動くのはなぜか！？", choices:["壁に対する作用で壁がスケボーを押し返すから！（反作用）","重力が突然変わるから！","速度保存の法則に反するから！"], correct:0, points:2, difficulty:"★★", explanation:"押す作用に対して壁の反作用によりスケボーが押し出される！"},
{ id:"q37", prompt:"泳ぐときに水を後ろに押すのは何の例か！？", choices:["作用・反作用の例！","運動方程式に反する例！","位置エネルギーの例！"], correct:0, points:1, difficulty:"★", explanation:"水を押す作用に対する反作用で体が前へ進む！"},
{ id:"q38", prompt:"ゴムが縮むときに働く力と反作用はどのようか！？", choices:["ゴムは引っ張る力を生み、それに対し物体が逆向きの力を加える！","ゴムは何も働かない！","ゴムの力は無限に増える！"], correct:0, points:2, difficulty:"★★", explanation:"弾性力は引っ張る・押す作用を生み、それに対する反作用がある！"},
{ id:"q39", prompt:"地面を蹴ってジャンプする時、ジャンプの高さは何と関係が深いか！？", choices:["脚が地面に与える力の大きさと時間！","作用・反作用だけでは決まらない！","太陽の位置！"], correct:0, points:2, difficulty:"★★★", explanation:"押す力とその作用時間（インパルス）が跳躍に重要だ！"},
{ id:"q40", prompt:"作用・反作用で一般に成り立たないものはどれか！？", choices:["一方だけが力を受ける状況！（成り立たない）","常に大きさが等しい」「向きが逆である"], correct:0, points:2, difficulty:"★★", explanation:"作用と反作用は同時に発生するため一方だけの力は存在しない！"},

/* 浮力（41〜50） */
{ id:"q41", prompt:"浮力の原因は何か！？", choices:["流体による上向きの圧力差！","物体自体の重さ！","摩擦力！"], correct:0, points:2, difficulty:"★★", explanation:"流体中では下部の圧力が上部より大きく、その差が上向きの浮力になる！"},
{ id:"q42", prompt:"アルキメデスの原理を述べるとどれか！？", choices:["物体が流体から受ける浮力は、その物体が排除した流体の重さに等しい！","浮力は常に物体の重さと等しい！","浮力は密度に依存しない！"], correct:0, points:3, difficulty:"★★★", explanation:"アルキメデスの原理は排除した流体の重さと浮力の関係を示す！"},
{ id:"q43", prompt:"密度ρの液体に体積Vの物体が完全に沈んでいるときの浮力の大きさは！？", choices:["ρVg！","mg！","ρg！","Vg！"], correct:0, points:3, difficulty:"★★★", explanation:"浮力=流体の密度×排除体積×重力加速度 (ρVg) だ！"},
{ id:"q44", prompt:"物体が浮く条件はどれか！？", choices:["物体の重さが浮力より小さいとき！","重さが浮力より大きいとき！","重さと浮力は無関係！"], correct:0, points:2, difficulty:"★★", explanation:"重さ<浮力なら浮く、重さ=浮力で静止、重さ>浮力で沈む！"},
{ id:"q45", prompt:"同じ体積の物体AとBがある。Aの密度がBより小さいときどうなる！？", choices:["Aの方が浮きやすい！","Bの方が浮きやすい！","両方とも同じ挙動！"], correct:0, points:2, difficulty:"★★", explanation:"密度が小さいほど重さが小さくなり、浮力に対して浮きやすい！"},
{ id:"q46", prompt:"沈めた物体が排除する体積とは何か！？", choices:["物体が押しのけた流体の体積！","物体の重量！","物体の表面積！"], correct:0, points:1, difficulty:"★", explanation:"排除体積は物体が占める流体の領域の体積だ！"},
{ id:"q47", prompt:"海水と淡水で同じ物体を浮かべるとどうなる！？", choices:["海水の方が浮きやすい（浮力が大きい）！","淡水の方が浮きやすい！","どちらも同じ！"], correct:0, points:2, difficulty:"★★", explanation:"海水は密度が大きいので同じ体積で浮力が大きく浮きやすい！"},
{ id:"q48", prompt:"潜水艦が浮上・潜航を行うときに調整するのは何か！？", choices:["浮力（バラストで排水・注水）！","重力の大きさ！","重力加速度g自体！"], correct:0, points:3, difficulty:"★★★", explanation:"バラストタンクで水を出し入れして排除体積や平均密度を変え浮力を調整する！"},
{ id:"q49", prompt:"船が重い貨物を積んでも沈まないのはなぜか！？", choices:["船全体の平均密度が水より小さいから！","貨物が軽いから！","船が磁石だから！"], correct:0, points:2, difficulty:"★★", explanation:"船は甲板や空気のおかげで全体の平均密度が小さくなるため浮く！"},
{ id:"q50", prompt:"浮力の単位は何で示されることが多いか！？", choices:["N（ニュートン）！","kg（キログラム）！","m^3（立方メートル）！","Pa（パスカル）！"], correct:0, points:1, difficulty:"★", explanation:"浮力は力なので N の単位で表す！"}
];


// レンダリング
const quizEl = document.getElementById("quiz");
const submitAllBtn = document.getElementById("submitAll");
const revealAllBtn = document.getElementById("revealAll");
const resultBox = document.getElementById("resultBox");
const summaryEl = document.getElementById("summary");
const breakdownEl = document.getElementById("breakdown");

let answers = {}; // id -> selectedChoiceIndex

function render(){
  QUESTIONS.forEach((q, idx) => {
    const card = document.createElement("div");
    card.className = "card";
    card.id = `card-${q.id}`;
    const header = document.createElement("div");
    header.className = "q-head";
    header.innerHTML = `<div class="q-title">第${idx+1}問</div><div class="difficulty">${q.difficulty}　配点：${q.points}点</div>`;
    const body = document.createElement("div");
    body.innerHTML = `<p style="margin:8px 0 0 0">${q.prompt}</p>`;
    const choicesDiv = document.createElement("div");
    choicesDiv.className = "choices";
    q.choices.forEach((ch, ci) => {
      const label = document.createElement("label");
      label.className = "choice";
      label.htmlFor = `${q.id}-c${ci}`;
      label.innerHTML = `<input type="radio" name="${q.id}" id="${q.id}-c${ci}" value="${ci}" /> <div style="flex:1">${String.fromCharCode(65+ci)}. ${ch}</div>`;
      // クリックで選択を視覚化
      label.addEventListener("click", (e) => {
        // set answers
        answers[q.id] = ci;
        // mark selected visually
        const siblings = choicesDiv.querySelectorAll(".choice");
        siblings.forEach(s => s.classList.remove("selected"));
        label.classList.add("selected");
        checkAllAnswered();
      });
      choicesDiv.appendChild(label);
    });
    body.appendChild(choicesDiv);
    // 解説を後で表示できるブロック
    const revealDiv = document.createElement("div");
    revealDiv.className = "reveal";
    revealDiv.id = `reveal-${q.id}`;
    revealDiv.style.display = "none";
    revealDiv.innerHTML = `<div class="small"><strong>正解：</strong> ${String.fromCharCode(65+q.correct)}　／　<strong>解説：</strong> ${q.explanation}</div>`;
    body.appendChild(revealDiv);

    card.appendChild(header);
    card.appendChild(body);
    quizEl.appendChild(card);
  });
}

// 全問回答チェック
function checkAllAnswered(){
  const total = QUESTIONS.length;
  const answeredCount = Object.keys(answers).length;
  submitAllBtn.disabled = answeredCount !== total;
  // optionally indicate how many remaining
  submitAllBtn.textContent = answeredCount === total ? "全問を採点してスコアを表示する！" : `残り ${total - answeredCount} 問を回答してから採点！`;
}

// 採点処理
function gradeAll(){
  let totalScore = 0;
  let maxScore = 0;
  let correctCount = 0;
  let breakdownHtml = "";
  QUESTIONS.forEach((q, idx) => {
    maxScore += q.points;
    const sel = answers[q.id];
    const isCorrect = (typeof sel !== "undefined" && sel === q.correct);
    if(isCorrect){
      totalScore += q.points;
      correctCount++;
    }
    breakdownHtml += `<div style="margin-bottom:8px;padding:10px;border-radius:8px;background:#fff7ef;">
      <div style="font-weight:800">第${idx+1}問：${q.prompt}</div>
      <div class="small" style="margin-top:6px">あなたの答え： ${typeof sel === "undefined" ? '<span class="wrong-mark">未回答</span>' : `${String.fromCharCode(65+sel)}. ${q.choices[sel]}`}</div>
      <div class="small" style="margin-top:4px">${isCorrect ? `<span class="correct-mark">正解！ +${q.points}点</span>` : `<span class="wrong-mark">不正解</span> （正解：${String.fromCharCode(65+q.correct)}. ${q.choices[q.correct]}）`}</div>
      <div id="ex-${q.id}" class="small" style="margin-top:6px;display:none"><strong>解説：</strong> ${q.explanation}</div>
      <div style="margin-top:6px"><button class="btn ghost" onclick="toggleExplain('${q.id}', this)">解説を表示／非表示</button></div>
    </div>`;
  });
  const percent = Math.round((totalScore / maxScore) * 100);
  summaryEl.innerHTML = `<div style="font-size:1.05rem;font-weight:800">合計得点： ${totalScore} / ${maxScore} 点　（正答数： ${correctCount} / ${QUESTIONS.length}　 正答率： ${percent}%）</div>`;
  breakdownEl.innerHTML = breakdownHtml;
  resultBox.style.display = "block";
  // enable revealAll button now
  revealAllBtn.disabled = false;
  // scroll to results
  resultBox.scrollIntoView({behavior:"smooth"});
}

// 解説トグル
function toggleExplain(qid, btn){
  const el = document.getElementById(`ex-${qid}`);
  if(!el) return;
  el.style.display = el.style.display === "none" ? "block" : "none";
  btn.textContent = el.style.display === "none" ? "解説を表示／非表示" : "解説を表示／非表示";
}

// revealAll 正解表示
function revealAllCorrect(){
  QUESTIONS.forEach(q => {
    const el = document.getElementById(`reveal-${q.id}`);
    if(el) el.style.display = "block";
    // visually mark correct choice
    const card = document.getElementById(`card-${q.id}`);
    if(card){
      const choices = card.querySelectorAll(".choice");
      choices.forEach((c, ci) => {
        c.classList.remove("selected");
        if(ci === q.correct){
          c.classList.add("selected");
        }
      });
    }
  });
  revealAllBtn.disabled = true;
  revealAllBtn.textContent = "正解を表示済み！";
}

// 初期化
render();
checkAllAnswered();

// イベント
submitAllBtn.addEventListener("click", () => {
  gradeAll();
});
revealAllBtn.addEventListener("click", () => {
  // only allow reveal after grading
  if(resultBox.style.display === "none"){
    alert("まずは全問を採点してスコア表示してから、正解表示ボタンを使ってください！");
    return;
  }
  revealAllCorrect();
});

// 予防：ページ離脱確認（未採点の場合）
window.addEventListener("beforeunload", (e) => {
  // もし一部回答済みで採点未実施なら確認
  if(Object.keys(answers).length > 0 && resultBox.style.display === "none"){
    e.preventDefault();
    e.returnValue = '';
  }
});
</script>
</body>
</html>
