<!doctype html>
<html lang="ja">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#000000">
<title>仕事と自分の体 時計</title>

<style>
  :root{
    --yellow:#ffd800;
    --red:#ef1b16;
    --black:#000;
    --white:#f7f7f7;
    --shift-x:0px;
    --shift-y:0px;
  }

  *{
    box-sizing:border-box;
  }

  html,
  body{
    margin:0;
    width:100%;
    height:100%;
    overflow:hidden;
    background:var(--black);
    color:#fff;
    font-family:
      "Hiragino Kaku Gothic ProN",
      "Yu Gothic",
      "Meiryo",
      system-ui,
      sans-serif;
  }

  body{
    user-select:none;
    cursor:none;
    overscroll-behavior:none;
    touch-action:manipulation;
  }

  #screen{
    width:100vw;
    height:100vh;

    display:grid;
    grid-template-rows:
      17vh
      1fr
      17vh;

    transform:
      translate(var(--shift-x), var(--shift-y))
      scale(1.004);

    transform-origin:center center;
    transition:transform 1.2s ease;

    background:#000;
  }

  /* =========================
     上下の黄色い帯
     ========================= */

  .ticker{
    position:relative;
    overflow:hidden;

    background:var(--yellow);
    color:#111;

    display:flex;
    align-items:center;

    border-top:2px solid rgba(0,0,0,.25);
    border-bottom:2px solid rgba(0,0,0,.25);
  }

  .track{
    width:max-content;

    display:flex;
    align-items:center;

    white-space:nowrap;
    will-change:transform;

    animation:
      scroll-left
      20s
      linear
      infinite;
  }

  .message{
    flex:none;

    font-weight:900;

    font-size:
      clamp(
        28px,
        4.2vw,
        80px
      );

    line-height:1;
    letter-spacing:.01em;

    padding-right:3.5vw;
  }

  .red{
    color:var(--red);
  }

  @keyframes scroll-left{

    from{
      transform:translateX(0);
    }

    to{
      transform:translateX(-50%);
    }

  }

  /* =========================
     時計エリア
     ========================= */

  .clock-area{
    position:relative;

    min-height:0;

    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;

    background:
      radial-gradient(
        circle at 50% 42%,
        #171717 0%,
        #090909 45%,
        #000 100%
      );
  }

  .date{
    font-size:
      clamp(
        20px,
        2.3vw,
        44px
      );

    font-weight:700;

    letter-spacing:.08em;

    opacity:.72;

    margin-bottom:1.8vh;
  }

  .clock{
    font-family:
      ui-monospace,
      "SFMono-Regular",
      "Roboto Mono",
      "Consolas",
      monospace;

    font-size:
      clamp(
        92px,
        18vw,
        360px
      );

    font-weight:900;

    line-height:.88;

    letter-spacing:-.075em;

    color:var(--white);

    font-variant-numeric:
      tabular-nums;

    text-shadow:
      0 0 12px rgba(255,255,255,.12),
      0 4px 20px rgba(0,0,0,.85);
  }

  .sub{
    margin-top:2.2vh;

    font-size:
      clamp(
        18px,
        1.7vw,
        34px
      );

    letter-spacing:.22em;

    font-weight:700;

    opacity:.35;
  }

  /* =========================
     最初だけ出る全画面案内
     ========================= */

  #hint{
    position:fixed;

    z-index:10;

    left:50%;
    bottom:22px;

    transform:
      translateX(-50%);

    padding:
      10px
      18px;

    border-radius:999px;

    background:
      rgba(20,20,20,.75);

    border:
      1px solid
      rgba(255,255,255,.18);

    color:#fff;

    font:
      700
      clamp(13px,1.1vw,18px)
      /1.2
      system-ui,
      sans-serif;

    letter-spacing:.04em;

    opacity:.82;

    transition:
      opacity .5s;

    pointer-events:none;
  }

  .hidden{
    opacity:0 !important;
  }

  /* 高さが低い画面向け */

  @media (max-height:650px){

    #screen{
      grid-template-rows:
        15vh
        1fr
        15vh;
    }

    .sub{
      display:none;
    }

    .date{
      margin-bottom:1vh;
    }

  }

</style>
</head>


<body>

