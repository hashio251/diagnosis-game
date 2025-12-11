'use strict'; // 記述ミスをエラーとして表示してくれる（厳格モード）
const userNameInput = document.getElementById('user-name');
const assessmentButton = document.getElementById('assessment');
const resultDivision = document.getElementById('result-area');
const tweetDivision = document.getElementById('tweet-area');

assessmentButton.addEventListener( // イベント検知設定の追加
  'click', // クリックイベント
  () => { // 無名関数でアロー関数、イベント検知したら実行される
    const userName = userNameInput.value; // 入力欄（input）の値が取れる
    if (userName.length === 0) { // 入力が空だったら
      return; // 関数の処理を終了させる
    }

// 診断結果表示エリアの作成
resultDivision.innerText = '' // divタグをから文字で上書きすることで、空にしている
// headerDivision の作成
const headerDivision = document.createElement('div'); // divタグの作成
headerDivision.setAttribute('class', 'card-header text-bg-primary');
headerDivision.innerText = '診断結果'; // タグの内側のテキストを設定
resultDivision.appendChild(headerDivision); // divタグの子要素として追加

// bodyDivisionの作成
const bodyDivision = document.createElement('div');
bodyDivision.setAttribute('class', 'card-body'); //bootstrap用のclassを設定
const paragraph = document.createElement('p'); //pタグの作成
paragraph.setAttribute('class', 'card-text'); // class設定
const result = assessment(userName);
paragraph.innerText = result; // 診断結果を作成
bodyDivision.appendChild(paragraph)
resultDivision.appendChild(bodyDivision); // divタグの内側のテキストを設定

// resultDivision に Bootstrap のスタイルを適用する
resultDivision.setAttribute('class', 'card');

// headerDivision と bodyDivision を resultDivision に差し込む
resultDivision.appendChild(headerDivision);
resultDivision.appendChild(bodyDivision);

// X投稿ボタンの作成
// (ツイートエリアが診断結果を押した際に消える動作の作成)
tweetDivision.innerText = ''; // Tweetのdivタグもからにする
const anchor = document.createElement('a'); // aタグの作成
const hrefValue = 'https://twitter.com/intent/tweet?button_hashtag=' + encodeURIComponent('あなたのいいところ') + '&ref_src=twsrc%5Etfw';

anchor.setAttribute('href', hrefValue); // href属性を追加
anchor.setAttribute('class', 'twitter-hashtag-button'); // class属性を追加
anchor.setAttribute('data-text', result); // 診断結果を追加
anchor.innerText = 'あなたのいいところを投稿する。'; // ボタンの文章

tweetDivision.appendChild(anchor) // divの子要素として追加

const script = document.createElement('script');
script.setAttribute('src', 'https://platform.twitter.com/widgets.js');
tweetDivision.appendChild(script) // divの子要素として追加


    console.log(assessment(userName)); // ログ出力をする
  }
);

userNameInput.addEventListener(
  'keydown',
  (evnt) => {
    if (event.code === 'Enter') {
      assessmentButton.dispatchEvent(new Event('click'))
    }
  }
)

const answers = [ // letは変数、constは定数（定数は変えられない）
  '###userName###のいいところは声です。###userName###の特徴的な声は皆を惹きつけ、心に残ります。',
  '###userName###のいいところはまなざしです。###userName###に見つめられた人は、気になって仕方がないでしょう。',
  '###userName###のいいところは情熱です。###userName###の情熱に周りの人は感化されます。',
  '###userName###のいいところは厳しさです。###userName###の厳しさがものごとをいつも成功に導きます。',
  '###userName###のいいところは知識です。博識な###userName###を多くの人が頼りにしています。',
  '###userName###のいいところはユニークさです。###userName###だけのその特徴が皆を楽しくさせます。',
  '###userName###のいいところは用心深さです。###userName###の洞察に、多くの人が助けられます。',
  '###userName###のいいところは見た目です。内側から溢れ出る###userName###の良さに皆が気を惹かれます。',
  '###userName###のいいところは決断力です。###userName###がする決断にいつも助けられる人がいます。',
  '###userName###のいいところは思いやりです。###userName###に気をかけてもらった多くの人が感謝しています。',
  '###userName###のいいところは感受性です。###userName###が感じたことに皆が共感し、わかりあうことができます。',
  '###userName###のいいところは節度です。強引すぎない###userName###の考えに皆が感謝しています。',
  '###userName###のいいところは好奇心です。新しいことに向かっていく###userName###の心構えが多くの人に魅力的に映ります。',
  '###userName###のいいところは気配りです。###userName###の配慮が多くの人を救っています。',
  '###userName###のいいところはそのすべてです。ありのままの###userName###自身がいいところなのです。',
  '###userName###のいいところは自制心です。やばいと思ったときにしっかりと衝動を抑えられる###userName###が皆から評価されています。'
];

// assessmentは繰り返し使える
// charCodeAtは文字コード番号を教えてくれる

/**                 ←JSDog
 * 名前の文字列を渡すと診断結果を返す関数
 * @param {string} userName ユーザーの名前
 * @return {string} 診断結果
 */
function assessment(userName) { // 全文字コード番号を取得してそれぞれを足し合わせる
  let sumOfCharCode = 0; // 文字コードの合計を取っておく変数
  for (let i = 0; i < userName.length; i++) { // 文字数回ループ
    sumOfCharCode = sumOfCharCode + userName.charCodeAt(i); // 合計を計算
  }

  // 合計値を配列の要素数であまりを撮ることで、配列の要素数の数値に収める
  // 文字のコード番号の合計を回答の数で割って添え字の数値を求める
  const index = sumOfCharCode % answers.length;
  let result = answers[index]; // 配列から答えを取得
  // TODO ###userName### をユーザの名前に置き換える
  result = result.replaceAll('###userName###', userName)
  return result; // 診断結果を返す
}

// console.assert() 関数はデバッグ用の関数で、指定した条件が false の場合にのみコンソールにエラーメッセージを出力し、条件が true の場合は何も表示されない
// テストを行う関数
function test() {
  console.log('診断結果の文章のテスト');

  //太郎
  console.log('太郎');
  console.assert(
    assessment('太郎') ===
      '太郎のいいところは決断力です。太郎がする決断にいつも助けられる人がいます。',
    '診断結果の文言の特定の部分を名前に置き換える処理が正しくありません。'
  );

  //次郎
  console.log('次郎');
  console.assert(
    assessment('次郎') ===
      '次郎のいいところは自制心です。やばいと思ったときにしっかりと衝動を抑えられる次郎が皆から評価されています。',
    '診断結果の文言の特定の部分を名前に置き換える処理が正しくありません。'
  );

  //花子
  console.log('花子');
  console.assert(
    assessment('花子') ===
      '花子のいいところはまなざしです。花子に見つめられた人は、気になって仕方がないでしょう。',
    '診断結果の文言の特定の部分を名前に置き換える処理が正しくありません。'
  );
  
  console.log('診断結果の文章のテスト終了');
}

test();



