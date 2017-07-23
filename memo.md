# Javascriptのメモ

## 基本的な書き方・ルール

### 記法

* `<script>`要素の中にコードを記述していく。
* 基本的には `</body>`閉じタグの直前に書く。
  * `</body>`タグの直前に記載することで、ページの表示後にスクリプトを読み込むのでページ表示の高速化につながる。
* 文の末尾には `;` （セミコロン）を付ける。
  * 付けなくても動くが、非推奨。
* 大文字と小文字は厳密に区別される。
* コメントは３つの記法が可能。
  * `// comment` ： 単一行コメント。
  * `/* comment */` ： 複数行コメント。
  * `/** comment */` ： ドキュメンテーションコメント。javadoc的なやつ。
  * 基本的には単一行コメントを優先的に使用する。

```html
<body>
    <script type="text/javascript">
        window.alert("Hello World");
    </script>
</body>
```

* Javascriptを外部ファイルにする場合、`<script>`タグの `src` 属性にjavascriptファイルのパスを記載する。
* 外部ファイルの読み込みを行う場合、`<script>`要素内のコードは無視される。

```html
<body>
    <script type="text/javascript" src="./javascript/common.js">
        window.alert("Hello World"); // これは無視される
    </script>
</body>
```

* Javascriptが無効な場合に代替コンテンツを表示させるには、`<noscript>` タグを用いる。

```html
<body>
    <noscript>Javascriptが有効ではありません。</noscript>
</body>
```

* アンカータグにスクリプトを埋め込むこともできる。
* その場合、「`Javascript:~`」の形式で記述する。
* 以下の例だと、aタグの`href`属性にスクリプトを埋め込んでおり、リンクをクリックする度にダイアログが表示される。

```html
<a href="Javascript: window.alert('Hello World');" >ダイアログ表示</a>
```

### 変数・定数

* 変数の宣言は `var 変数名 [=初期値];` で行う。
* 複数の変数を `,` （カンマ）区切りで記述することもできる。

```javascript
var msg; // msgという変数を定義
var x, y; // 複数定義
var hello = 'Hello World'; // 変数の定義と同時に、初期値を設定。
```

* 変数を宣言する命令として `var` 以外に、`let` 命令が使用できる。
* `let`命令は、ES2015から追加された。
* `var` との違いは以下。
  * 変数名の重複を許可しない。
  * ブロックスコープを認識する。

```javascript
// varの場合、変数名の重複は許可されている。
var x = 'hello';
var x = 'world';

// letの場合、変数目の重複は許可されない。
let msg = 'hello';
let msg = 'world'; // 重複ダメ、ぜったい。
```

ブロックスコープについては、あとで説明。<br/>
とりあえず、`var` よりも「変数の有効範囲を細かく管理できる」と理解する。



## 分からなかった単語

* アンカータグ
  * 他ページへのリンクを貼ったり、他の要素への参照時に利用されるタグのこと。
  * `href`属性, `id`属性, `name`属性などがアンカータグにあたる。
