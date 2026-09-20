<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
  <title>忘却曲線 英単語アプリ</title>
  <style>
    :root {
      --primary: #4f46e5;
      --bg: #f3f4f6;
      --card-bg: #ffffff;
      --text: #1f2937;
      --success: #10b981;
      --warning: #f59e0b;
      --danger: #ef4444;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
    body { background: var(--bg); color: var(--text); padding-bottom: 70px; display: flex; flex-direction: column; min-height: 100vh; }
    header { background: var(--primary); color: white; padding: 16px; text-align: center; font-weight: bold; font-size: 1.2rem; }
    
    .container { padding: 16px; max-width: 500px; margin: 0 auto; width: 100%; flex: 1; }
    .screen { display: none; }
    .screen.active { display: block; }

    /* UI Components */
    .card { background: var(--card-bg); border-radius: 12px; padding: 20px; margin-bottom: 16px; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1); text-align: center; }
    .btn { background: var(--primary); color: white; border: none; padding: 12px 20px; border-radius: 8px; font-size: 1rem; font-weight: bold; width: 100%; cursor: pointer; margin-top: 8px; }
    .btn:active { opacity: 0.8; }
    .btn-success { background: var(--success); }
    .btn-warning { background: var(--warning); }
    .btn-danger { background: var(--danger); }
    
    input, select { width: 100%; padding: 12px; margin: 8px 0; border: 1px solid #ccc; border-radius: 8px; font-size: 1rem; }
    
    /* Navigation Bar */
    nav { position: fixed; bottom: 0; width: 100%; background: white; display: flex; border-top: 1px solid #ddd; height: 60px; }
    nav button { flex: 1; border: none; background: none; font-size: 0.75rem; color: #666; display: flex; flex-direction: column; align-items: center; justify-content: center; }
    nav button.active { color: var(--primary); font-weight: bold; }

    /* Flashcard Special */
    .flashcard { min-height: 180px; display: flex; flex-direction: column; justify-content: center; align-items: center; cursor: pointer; border: 2px solid var(--primary); }
    .word-title { font-size: 2rem; font-weight: bold; margin-bottom: 10px; }
    .word-meaning { font-size: 1.2rem; color: #4b5563; }
    .hidden { display: none !important; }

    /* List & Stats */
    .ranking-item { display: flex; justify-content: space-between; padding: 12px; border-bottom: 1px solid #eee; background: white; border-radius: 8px; margin-bottom: 6px; }
  </style>
</head>
<body>

<header id="header-title">今日の学習</header>

<div class="container">
  <!-- ホーム・設定画面 -->
  <div id="screen-home" class="screen active">
    <div class="card">
      <h3>今日の学習設定</h3>
      <p style="margin: 10px 0; color: #666;">本日の目標単語数を指定してください</p>
      <input type="number" id="daily-limit" value="10" min="1" max="50">
      <button class="btn" onclick="startDailySession()">今日の学習を始める</button>
    </div>
    
    <div class="card">
      <h3>新規単語の追加</h3>
      <input type="text" id="new-word" placeholder="英単語 (例: apple)">
      <input type="text" id="new-meaning" placeholder="意味 (例: りんご)">
      <button class="btn btn-success" onclick="addWord()">単語を追加</button>
    </div>
  </div>

  <!-- 1. インプットゾーン -->
  <div id="screen-input" class="screen">
    <div class="card">
      <span style="font-size:0.8rem; color:#888;" id="input-progress">1 / 10</span>
      <div class="word-title" id="input-word">---</div>
      <div class="word-meaning" id="input-meaning">---</div>
    </div>
    <button class="btn" onclick="nextInputWord()">次へ進む</button>
  </div>

  <!-- 2. シャッフルカードゾーン -->
  <div id="screen-card" class="screen">
    <div class="card flashcard" onclick="toggleCardMeaning()">
      <div class="word-title" id="card-word">---</div>
      <div class="word-meaning hidden" id="card-meaning">タップして意味を表示</div>
    </div>
    <div id="card-controls" class="hidden">
      <div style="display: flex; gap: 8px;">
        <button class="btn btn-danger" onclick="answerCard(0)">覚えてない</button>
        <button class="btn btn-warning" onclick="answerCard(1)">微妙</button>
        <button class="btn btn-success" onclick="answerCard(2)">覚えてる</button>
      </div>
    </div>
    <p style="text-align: center; margin-top: 12px; font-size: 0.85rem; color: #666;" id="card-remaining"></p>
  </div>

  <!-- 3. テストゾーン -->
  <div id="screen-test" class="screen">
    <div class="card">
      <span style="font-size:0.8rem; color:#888;" id="test-progress">1 / 10</span>
      <div class="word-title" id="test-word">---</div>
      <input type="text" id="test-input" placeholder="意味を入力してください" autocomplete="off">
      <button class="btn" onclick="checkTestAnswer()">回答する</button>
    </div>
  </div>

  <!-- 苦手ランキング＆履歴画面 -->
  <div id="screen-stats" class="screen">
    <div class="card">
      <h3>覚えられないランキング (TOP 10)</h3>
      <p style="font-size:0.8rem; color:#666; margin-bottom:10px;">「覚えてない」選択＋テスト失敗回数の合計</p>
      <div id="ranking-list"></div>
    </div>
    <div class="card">
      <h3>テスト実施履歴</h3>
      <div id="history-list"></div>
    </div>
  </div>
</div>

<!-- 下部ナビゲーション -->
<nav>
  <button onclick="switchScreen('home')" id="nav-home" class="active">学習開始</button>
  <button onclick="switchScreen('stats')" id="nav-stats">成績・苦手</button>
</nav>

<script>
  // データ構造
  let words = JSON.parse(localStorage.getItem('words')) || [];
  let testHistory = JSON.parse(localStorage.getItem('testHistory')) || [];
  
  // セッション状態
  let sessionWords = [];
  let currentInputIndex = 0;
  let cardQueue = [];
  let currentCardWord = null;
  let testQueue = [];
  let currentTestIndex = 0;
  let testScore = 0;

  // 画面切替
  function switchScreen(screenId) {
    document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
    
    document.getElementById(`screen-${screenId}`).classList.add('active');
    if(document.getElementById(`nav-${screenId}`)) {
      document.getElementById(`nav-${screenId}`).classList.add('active');
    }
    
    if(screenId === 'stats') renderStats();
  }

  // 単語追加
  function addWord() {
    const wordInput = document.getElementById('new-word');
    const meaningInput = document.getElementById('new-meaning');
    if (!wordInput.value || !meaningInput.value) return alert('単語と意味を入力してください');

    words.push({
      id: Date.now(),
      word: wordInput.value.trim(),
      meaning: meaningInput.value.trim(),
      nextReviewDate: new Date().toISOString().split('T')[0], // 今日
      interval: 0,
      failCount: 0
    });

    saveData();
    wordInput.value = '';
    meaningInput.value = '';
    alert('単語を追加しました！');
  }

  function saveData() {
    localStorage.setItem('words', JSON.stringify(words));
    localStorage.setItem('testHistory', JSON.stringify(testHistory));
  }

  // 今日の学習セッション開始
  function startDailySession() {
    const limit = parseInt(document.getElementById('daily-limit').value);
    const today = new Date().toISOString().split('T')[0];

    // 復習優先＋新規で選出
    let dueWords = words.filter(w => w.nextReviewDate <= today);
    if(dueWords.length === 0) {
      alert('本日復習する単語はありません！新しい単語を追加するか、明日また開きましょう。');
      return;
    }

    sessionWords = dueWords.slice(0, limit);
    
    // 1. インプットゾーンの初期化
    currentInputIndex = 0;
    document.getElementById('header-title').innerText = '1. インプットゾーン';
    switchScreen('input');
    renderInputWord();
  }

  // 1. インプットゾーン制御
  function renderInputWord() {
    const w = sessionWords[currentInputIndex];
    document.getElementById('input-progress').innerText = `${currentInputIndex + 1} / ${sessionWords.length}`;
    document.getElementById('input-word').innerText = w.word;
    document.getElementById('input-meaning').innerText = w.meaning;
  }

  function nextInputWord() {
    currentInputIndex++;
    if (currentInputIndex < sessionWords.length) {
      renderInputWord();
    } else {
      startCardZone();
    }
  }

  // 2. シャッフルカードゾーン制御
  function startCardZone() {
    document.getElementById('header-title').innerText = '2. シャッフルカードゾーン';
    cardQueue = [...sessionWords];
    switchScreen('card');
    nextCard();
  }

  function nextCard() {
    if (cardQueue.length === 0) {
      startTestZone();
      return;
    }
    // ランダム取得
    const randomIndex = Math.floor(Math.random() * cardQueue.length);
    currentCardWord = cardQueue[randomIndex];

    document.getElementById('card-word').innerText = currentCardWord.word;
    document.getElementById('card-meaning').innerText = currentCardWord.meaning;
    document.getElementById('card-meaning').classList.add('hidden');
    document.getElementById('card-controls').classList.add('hidden');
    document.getElementById('card-remaining').innerText = `残り対象: ${cardQueue.length}単語`;
  }

  function toggleCardMeaning() {
    document.getElementById('card-meaning').classList.remove('hidden');
    document.getElementById('card-controls').classList.remove('hidden');
  }

  function answerCard(type) {
    // 0: 覚えてない, 1: 微妙, 2: 覚えてる
    const wordObj = words.find(w => w.id === currentCardWord.id);

    if (type === 2) { // 覚えてる
      // キューから削除
      cardQueue = cardQueue.filter(w => w.id !== currentCardWord.id);
      updateInterval(wordObj, true);
    } else {
      // 覚えてない / 微妙 -> キューに残し、失敗カウントを加算
      wordObj.failCount++;
      updateInterval(wordObj, false);
    }
    saveData();
    nextCard();
  }

  // 3. テストゾーン制御
  function startTestZone() {
    document.getElementById('header-title').innerText = '3. テストゾーン';
    testQueue = [...sessionWords];
    currentTestIndex = 0;
    testScore = 0;
    switchScreen('test');
    renderTestQuestion();
  }

  function renderTestQuestion() {
    const w = testQueue[currentTestIndex];
    document.getElementById('test-progress').innerText = `${currentTestIndex + 1} / ${testQueue.length}`;
    document.getElementById('test-word').innerText = w.word;
    document.getElementById('test-input').value = '';
  }

  function checkTestAnswer() {
    const input = document.getElementById('test-input').value.trim();
    const w = testQueue[currentTestIndex];
    const targetObj = words.find(item => item.id === w.id);

    // 部分一致または完全一致チェック
    if (input && w.meaning.includes(input)) {
      testScore++;
    } else {
      targetObj.failCount++;
      alert(`不正解！ 正解は: ${w.meaning}`);
    }

    currentTestIndex++;
    if (currentTestIndex < testQueue.length) {
      renderTestQuestion();
    } else {
      // テスト終了処理
      testHistory.unshift({
        date: new Date().toLocaleDateString(),
        score: testScore,
        total: testQueue.length
      });
      saveData();
      alert(`本日のテスト終了！ スコア: ${testScore} / ${testQueue.length}`);
      switchScreen('home');
      document.getElementById('header-title').innerText = '今日の学習';
    }
  }

  // 忘却曲線アルゴリズム (Spaced Repetition)
  function updateInterval(wordObj, isSuccess) {
    const intervals = [1, 3, 7, 14, 30]; // 復習間隔（日）
    
    if (isSuccess) {
      const nextDays = intervals[wordObj.interval] || 30;
      wordObj.interval = Math.min(wordObj.interval + 1, intervals.length - 1);
      
      let targetDate = new Date();
      targetDate.setDate(targetDate.getDate() + nextDays);
      wordObj.nextReviewDate = targetDate.toISOString().split('T')[0];
    } else {
      // 失敗時はリセット（翌日再出題）
      wordObj.interval = 0;
      let tomorrow = new Date();
      tomorrow.setDate(tomorrow.getDate() + 1);
      wordObj.nextReviewDate = tomorrow.toISOString().split('T')[0];
    }
  }

  // 統計・苦手ランキング表示
  function renderStats() {
    // ランキング描画
    const sorted = [...words].sort((a, b) => b.failCount - a.failCount).slice(0, 10);
    const rankingEl = document.getElementById('ranking-list');
    rankingEl.innerHTML = sorted.length === 0 ? '<p style="color:#888;">データがありません</p>' : '';
    
    sorted.forEach((w, index) => {
      rankingEl.innerHTML += `
        <div class="ranking-item">
          <span><strong>${index + 1}. ${w.word}</strong> (${w.meaning})</span>
          <span style="color:var(--danger); font-weight:bold;">ミス: ${w.failCount}回</span>
        </div>
      `;
    });

    // 履歴描画
    const historyEl = document.getElementById('history-list');
    historyEl.innerHTML = testHistory.length === 0 ? '<p style="color:#888;">履歴がありません</p>' : '';
    
    testHistory.slice(0, 5).forEach(h => {
      historyEl.innerHTML += `
        <div class="ranking-item">
          <span>${h.date}</span>
          <span>スコア: ${h.score} / ${h.total}</span>
        </div>
      `;
    });
  }
</script>
</body>
</html>