<div id="screen">

  <!-- 上のテロップ -->

  <div class="ticker">

    <div class="track">

      <div class="message">

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

      </div>


      <div
        class="message"
        aria-hidden="true"
      >

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

      </div>

    </div>

  </div>


  <!-- 時計 -->

  <main class="clock-area">

    <div
      class="date"
      id="date"
    >
    </div>

    <div
      class="clock"
      id="clock"
    >
      00:00:00
    </div>

    <div class="sub">
      TIME IS YOURS
    </div>

  </main>


  <!-- 下のテロップ -->

  <div class="ticker">

    <div class="track">

      <div class="message">

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

      </div>


      <div
        class="message"
        aria-hidden="true"
      >

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

        <span class="red">
          仕事
        </span>

        と

        <span class="red">
          自分の体
        </span>

        どっちが大事かを考えなさい。

       　●　　

      </div>

    </div>

  </div>

</div>


<div id="hint">
  画面を1回押すと全画面
</div>


<script>

(() => {

  const clock =
    document.getElementById(
      'clock'
    );

  const date =
    document.getElementById(
      'date'
    );

  const hint =
    document.getElementById(
      'hint'
    );


  const weekdays =
    [
      '日',
      '月',
      '火',
      '水',
      '木',
      '金',
      '土'
    ];


  function pad(n){

    return String(n)
      .padStart(
        2,
        '0'
      );

  }


  /* =========================
     時計更新
     ========================= */

  function updateClock(){

    const now =
      new Date();


    clock.textContent =
      `${pad(now.getHours())}:` +
      `${pad(now.getMinutes())}:` +
      `${pad(now.getSeconds())}`;


    date.textContent =
      `${now.getFullYear()}年` +
      `${now.getMonth()+1}月` +
      `${now.getDate()}日` +
      `（${weekdays[now.getDay()]}）`;

  }


  updateClock();

  setInterval(
    updateClock,
    200
  );


  /* =========================
     焼き付き対策

     5分ごとに画面全体を
     数pxだけ動かす
     ========================= */

  const shifts =
    [
      [0,0],
      [4,0],
      [-4,0],
      [0,4],
      [0,-4],
      [3,3],
      [-3,3],
      [3,-3],
      [-3,-3]
    ];


  let shiftIndex =
    0;


  function shiftScreen(){

    shiftIndex =
      (shiftIndex + 1)
      % shifts.length;


    const [x,y] =
      shifts[
        shiftIndex
      ];


    document.documentElement
      .style
      .setProperty(
        '--shift-x',
        x + 'px'
      );


    document.documentElement
      .style
      .setProperty(
        '--shift-y',
        y + 'px'
      );

  }


  setInterval(
    shiftScreen,
    5 * 60 * 1000
  );


  /* =========================
     全画面表示
     ========================= */

  async function requestFullscreen(){

    try{

      if(
        !document.fullscreenElement
        &&
        document.documentElement
          .requestFullscreen
      ){

        await
          document.documentElement
            .requestFullscreen();

      }

    }
    catch(e){
    }


    hint.classList
      .add(
        'hidden'
      );


    requestWakeLock();

  }


  /*
   TVリモコンの「決定」、
   クリック、タップ等に対応
  */

  document.addEventListener(
    'click',
    requestFullscreen
  );


  document.addEventListener(
    'touchend',
    requestFullscreen
  );


  document.addEventListener(
    'keydown',
    (e) => {

      if(
        [
          'Enter',
          ' ',
          'f',
          'F'
        ]
        .includes(e.key)
      ){

        requestFullscreen();

      }

    }
  );


  /* =========================
     スリープ防止
     対応ブラウザのみ有効
     ========================= */

  let wakeLock =
    null;


  async function requestWakeLock(){

    if(
      !('wakeLock' in navigator)
    ){
      return;
    }


    try{

      wakeLock =
        await navigator
          .wakeLock
          .request(
            'screen'
          );

    }
    catch(e){
    }

  }


  document.addEventListener(
    'visibilitychange',
    () => {

      if(
        document.visibilityState
        ===
        'visible'
      ){

        requestWakeLock();

      }

    }
  );


  /*
   全画面案内は10秒後に消す
  */

  setTimeout(
    () => {

      hint.classList
        .add(
          'hidden'
        );

    },
    10000
  );

})();

</script>

</body>
</html>