勝手に日本語化シリーズ、今回は React の公式 Tutorial にチャレンジします。例によってわかりづらいところはかなり言葉を足しています。

<a href="https://facebook.github.io/react/tutorial/tutorial.html" target="_blank" rel="noopener noreferrer">https://facebook.github.io/react/tutorial/tutorial.html</a>
<h1>Tutorial: Intro To React</h1>
<div class="subHeader">チュートリアル：React への案内</div>
<h2><a class="anchor" name="before-we-start"></a>Before We Start</h2>
始める前に
<h3><a class="anchor" name="what-were-building"></a>What We're Building</h3>
作るもの

Today, we're going to build an interactive tic-tac-toe game.

今日は、3目並べゲームを作っていきます。これはユーザー操作を受付け、それに反応して進んでいく、インタラクティブなゲームです。

If you like, you can check out the final result here: <a href="https://codepen.io/gaearon/pen/gWWZgR?editors=0010">Final Result</a>. Don't worry if the code doesn't make sense to you yet, or if it uses an unfamiliar syntax. We will be learning how to build this game step by step throughout this tutorial.

完成形をこちらから見ることもできます。でも、今のところ、コードが何を意味しているのかわからなくても、使われているシンタックスが見慣れないものであっても、心配しないで大丈夫です。これから段階的に、このゲームを作る方法を、チュートリアルを通して学んでいきましょう。

Try playing the game. You can also click on a link in the move list to go "back in time" and see what the board looked like just after that move was made.

まずは実際にゲームをプレイしてみてください。右側にある「move list」をクリックして、「時間を逆戻し」することもできます。これは使えば、その手を打った直後の状態に戻ることができます。

Once you get a little familiar with the game, feel free to close that tab, as we'll start from a simpler template in the next sections.

ゲームの概要が大体理解できたら、タブを閉じて、まずはシンプルなテンプレートを作るところから始めていきましょう。
<h3><a class="anchor" name="prerequisites"></a>Prerequisites</h3>
前準備

We'll assume some familiarity with HTML and JavaScript but you should be able to follow along even if you haven't used them before.

ある程度 HTML と JavaScript に慣れている前提で進めていきますが、全くそれらの知識がないかたも理解することは出来ると思います。

If you need a refresher on JavaScript, we recommend reading <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript">this guide</a>. Note that we're also using some features from ES6, a recent version of JavaScript. In this tutorial, we're using <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions">arrow functions</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes">classes</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let"><code>let</code></a>, and <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const"><code>const</code></a> statements. You can use <a href="http://babeljs.io/repl/#?babili=false&amp;evaluate=true&amp;lineWrap=false&amp;presets=es2015%2Creact&amp;experimental=false&amp;loose=false&amp;spec=false&amp;code=const%20element%20%3D%20%3Ch1%3EHello%2C%20world!%3C%2Fh1%3E%3B%0Aconst%20container%20%3D%20document.getElementById('root')%3B%0AReactDOM.render(element%2C%20container)%3B%0A">Babel REPL</a> to check what ES6 code compiles to.

過去に JS を書いていたけれどしばらく離れていて、久しぶりに JS に戻ってきた人には、このガイドを読むことをおすすめします。直近の JS バージョンである ES6 をの機能を使っていきますので。このチュートリアルでは、ES6の機能から、arrow functions, classes, それから let と const よる変数の宣言を用いていきます。<a href="http://babeljs.io/repl/#?babili=false&amp;evaluate=true&amp;lineWrap=false&amp;presets=es2015%2Creact&amp;experimental=false&amp;loose=false&amp;spec=false&amp;code=const%20element%20%3D%20%3Ch1%3EHello%2C%20world!%3C%2Fh1%3E%3B%0Aconst%20container%20%3D%20document.getElementById('root')%3B%0AReactDOM.render(element%2C%20container)%3B%0A">Babel REPL</a>を使えば ES6 のコードがどのようにコンパイルされるか確認するこができます。(訳注：フロントエンドをされている人には特に説明は必要ないとは思いますが、現在 gulp 等のタスクマネージャーを用いて、先行して策定されたバージョンであるES6で書いたJSを、ブラウザが認識できる現行のJSへとトランスコンパイルするのが標準的なワークフローです。ES6に馴染みがない、Gulp等に馴染みがない、という人は上記のガイドを参照するといいよ、とのことです。)

<!--more-->
<h3><a class="anchor" name="how-to-follow-along"></a>How to Follow Along</h3>
作業方法

There are two ways to complete this tutorial: you could either write the code right in the browser, or you could set up a local development environment on your machine. You can choose either option depending on what you feel comfortable with.

このチュートリアルに取り組むための方法は2つあります。コードをブラウザで直接書く方法(訳注：Codepenを使っていく方法です)、もしくはローカル開発環境をつくってそこでコーディングする方法の２つです。自分が好きな方を選択してください。
<h4><a class="anchor" name="if-you-prefer-to-write-code-in-the-browser"></a>If You Prefer to Write Code in the Browser</h4>
ブラウザでコーディングしたい場合

This is the quickest way to get started!

これが、一番早く始めることのできる方法です。

First, open this <a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0010">starter code</a> in a new tab. It should display an empty tic-tac-toe field. We will be editing that code during this tutorial.

まずはこのリンクを開いてください。中に何も記録されていない、三目揃えゲームが表示されます。このコードをチュートリアルの中で書き換えていきます。

You can now skip the next section about setting up a local development environment and head straight to the <a href="https://facebook.github.io/react/tutorial/tutorial.html#overview">overview</a>.

この方法を選ぶ場合は、次のローカル開発環境のセクションは飛ばして、overvieまで進みましょう。
<h4><a class="anchor" name="if-you-prefer-to-write-code-in-your-editor"></a>If You Prefer to Write Code in Your Editor</h4>
自分のエディターでコーディングしたい場合

Alternatively, you can set up a project on your computer.

自分のコンピューター内にプロジェクトを立ち上げてコーディングする方法もあります。

Note: <strong>this is completely optional and not required for this tutorial!</strong>

アドバイス：このチュートリアルをおこなうためには必須ではありません。任意の選択肢です。

This is more work, but lets you work from the comfort of your editor.

これを選択する場合にはブラウザでコーディングする場合よりも追加の作業が必要になりますが、しかし慣れ親しんだエディターで作業をすることができます。

If you want to do it, here are the steps to follow:

その場合には、次の作業をおこなってください。
<ol>
 	<li>Make sure you have a recent version of <a href="https://nodejs.org/en/">Node.js</a> installed.
最近のバージョンのNode.jsをインストールします。</li>
 	<li>Follow the <a href="https://facebook.github.io/react/docs/installation.html#creating-a-new-application">installation instructions</a> to create a new project.
次の記事を読んで新しいプロジェクトを作成してください。(訳注：NPMであるcreate-react-appを使ってコマンドラインから一発で開発環境を作成できます)</li>
 	<li>Delete all files in the <code>src/</code> folder of the new project.
src/以下のフォルダーを全て削除。</li>
 	<li>Add a file named <code>index.css</code> in the <code>src/</code> folder with <a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0100">this CSS code</a>.
index.css という名前のファイルをsrc/の下に配置し、<a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0100">this CSS code</a> の内容をコピー。</li>
 	<li>Add a file named <code>index.js</code> in the <code>src/</code> folder with <a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0010">this JS code</a>, and then add three lines to the top of it:
index.js という名前のファイルをsrc/の下に配置し、<a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0010">this JS code</a> の内容をコピー。さらに次の3行を冒頭に追加してください。
<div class="highlight">
<pre><code class="language-js" data-lang="js"><span class="kr">import</span> <span class="nx">React</span> <span class="nx">from</span> <span class="s1">'react'</span><span class="p">;</span>
<span class="kr">import</span> <span class="nx">ReactDOM</span> <span class="nx">from</span> <span class="s1">'react-dom'</span><span class="p">;</span>
<span class="kr">import</span> <span class="s1">'./index.css'</span><span class="p">;</span>
</code></pre>
</div></li>
</ol>
Now if you run <code>npm start</code> in the project folder and open <code>http://localhost:3000</code> in the browser, you should see an empty tic-tac-toe field.

ここまで準備が整ったら、run npm start をして http://localhost:3000 をブラウザで開けば、空の三目並べゲームが現れます。

We recommend following <a href="http://babeljs.io/docs/editors">these instructions</a> to configure syntax highlighting for your editor.

次の記事を読んで、エディターのハイライト機能を設定することをおすすめします。
<h3><a class="anchor" name="help-im-stuck"></a>Help, I'm Stuck!</h3>
助けて！ハマったよ！

If you get stuck, check out the <a href="https://facebook.github.io/react/community/support.html">community support resources</a>. In particular, <a href="https://facebook.github.io/react/community/support.html#reactiflux-chat">Reactiflux chat</a> is a great way to get quick help. If you don't get a good answer anywhere, please file an issue, and we'll help you out.

行き詰まってしまった場合に、React コミュニティが用意した様々なリソースを参照してください。とくに、<a href="https://facebook.github.io/react/community/support.html#reactiflux-chat">Reactiflux chat</a> はすぐに助けをもらえる素晴らしい方法です。(訳注：英語で質問しないといけないですが…日本のReactコミュニティのslackもきっとあるはず！自分は知らないですが…) もしどのリソースを参照しても解決できない場合には、それをまとめて私たちに送ってください。きっと手助けできるはずです。

With this out of the way, let's get started!

では始めましょう！
<h2>Overview</h2>
概要
<h3><a class="anchor" name="what-is-react"></a>What is React?</h3>
React とは？

React is a declarative, efficient, and flexible JavaScript library for building user interfaces.

React は declarative(訳注：宣言的プログラミングという分類があるようですが、わたしにはわからないので原語のままにしておきます)かつフレキシブルなJavaScript ライブラリで、ユーザーインターフェースの作成のために用いることができます。

React has a few different kinds of components, but we'll start with <code>React.Component</code>subclasses:

React はそれほど多くはありませんが、しかし異なる種類のコンポーネントを幾つか持っています。その中からまずは React.component というサブクラスから始めていきましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span style="font-size: 18pt;"><strong><span class="nx" style="color: #008000;">ShoppingList</span></strong></span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span style="color: #ff6600;"><strong><span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"shopping-list"</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">h1</span><span class="o">&gt;</span><span class="nx">Shopping</span> <span class="nx">List</span> <span class="k">for</span> <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">name</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/h1&gt;</span>
        <span class="o">&lt;</span><span class="nx">ul</span><span class="o">&gt;</span>
          <span class="o">&lt;</span><span class="nx">li</span><span class="o">&gt;</span><span class="nx">Instagram</span><span class="o">&lt;</span><span class="err">/li&gt;</span>
          <span class="o">&lt;</span><span class="nx">li</span><span class="o">&gt;</span><span class="nx">WhatsApp</span><span class="o">&lt;</span><span class="err">/li&gt;</span>
          <span class="o">&lt;</span><span class="nx">li</span><span class="o">&gt;</span><span class="nx">Oculus</span><span class="o">&lt;</span><span class="err">/li&gt;</span>
        <span class="o">&lt;</span><span class="err">/ul&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span></strong></span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>

<span class="c1">// Example usage: &lt;ShoppingList name="Mark" /&gt;</span>
</code></pre>
</div>
We'll get to the funny XML-like tags in a second. Your components tell React what you want to render – then React will efficiently update and render just the right components when your data changes.

まずは、ちょっと変わった、しかしXMLに似ているタグを見てきましょう。あなたがコンポーネントを書くと、それは React へ、どのような物をレンダリングしたらいいのかを伝えます。そしてそれを伝え聞いた React はその通りコンポーネントをレンダリングし、またデータに変更があればコンポーネントを効率的に更新し、再レンダリングを行います。

Here, ShoppingList is a <strong>React component class</strong>, or <strong>React component type</strong>. A component takes in parameters, called <code>props</code>, and returns a hierarchy of views to display via the <code>render</code>method.

この例では、ShoppingList が<strong>React component </strong>クラスです。 もしくは <strong>React component </strong>形式であるといってもよいでしょう。Component は props と呼ばれる引数を受取り、render メソッドと、その中にある returnによって、構造化された view を返します。(訳注：view は後にレンダリングされて、表示される内容のこと)

The <code>render</code> method returns a <em>description</em> of what you want to render, and then React takes that description and renders it to the screen. In particular, <code>render</code> returns a <strong>React element</strong>, which is a lightweight description of what to render. Most React developers use a special syntax called JSX which makes it easier to write these structures. The <code>&lt;div /&gt;</code> syntax is transformed at build time to <code>React.createElement('div')</code>. The example above is equivalent to:

Render メソッドはレンダーする内容を return し、そして React がそれを受け取って、その内容をレンダリングし、スクリーンに表示します。Render メソッドが返しているものは、React element というもので、これにはレンダー内容が含まれているわけですが、軽量な点が特徴です。React 開発者のほとんどは、JSX という専用の構文を使ってこれらの構造を記述します。JSX を使うことでより簡単に書くことが可能になるからです。実際にはこのJSX構文はどのように処理されるのでしょうか。例えば&lt;div/&gt;というJSX構文は、ビルド時にReact.createElement('div') へと変形されます。また、今取り上げているザッカーバーグのショッピングリストクラスのサンプルは、次のように変形されられます。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="k">return</span> <span class="nx">React</span><span class="p">.</span><span class="nx">createElement</span><span class="p">(</span><span class="s1">'div'</span><span class="p">,</span> <span class="p">{</span><span class="nx">className</span><span class="o">:</span> <span class="s1">'shopping-list'</span><span class="p">},</span>
  <span class="nx">React</span><span class="p">.</span><span class="nx">createElement</span><span class="p">(</span><span class="s1">'h1'</span><span class="p">,</span> <span class="cm">/* ... h1 children ... */</span><span class="p">),</span>
  <span class="nx">React</span><span class="p">.</span><span class="nx">createElement</span><span class="p">(</span><span class="s1">'ul'</span><span class="p">,</span> <span class="cm">/* ... ul children ... */</span><span class="p">)</span>
<span class="p">);</span>
</code></pre>
</div>
<a href="https://babeljs.io/repl/#?babili=false&amp;evaluate=false&amp;lineWrap=false&amp;presets=react&amp;targets=&amp;browsers=&amp;builtIns=false&amp;debug=false&amp;experimental=false&amp;loose=false&amp;spec=false&amp;playground=true&amp;code=%3Cdiv%20className%3D%22shopping-list%22%3E%0A%20%20%3Ch1%3EShopping%20List%20for%20%7Bprops.name%7D%3C%2Fh1%3E%0A%20%20%3Cul%3E%0A%20%20%20%20%3Cli%3EInstagram%3C%2Fli%3E%0A%20%20%20%20%3Cli%3EWhatsApp%3C%2Fli%3E%0A%20%20%20%20%3Cli%3EOculus%3C%2Fli%3E%0A%20%20%3C%2Ful%3E%0A%3C%2Fdiv%3E">See full expanded version.</a>

If you're curious, <code>createElement()</code> is described in more detail in the <a href="https://facebook.github.io/react/docs/react-api.html#createelement">API reference</a>, but we won't be using it directly in this tutorial. Instead, we will keep using JSX.

さらに createElement() へ興味があれば <a href="https://facebook.github.io/react/docs/react-api.html#createelement">API reference</a> に詳細が書かれていますので参考にしてください。このレクチャーにおいては createElement() ではなくて JSX を用いていくことにします。

You can put any JavaScript expression within braces inside JSX. Each React element is a real JavaScript object that you can store in a variable or pass around your program.

JSX コード内の {} の中には、どのような JavaScript 表現をも書くことができます。 React element は全て純粋な JavaScript オブジェクトなので、変数の中にこれを保持したり、引数として渡すことが可能です。

The <code>ShoppingList</code> component only renders built-in DOM components, but you can compose custom React components just as easily, by writing <code>&lt;ShoppingList /&gt;</code>. Each component is encapsulated so it can operate independently, which allows you to build complex UIs out of simple components.

先のShoppingList コンポーネントがレンダリングしているのは、もとから用意されている DOM (訳注：divやh1といったHTMLの規格で元から用意されている要素) しか含まれないコンポーネントですが、このカスタム React component を組み立てる (訳注：単に使うということ) 方法は非常に簡単で、&lt;ShoppingList /&gt;と書くだけです。それぞれのコンポーネントはカプセル化されているので、それぞれ独立して運用することが可能で、これによって複雑な UI をシンプルなコンポーネントの組み合わせによって作成することができます。

(訳注(英辞郎からそのままコピペ)：カプセル化する◆オブジェクト指向プログラミングで使用される技法の一つ。薬をカプセルに入れるかのごとく、データとそれらを操作する関数を一つの構造体としてまとめてオブジェクトに格納することにより、内部で行われる処理を外部から隠し、オブジェクトに対するアクセス方法を限定する。)
<h3><a class="anchor" name="getting-started"></a>Getting Started</h3>
始めよう

Start with this example: <a href="https://codepen.io/gaearon/pen/oWWQNa?editors=0010">Starter Code</a>.

まずはこのサンプルから始めることにしましょう。

It contains the shell of what we're building today. We've provided the styles so you only need to worry about the JavaScript.

このサンプルには、これから作っていくアプリケーションの骨格だけが含まれています。CSS スタイルも既にこれに含まれていますので、これからの作業においては JavaScript についてだけ考えていだければよいということになります。

In particular, we have three components:

具体的には、3つのコンポーネントについて作業をしていきます。
<ul>
 	<li>Square</li>
 	<li>Board</li>
 	<li>Game</li>
</ul>
The Square component renders a single <code>&lt;button&gt;</code>, the Board renders 9 squares, and the Game component renders a board with some placeholders that we'll fill in later. None of the components are interactive at this point.

Square コンポーネントは&lt;button&gt;だけをレンダリングするコンポーネントで、Board コンポーネントは 9個の Square コンポーネントをレンダリングするコンポーネントです。Game コンポーネントは Board を一つレンダリングします。これには幾つかの情報を表示するエリアを持っていて、後ほど実装することになります。
<h3><a class="anchor" name="passing-data-through-props"></a>Passing Data Through Props</h3>
データを Props を用いて渡す

Just to get our feet wet, let's try passing some data from the Board component to the Square component.

さあまずは、データを渡してみることにしましょう。Board コンポーネントから Square コンポーネントへとデータをわたします。

In Board's <code>renderSquare</code> method, change the code to pass a <code>value</code> prop to the Square:

Board コンポーネント内にある renderSquare メソッドに変更を加え、value という名前の prop (訳注：何かを支えたり、助けるために使う棒のこと)　を Square コンポーネントに渡すようにします。
<div class="highlight">
<pre><code class="language-js" data-lang="js"><span class="kr">class</span> <span class="nx">Board</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
<span class="hll">    <span class="k">return</span> <span class="o">&lt;</span><span class="nx">Square</span> <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="nx">i</span><span class="p">}</span> <span class="o">/&gt;</span><span class="p">;</span>
</span>  <span class="p">}</span>
</code></pre>
</div>
Then change Square's <code>render</code> method to show that value by replacing <code>{/* TODO */}</code> with <code>{this.props.value}</code>:

次に Square コンポーネント内の render メソッドを変更します。受け取った値を表示できるように、<code>{/* TODO */}</code> を <code>{this.props.value}</code>へと変更してください。
<div class="highlight">
<pre><code class="language-js" data-lang="js"><span class="kr">class</span> <span class="nx">Square</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span><span class="o">&gt;</span>
<span class="hll">        <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
</span>      <span class="o">&lt;</span><span class="err">/button&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
Before:

変更前

<img src="https://facebook.github.io/react/img/tutorial/tictac-empty.png" alt="React Devtools" />

After: You should see a number in each square in the rendered output.

変更後：レンダリング結果をみると、それぞれのマスに数字が表示されているはずです。

<img src="https://facebook.github.io/react/img/tutorial/tictac-numbers.png" alt="React Devtools" />

<a href="https://codepen.io/gaearon/pen/aWWQOG?editors=0010">View the current code.</a>
<h3><a class="anchor" name="an-interactive-component"></a>An Interactive Component</h3>
インタラクティブなコンポーネント(訳注：ユーザー操作を受け付け、それに反応するコンポーネント)

Let's make the Square component fill in an "X" when you click it. Try changing the button tag returned in the <code>render()</code> function of the Square like this:

では次に、クリックした時に"X"が表示されるよう Square コンポーネントを変更していきましょう。Square コンポーネント内の render 関数が返す(訳注：JSのreturnで返してくる部分です) button タグに変更を加えます。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Square</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
<span class="hll">      <span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="nx">alert</span><span class="p">(</span><span class="s1">'click'</span><span class="p">)}</span><span class="o">&gt;</span>
</span>        <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
      <span class="o">&lt;</span><span class="err">/button&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
If you click on a square now, you should get an alert in your browser.

すると、マス目をクリックした際に、アラートがブラウザに表示されるはずです。

This uses the new JavaScript <a href="https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions">arrow function</a> syntax. Note that we're passing a function as the <code>onClick</code> prop. Doing <code>onClick={alert('click')}</code> would alert immediately instead of when the button is clicked.

このコードは JavaScript の新しいアローファンクション構文を使っています。注意してほしいでのですが、ここで渡しているのは関数です。もし onClick={alert('click')} としてしまうと(訳注：関数ではなくて直接 alert の実行文を書いてしまうと) ボタンがクリックした時に動作するのではなく、即座にアラートが発生してしまいます。

React components can have state by setting <code>this.state</code> in the constructor, which should be considered private to the component. Let's store the current value of the square in state, and change it when the square is clicked.

React のコンポーネントは、コンストラクター内に this.state を設置することで、状態=stateを保持することができます。これは他のコンポーネントに対して private です。では、マス目の現在の値を state 内に保持し、クリックされたときには変更されるように、コードを書き換えていきましょう。

(英辞郎より引用：プライベートな◆あるオブジェクトに属するメンバーが、そのオブジェクトの内部でのみアクセス可能であること。訳さずに「privateな」と表現されることも多い。)

First, add a constructor to the class to initialize the state:

まずはコンストラクタをクラス内に追加して、state 状態を初期化するようにします。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Square</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
<span class="hll">  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
</span><span class="hll">    <span class="kr">super</span><span class="p">();</span>
</span><span class="hll">    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">value</span><span class="o">:</span> <span class="kc">null</span><span class="p">,</span>
</span><span class="hll">    <span class="p">};</span>
</span><span class="hll">  <span class="p">}</span>
</span>
  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="nx">alert</span><span class="p">(</span><span class="s1">'click'</span><span class="p">)}</span><span class="o">&gt;</span>
        <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
      <span class="o">&lt;</span><span class="err">/button&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
In <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes">JavaScript classes</a>, you need to explicitly call <code>super();</code> when defining the constructor of a subclass.

JSのクラスにおいては、コンストラクタを、あるクラスのサブクラスのコンストラクタとして定義するためには、明示的にsuper();を宣言する必要があります。

Now change the Square <code>render</code> method to display the value from the current state, and to toggle it on click:

では Square コンポーネント内の render メソッドを変更して、現在の状態 state を表示し、またクリックされた際には状態が変更されるようにしましょう。
<ul>
 	<li>Replace <code>this.props.value</code> with <code>this.state.value</code> inside the <code>&lt;button&gt;</code> tag.
this.props.valueを変更し、this.state.valueにしてください。これは&lt;button&gt;タグの中にあります。</li>
 	<li>Replace the <code>() =&gt; alert()</code> event handler with <code>() =&gt; this.setState({value: 'X'})</code>.
<code>() =&gt; alert()</code> というイベントハンドラーの内容を変更して、 <code>() =&gt; this.setState({value: 'X'})</code> とします。</li>
</ul>
Now the <code>&lt;button&gt;</code> tag looks like this:

この変更を加えると、&lt;button&gt;タグは次のようになっているはずです。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Square</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">super</span><span class="p">();</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
      <span class="nx">value</span><span class="o">:</span> <span class="kc">null</span><span class="p">,</span>
    <span class="p">};</span>
  <span class="p">}</span>

  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
<span class="hll">    <span class="k">return</span> <span class="p">(</span>
</span><span class="hll">      <span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span><span class="nx">value</span><span class="o">:</span> <span class="s1">'X'</span><span class="p">})}</span><span class="o">&gt;</span>
</span><span class="hll">        <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
</span>      <span class="o">&lt;</span><span class="err">/button&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
Whenever <code>this.setState</code> is called, an update to the component is scheduled, causing React to merge in the passed state update and rerender the component along with its descendants. When the component rerenders, <code>this.state.value</code> will be <code>'X'</code> so you'll see an X in the grid.

this.setState メソッドが実行されると、コンポーネントへのアップデートが予定に組み込まれます。そしてそれによって React は、受け取った状態 state への更新を、現在の state へとマージした上で、コンポーネントをその子コンポーネントも含めて、再レンダリングします。このコンポーネントの再レンダリングの際には、this.state.value の値は "X" へと変更されているので、結果としてグリッド内には X が表示されることになります。

If you click on any square, an X should show up in it.

どのマス目をクリックしても、X が現れるようになりました。

<a href="https://codepen.io/gaearon/pen/VbbVLg?editors=0010">View the current code.</a>
<h3><a class="anchor" name="developer-tools"></a>Developer Tools</h3>
開発者用ツール

The React Devtools extension for <a href="https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en">Chrome</a> and <a href="https://addons.mozilla.org/en-US/firefox/addon/react-devtools/">Firefox</a> lets you inspect a React component tree in your browser devtools.

React 用の開発者向け拡張機能が、Chrome と Firefox において用意されています。これを使うと、リアクトコンポーネントのツリーをブラウザから確認することができます。

<img src="https://facebook.github.io/react/img/tutorial/devtools.png" alt="React Devtools" />

It lets you inspect the props and state of any of the components in your tree.

コンポーネントツリー内の、全ての props と 状態 state を確認することができます。

After installing it, you can right-click any element on the page, click "Inspect" to open the developer tools, and the React tab will appear as the last tab to the right.

ツールの使い方ですが、まずこのツールをインストールした後、ページ上の要素の上で右クリックをして、"検証する"を選んでディベロッパーツールを開きます。その後、React tab がタブの一番右側にあるはずなので、これを開きます。

<strong>However, note there are a few extra steps to get it working with CodePen:</strong>

ただしCodePen内でこのツールを使うためには、いくつか追加の設定が必要です。
<ol>
 	<li>Log in or register and confirm your email (required to prevent spam).
ログインもしくは新しくアカウントを登録した上で、アカウントの Email 確認を済ませておく。(これはスパムだと認定されないために必要です)</li>
 	<li>Click the "Fork" button.
Fork ボタンを押す</li>
 	<li>Click "Change View" and then choose "Debug mode".
Change View ボタンを押して、その後にDebug mode を選ぶ。</li>
 	<li>In the new tab that opens, the devtools should now have a React tab.
それによって開いた新しいタブの中では、ディベロッパーツールがReact タブを表示してくれます。</li>
</ol>
<h2>Lifting State Up</h2>
状態を保持する階層を上の階層へ持ち上げる

We now have the basic building blocks for a tic-tac-toe game. But right now, the state is encapsulated in each Square component. To make a fully-working game, we now need to check if one player has won the game, and alternate placing X and O in the squares. To check if someone has won, we'll need to have the value of all 9 squares in one place, rather than split up across the Square components.

さあここまでの作業で、基本的なゲームの構造を作り終えました。しかし現時点では、状態はそれぞれ Square コンポーネントの内部にカプセル化されています。このゲームが意図したとおりに動いてもらうためには、さらに機能を追加しないといけません。どのプレイヤーが勝ったのかをチェックする機能と、それからプレイヤーがクリックした時に現れるマークを、XマークとOマークへと交互に入れ替える機能です。誰が勝者なのかを判断する機能をつけるためには、9個のマス目の値を全て、1箇所で保持する必要があります。それぞれの Square コンポーネントに散在していていはいけまんせん。

You might think that Board should just inquire what the current state of each Square is. Although it is technically possible to do this in React, it is discouraged because it tends to make code difficult to understand, more brittle, and harder to refactor.

そんなことをしなくても、Board コンポーネントが、Square の中にある現在の状態 state を全て問い合わせればいいではないか、と考えたかもしれません。もちろん技術的にそうすることは可能ですが、あまりおすすめできません。何故かというと、そうしてしまうとコードが複雑になって理解しづらく、容易に破綻しやすくなってしまい、リファクタリングもやりにくいコードになってしまいます。

Instead, the best solution here is to store this state in the Board component instead of in each Square – and the Board component can tell each Square what to display, like how we made each square display its index earlier.

ではどうするのがいいかというと、状態を Board コンポーネントに持たせればよいのです。つまり Square コンポーネントそれぞれには、状態を持たせません。そのうえで、Board コンポーネントが、それぞれの Square コンポーネントに対して、何を表示すべきなのかその内容を伝えるようにします。これはちょうど、我々が既に作業した Square に 自分の番号を表示させた時にやり方と似ています。

(訳注：一つ階層上にあるBoardからpropsを受取り、Square はそれをthis.props.valueという構文によってそれを表示していた)
<pre><code class="language-js" data-lang="js"><span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span><span class="o">&gt;</span>
<span class="hll">        <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
</span>      <span class="o">&lt;</span><span class="err">/button&gt;</span></code></pre>
<strong>When you want to aggregate data from multiple children or to have two child components communicate with each other, move the state upwards so that it lives in the parent component. The parent can then pass the state back down to the children via props, so that the child components are always in sync with each other and with the parent.</strong>

複数の子コンポーネントが持つデータを集計したり、２つの子コンポーネント同士がお互いにデータをやり取りする必要がある場合には、状態 State を上の階層へと譲渡していき、親コンポーネントが状態を持つようにしましょう。親コンポーネントは、子コンポーネントへと props を用いて、下へと伝えて行くことが出来るので、子コンポーネントはいつでも子コンポーネント同士で同期することができます。また子コンポーネントは親コンポーネントとも同期することができます。

Pulling state upwards like this is common when refactoring React components, so let's take this opportunity to try it out. Add a constructor to the Board and set its initial state to contain an array with 9 nulls, corresponding to the 9 squares:

このように、状態を上へと引き上げていく手法は、React のリファクタリングにおいて一般的なものです。良い機会ですから、やってみましょう。Board コンポーネントにコンストラクターを追加し、9マスあるので9つの null 配列を、初期状態として持つように設定します。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Board</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
<span class="hll">  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
</span><span class="hll">    <span class="kr">super</span><span class="p">();</span>
</span><span class="hll">    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">squares</span><span class="o">:</span> <span class="nb">Array</span><span class="p">(</span><span class="mi">9</span><span class="p">).</span><span class="nx">fill</span><span class="p">(</span><span class="kc">null</span><span class="p">),</span>
</span><span class="hll">    <span class="p">};</span>
</span><span class="hll">  <span class="p">}</span>
</span>
  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="o">&lt;</span><span class="nx">Square</span> <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="nx">i</span><span class="p">}</span> <span class="o">/&gt;</span><span class="p">;</span>
  <span class="p">}</span>

  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: X'</span><span class="p">;</span>

    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"status"</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">status</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">0</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">1</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">2</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">3</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">4</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">5</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">6</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">7</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">8</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
We'll fill it in later so that a board looks something like

ここには後ほど次のような値が入る予定です。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="p">[</span>
  <span class="s1">'O'</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="s1">'X'</span><span class="p">,</span>
  <span class="s1">'X'</span><span class="p">,</span> <span class="s1">'X'</span><span class="p">,</span> <span class="s1">'O'</span><span class="p">,</span>
  <span class="s1">'O'</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
<span class="p">]</span>
</code></pre>
</div>
Board's <code>renderSquare</code> method currently looks like this:

Board コンポーネント内の renderSquare メソッドは、現在次のようになっています。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="o">&lt;</span><span class="nx">Square</span> <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="nx">i</span><span class="p">}</span> <span class="o">/&gt;</span><span class="p">;</span>
  <span class="p">}</span>
</code></pre>
</div>
Modify it to pass a <code>value</code> prop to Square.

変更を加え、value という名前のprop を Square コンポーネントへと渡すようにします。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
<span class="hll">    <span class="k">return</span> <span class="o">&lt;</span><span class="nx">Square</span> <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]}</span> <span class="o">/&gt;</span><span class="p">;</span>
</span>  <span class="p">}</span>
</code></pre>
</div>
<a href="https://codepen.io/gaearon/pen/gWWQPY?editors=0010">View the current code.</a>

Now we need to change what happens when a square is clicked. The Board component now stores which squares are filled, which means we need some way for Square to update the state of Board. Since component state is considered private, we can't update Board's state directly from Square.

では次に、マス目がクリックされた時の挙動を変更しましょう。マス目にどのようなマークが記録されているかは、今や Board コンポーネントが保持しています。ですから、「Square コンポーネント」が「Board コンポーネントの状態を変更する方法」を、用意せねばいけません。コンポーネントの状態は private ですから、Board コンポーネントの状態を、Square コンポーネントから直接更新することはできません。

The usual pattern here is pass down a function from Board to Square that gets called when the square is clicked. Change <code>renderSquare</code> in Board again so that it reads:

こういった場合に使われる典型的な設計パターンは、関数を Board コンポーネントから Square コンポーネントへと渡し、Square コンポーネントがクリックされた際に、その渡された関数が実行されるようにすることです。そうなるように、Board コンポーネント内の renderSquare を再度変更しましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">Square</span>
        <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]}</span>
<span class="hll">        <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)}</span>
</span>      <span class="o">/&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
</code></pre>
</div>
We split the returned element into multiple lines for readability, and added parens around it so that JavaScript doesn't insert a semicolon after <code>return</code> and break our code.

return 内の HTML要素の記述箇所においては、可読性を上げるために、複数行に改行しています。さらに丸括弧でそれをくくっています。これは JavaScript がreturn の後ろに semicolon を追加して、コードが破綻しないようにするためです。(訳注：return 改行 &lt;square/&gt; と書いてしまうと、return の後ろにセミコロンを入れて JS が解釈し意図しない挙動になるため、そのようなトラブルが発生しないように、上記のような記法を取っている、ということ。)

Now we're passing down two props from Board to Square: <code>value</code> and <code>onClick</code>. The latter is a function that Square can call. Let's make the following changes to Square:

さて、2つのpropsを、BoardからSquareへと渡すようになりました。2つのpropsはそれぞれ、valueとonClickでしたね。さらに、onClickがSquareから呼び出すことができるよう、変更を Square に対して加えましょう。
<ul>
 	<li>Replace <code>this.state.value</code> with <code>this.props.value</code> in Square's <code>render</code>.
<code>this.state.value</code> を変更し、 <code>this.props.value</code> にする。これは次の場所にある： Square の中の <code>render</code></li>
 	<li>Replace <code>this.setState()</code> with <code>this.props.onClick()</code> in Square's <code>render</code>.
<code>this.setState()</code> を変更し、 <code>this.props.onClick()</code> とする。これは次の中にある：Square の中の <code>render</code>.</li>
 	<li>Delete <code>constructor</code> definition from Square because it doesn't have state anymore.
<code>constructor</code> をSquareコンポーネントから削除する。何故なら Square コンポーネントは状態を既に持っていないので、必要がないから。</li>
</ul>
After these changes, the whole Square component looks like this:

これらの変更を加えた後、Square コンポーネントの全体像は、このようになっているはずです。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="hll"><span class="kr">class</span> <span class="nx">Square</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
</span><span class="hll">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
</span>    <span class="k">return</span> <span class="p">(</span>
<span class="hll">      <span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">onClick</span><span class="p">()}</span><span class="o">&gt;</span>
</span><span class="hll">        <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
</span>      <span class="o">&lt;</span><span class="err">/button&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
Now when the square is clicked, it calls the <code>onClick</code> function that was passed by Board. Let's recap what happens here:

この状態でマス目をクリックすると、Square コンポーネントは onClick 関数を呼び出します。この呼び出される関数は、Board コンポーネントから渡されたものです。(訳注：this.props.onClick()は、Boardから受けとったpropsの中にある関数。)

では今までやってきたことをおさらいしましょう。
<ol>
 	<li>The <code>onClick</code> prop on the built-in DOM <code>&lt;button&gt;</code> component tells React to set up a click event listener.
標準搭載の&lt;button&gt;コンポーネント内に配置された、onClickというpropは、React へ「クリックイベントリスナー」をこのコンポーネントへ設置することを要求する。</li>
 	<li>When the button is clicked, React will call the <code>onClick</code> event handler defined in Square's <code>render()</code> method.
ボタンがクリックされると、ReactはonClickイベントに紐付けられた関数を呼び出す。このイベントへの紐付けは、Square のrender()メソッド内で定義されている。</li>
 	<li>This event handler calls <code>this.props.onClick()</code>. Square's props were specified by the Board.
this.props.onClick()を呼び出す。Square が受け取っている props は、Board コンポーネントの中で定義されている。</li>
 	<li>Board passed <code>onClick={() =&gt; this.handleClick(i)}</code> to Square, so, when called, it runs <code>this.handleClick(i)</code> on the Board.
Board コンポーネントは <code>onClick={() =&gt; this.handleClick(i)}</code> を、Square コンポーネントへと渡しているので、これが呼び出されると、Board コンポーネント内の <code>this.handleClick(i)</code> を実行する。</li>
 	<li>We have not defined the <code>handleClick()</code> method on the Board yet, so the code crashes.
まだ handleClick() メソッドを Board コンポーネント内に定義していないので、この時点ではまだクリックするとクラッシュする。</li>
</ol>
Note that <code>onClick</code> on the DOM <code>&lt;button&gt;</code> component has a special meaning to React, but we could have called <code>onClick</code> prop in Square and <code>handleClick</code> in Board something else. It is, however, a common convention in React apps to use <code>on*</code> names for the handler prop names and <code>handle*</code> for their implementations.

注意してほしいのですが、&lt;button&gt; DOM 内に配置された onClick は、React において特殊な意味を持ちます。しかし同じ onClick という名前をもつ prop を Square コンポーネントにおいて呼び出すことができましたし、handleClick を Board コンポーネントなので呼び出しました。React における慣習として、on* をhandler 用の prop に付け、handle* をその実装に用います。

(訳注：まだ理解が十分ではないが、おそらく標準的なDOM要素、例えばdivやbutton内でonClick={関数}と書いた場合には、これはbuttonへクリックイベントハンドラーを定義する効果がある。しかし、カスタムコンポーネントにおいて、onClick={関数}として渡した場合には、これはクリックイベントハンドラーの指定ではなく、単にpropsとして子コンポーネントに渡される。このようにpropsとして渡す場合にはon*という名前をつけ、実際に実行する関数に関してはhandle*という名前をつけることが慣習になっている。ということだと思われる。)

Try clicking a square – you should get an error because we haven't defined <code>handleClick</code>yet. Add it to the Board class.

この時点でマス目をクリックすると、エラーが発生するはずです。何故ならまだhandleClick を定義していないからです。これを Board クラスに加えましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Board</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">super</span><span class="p">();</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
      <span class="nx">squares</span><span class="o">:</span> <span class="nb">Array</span><span class="p">(</span><span class="mi">9</span><span class="p">).</span><span class="nx">fill</span><span class="p">(</span><span class="kc">null</span><span class="p">),</span>
    <span class="p">};</span>
  <span class="p">}</span>

<span class="hll">  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
</span><span class="hll">    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
</span><span class="hll">    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="s1">'X'</span><span class="p">;</span>
</span><span class="hll">    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span><span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span><span class="p">});</span>
</span><span class="hll">  <span class="p">}</span>
</span>
  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">Square</span>
        <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]}</span>
        <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)}</span>
      <span class="o">/&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>

  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: X'</span><span class="p">;</span>

    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"status"</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">status</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">0</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">1</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">2</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">3</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">4</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">5</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">6</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">7</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">8</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
<a href="https://codepen.io/gaearon/pen/ybbQJX?editors=0010">View the current code.</a>

We call <code>.slice()</code> to copy the <code>squares</code> array instead of mutating the existing array. Jump ahead a <a href="https://facebook.github.io/react/tutorial/tutorial.html#why-immutability-is-important">section</a> to learn why immutability is important.

訳注：飛ばす

Now you should be able to click in squares to fill them again, but the state is stored in the Board component instead of in each Square, which lets us continue building the game. Note how whenever Board's state changes, the Square components rerender automatically.

改めてマス目をクリックしてその中にマークが付くようになりました。Square コンポーネントをクリックしていますが、しかし状態は Board コンポーネントに保持されており、Square コンポーネントには保持されていません。これによってゲームの開発をさらに進めていけるようになりました。Board コンポーネントの状態が変更されると、どんなときでも自動的に Square コンポーネントが更新されていることに注目してください。

Square no longer keeps its own state; it receives its value from its parent Board and informs its parent when it's clicked. We call components like this <strong>controlled components</strong>.

Square コンポーネントは最早自分自身で状態を保持していません。つまり、値を親コンポーネントである Board から受け取って、親コンポーネントに対して、クリックされた時にその旨を告げているにすぎません。このようなコンポーネントをコントロールドコンポーネントと名付けることにします。
<h3><a class="anchor" name="why-immutability-is-important"></a>Why Immutability Is Important</h3>
(訳注: イミュータブルは重要な概念且つ、中身が正確にわからないと誤訳しそうなので飛ばす。簡単に言えば、this.state.value = 4 と直接変更するのではなく、一回コピーしたものを変更して、それを代入する手法を取ること。)

In the previous code example, we suggest using the <code>.slice()</code> operator to copy the <code>squares</code>array prior to making changes and to prevent mutating the existing array. Let's talk about what this means and why it is an important concept to learn.

There are generally two ways for changing data. The first method is to <em>mutate</em> the data by directly changing the values of a variable. The second method is to replace the data with a new copy of the object that also includes desired changes.
<h4><a class="anchor" name="data-change-with-mutation"></a>Data change with mutation</h4>
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kd">var</span> <span class="nx">player</span> <span class="o">=</span> <span class="p">{</span><span class="nx">score</span><span class="o">:</span> <span class="mi">1</span><span class="p">,</span> <span class="nx">name</span><span class="o">:</span> <span class="s1">'Jeff'</span><span class="p">};</span>
<span class="nx">player</span><span class="p">.</span><span class="nx">score</span> <span class="o">=</span> <span class="mi">2</span><span class="p">;</span>
<span class="c1">// Now player is {score: 2, name: 'Jeff'}</span>
</code></pre>
</div>
<h4><a class="anchor" name="data-change-without-mutation"></a>Data change without mutation</h4>
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kd">var</span> <span class="nx">player</span> <span class="o">=</span> <span class="p">{</span><span class="nx">score</span><span class="o">:</span> <span class="mi">1</span><span class="p">,</span> <span class="nx">name</span><span class="o">:</span> <span class="s1">'Jeff'</span><span class="p">};</span>

<span class="kd">var</span> <span class="nx">newPlayer</span> <span class="o">=</span> <span class="nb">Object</span><span class="p">.</span><span class="nx">assign</span><span class="p">({},</span> <span class="nx">player</span><span class="p">,</span> <span class="p">{</span><span class="nx">score</span><span class="o">:</span> <span class="mi">2</span><span class="p">});</span>
<span class="c1">// Now player is unchanged, but newPlayer is {score: 2, name: 'Jeff'}</span>

<span class="c1">// Or if you are using object spread syntax proposal, you can write:</span>
<span class="c1">// var newPlayer = {...player, score: 2};</span>
</code></pre>
</div>
The end result is the same but by not mutating (or changing the underlying data) directly we now have an added benefit that can help us increase component and overall application performance.
<h4><a class="anchor" name="easier-undoredo-and-time-travel"></a>Easier Undo/Redo and Time Travel</h4>
Immutability also makes some complex features much easier to implement. For example, further in this tutorial we will implement time travel between different stages of the game. Avoiding data mutations lets us keep a reference to older versions of the data, and switch between them if we need to.
<h4><a class="anchor" name="tracking-changes"></a>Tracking Changes</h4>
Determining if a mutated object has changed is complex because changes are made directly to the object. This then requires comparing the current object to a previous copy, traversing the entire object tree, and comparing each variable and value. This process can become increasingly complex.

Determining how an immutable object has changed is considerably easier. If the object being referenced is different from before, then the object has changed. That's it.
<h4><a class="anchor" name="determining-when-to-re-render-in-react"></a>Determining When to Re-render in React</h4>
The biggest benefit of immutability in React comes when you build simple <em>pure components</em>. Since immutable data can more easily determine if changes have been made it also helps to determine when a component requires being re-rendered.

To learn more about <code>shouldComponentUpdate()</code> and how you can build <em>pure components</em>take a look at <a href="https://facebook.github.io/react/docs/optimizing-performance.html#examples">Optimizing Performance</a>.
<h3><a class="anchor" name="functional-components"></a>Functional Components</h3>
ファンクショナル・コンポーネント

We've removed the constructor, and in fact, React supports a simpler syntax called <strong>functional components</strong> for component types like Square that only consist of a <code>render</code> method. Rather than define a class extending <code>React.Component</code>, simply write a function that takes props and returns what should be rendered.

すでにコンストラクタを取り除いてしまいましたが、React は ファンクショナル・コンポーネントを書くためのシンプルな構文を持っていますので、これは適切な処置です。ファンクショナル・コンポーネントというのは、今回の Square のように render メソッドしかもっていないコンポーネントです。　React.Component を拡張してクラスを規定するのではなく、単に props を引数に取り、レンダーされる内容を返す、そのような関数を書くことができます。

Replace the whole Square class with this function:

Square クラスを変更し、ファンクショナル・コンポーネントにしてしまいましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kd">function</span> <span class="nx">Square</span><span class="p">(</span><span class="nx">props</span><span class="p">)</span> <span class="p">{</span>
  <span class="k">return</span> <span class="p">(</span>
    <span class="o">&lt;</span><span class="nx">button</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"square"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{</span><span class="nx">props</span><span class="p">.</span><span class="nx">onClick</span><span class="p">}</span><span class="o">&gt;</span>
      <span class="p">{</span><span class="nx">props</span><span class="p">.</span><span class="nx">value</span><span class="p">}</span>
    <span class="o">&lt;</span><span class="err">/button&gt;</span>
  <span class="p">);</span>
<span class="p">}</span>
</code></pre>
</div>
You'll need to change <code>this.props</code> to <code>props</code> both times it appears. Many components in your apps will be able to be written as functional components: these components tend to be easier to write and React will optimize them more in the future.

this.props を変更し、props にしましょう。あなたのアプリケーション内の多くのコンポーネントは、ファンクショナルコンポーネントとして書けるはずです。ファンクショナルコンポーネントは書くのが簡単ですし、将来的には React はこれをより活用するようになります。

While we're cleaning up the code, we also changed <code>onClick={() =&gt; props.onClick()}</code> to just <code>onClick={props.onClick}</code>, as passing the function down is enough for our example. Note that <code>onClick={props.onClick()}</code> would not work because it would call <code>props.onClick</code>immediately instead of passing it down.

さらに <code>onClick={() =&gt; props.onClick()}</code> を変更し <code>onClick={props.onClick}</code> にした点に注目しましょう。関数を Board コンポーネントから Square コンポーネントへと渡したわけですから、これだけで十分です。注意してほしいのは <code>onClick={props.onClick()}</code> と書いてしまうと意図したとおりには機能しません。何故なら、その場合には即座に <code>props.onClick</code> が実行されてしまうからです。

<a href="https://codepen.io/gaearon/pen/QvvJOv?editors=0010">View the current code.</a>
<h3><a class="anchor" name="taking-turns"></a>Taking Turns</h3>
プレイヤーが交代する

An obvious defect in our game is that only X can play. Let's fix that.

さて我々のゲームにある明らかな欠点は、X のプレイヤーしかプレイできない点です。直していきましょう。

Let's default the first move to be by 'X'. Modify our starting state in our Board constructor.

まず最初の手は、X から始まるようにしましょう。Board コンポーネント内の初期状態の設定を変更します。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Board</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">super</span><span class="p">();</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
      <span class="nx">squares</span><span class="o">:</span> <span class="nb">Array</span><span class="p">(</span><span class="mi">9</span><span class="p">).</span><span class="nx">fill</span><span class="p">(</span><span class="kc">null</span><span class="p">),</span>
<span class="hll">      <span class="nx">xIsNext</span><span class="o">:</span> <span class="kc">true</span><span class="p">,</span>
</span>    <span class="p">};</span>
  <span class="p">}</span>
</code></pre>
</div>
Each time we move we shall toggle <code>xIsNext</code> by flipping the boolean value and saving the state. Now update Board's <code>handleClick</code> function to flip the value of <code>xIsNext</code>.

手をプレイする度に、xIsNext を true と false の間でひっくり返して、そして状態に記録します。では handleClick ファンクションを変更して、xIsNext がそのように変更されるようにしましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
<span class="hll">    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">;</span>
</span>    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
      <span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span><span class="p">,</span>
<span class="hll">      <span class="nx">xIsNext</span><span class="o">:</span> <span class="o">!</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span><span class="p">,</span>
</span>    <span class="p">});</span>
  <span class="p">}</span>
</code></pre>
</div>
Now X and O take turns. Next, change the "status" text in Board's <code>render</code> so that it also displays who is next.

さあ、X と O が順番にプレイできるようになりました。次に、Board コンポーネント内の "status" と書かれたテキスト部分に、次に誰がプレイする番なのかを表示するようにしましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: '</span> <span class="o">+</span> <span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">);</span>
</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="c1">// the rest has not changed</span>
</code></pre>
</div>
After these changes you should have this Board component:

この変更を加えると、Board コンポーネントは以下の用になっているはずです。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Board</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">super</span><span class="p">();</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
      <span class="nx">squares</span><span class="o">:</span> <span class="nb">Array</span><span class="p">(</span><span class="mi">9</span><span class="p">).</span><span class="nx">fill</span><span class="p">(</span><span class="kc">null</span><span class="p">),</span>
<span class="hll">      <span class="nx">xIsNext</span><span class="o">:</span> <span class="kc">true</span><span class="p">,</span>
</span>    <span class="p">};</span>
  <span class="p">}</span>

  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
</span><span class="hll">    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">;</span>
</span><span class="hll">    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
</span><span class="hll">      <span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span><span class="p">,</span>
</span><span class="hll">      <span class="nx">xIsNext</span><span class="o">:</span> <span class="o">!</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span><span class="p">,</span>
</span><span class="hll">    <span class="p">});</span>
</span>  <span class="p">}</span>

  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">Square</span>
        <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]}</span>
        <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)}</span>
      <span class="o">/&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>

  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: '</span> <span class="o">+</span> <span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">);</span>
</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"status"</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">status</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">0</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">1</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">2</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">3</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">4</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">5</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">6</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">7</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">8</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
<a href="https://codepen.io/gaearon/pen/KmmrBy?editors=0010">View the current code.</a>
<h3><a class="anchor" name="declaring-a-winner"></a>Declaring a Winner</h3>
勝利者の宣言

Let's show when a game is won. Add this helper function to the end of the file:

次に、勝者が決まった場合に、それを表示するようにしましょう。そのために、次の関数をファイルの最後に追加します。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kd">function</span> <span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">squares</span><span class="p">)</span> <span class="p">{</span>
  <span class="kr">const</span> <span class="nx">lines</span> <span class="o">=</span> <span class="p">[</span>
    <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">6</span><span class="p">,</span> <span class="mi">7</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">6</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">7</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">2</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">8</span><span class="p">],</span>
    <span class="p">[</span><span class="mi">2</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">6</span><span class="p">],</span>
  <span class="p">];</span>
  <span class="k">for</span> <span class="p">(</span><span class="kd">let</span> <span class="nx">i</span> <span class="o">=</span> <span class="mi">0</span><span class="p">;</span> <span class="nx">i</span> <span class="o">&lt;</span> <span class="nx">lines</span><span class="p">.</span><span class="nx">length</span><span class="p">;</span> <span class="nx">i</span><span class="o">++</span><span class="p">)</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="p">[</span><span class="nx">a</span><span class="p">,</span> <span class="nx">b</span><span class="p">,</span> <span class="nx">c</span><span class="p">]</span> <span class="o">=</span> <span class="nx">lines</span><span class="p">[</span><span class="nx">i</span><span class="p">];</span>
    <span class="k">if</span> <span class="p">(</span><span class="nx">squares</span><span class="p">[</span><span class="nx">a</span><span class="p">]</span> <span class="o">&amp;&amp;</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">a</span><span class="p">]</span> <span class="o">===</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">b</span><span class="p">]</span> <span class="o">&amp;&amp;</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">a</span><span class="p">]</span> <span class="o">===</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">c</span><span class="p">])</span> <span class="p">{</span>
      <span class="k">return</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">a</span><span class="p">];</span>
    <span class="p">}</span>
  <span class="p">}</span>
  <span class="k">return</span> <span class="kc">null</span><span class="p">;</span>
<span class="p">}</span>
</code></pre>
</div>
You can call it in Board's <code>render</code> function to check if anyone has won the game and make the status text show "Winner: [X/O]" when someone wins.

この関数を Board コンポーネントの render 関数の中で呼び出すことで、誰が勝ったかを判断することができます。さらに勝者を ステータス表示部分に"Winner: [X/O]"と表示するために次のように変更を加えます。

Replace the <code>status</code> declaration in Board's <code>render</code> with this code:

Board コンポーネントの render 内の status 部分を、次のようにします。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">winner</span> <span class="o">=</span> <span class="nx">calculateWinner</span><span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">);</span>
</span><span class="hll">    <span class="kd">let</span> <span class="nx">status</span><span class="p">;</span>
</span><span class="hll">    <span class="k">if</span> <span class="p">(</span><span class="nx">winner</span><span class="p">)</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Winner: '</span> <span class="o">+</span> <span class="nx">winner</span><span class="p">;</span>
</span><span class="hll">    <span class="p">}</span> <span class="k">else</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: '</span> <span class="o">+</span> <span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">);</span>
</span><span class="hll">    <span class="p">}</span>
</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="c1">// the rest has not changed</span>
</code></pre>
</div>
You can now change <code>handleClick</code> in Board to return early and ignore the click if someone has already won the game or if a square is already filled:

さらに Board コンポーネント内の handleClick に変更を加えて、既に勝者が決まっていたり、もしくは既にクリックしたマス目が埋まっていた場合に、return を返して処理を無視するようにします。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
<span class="hll">    <span class="k">if</span> <span class="p">(</span><span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">squares</span><span class="p">)</span> <span class="o">||</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">])</span> <span class="p">{</span>
</span><span class="hll">      <span class="k">return</span><span class="p">;</span>
</span><span class="hll">    <span class="p">}</span>
</span>    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">;</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
      <span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span><span class="p">,</span>
      <span class="nx">xIsNext</span><span class="o">:</span> <span class="o">!</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span><span class="p">,</span>
    <span class="p">});</span>
  <span class="p">}</span>
</code></pre>
</div>
Congratulations! You now have a working tic-tac-toe game. And now you know the basics of React. So <em>you're</em> probably the real winner here.

おめでとうございます！あなたは、三目並べを作るワークショップに勝利しました。そして React の基礎を身につけることができました。ある意味で真の勝者です。

<a href="https://codepen.io/gaearon/pen/LyyXgK?editors=0010">View the current code.</a>
<h2>Storing a History</h2>
履歴を表示する

Let's make it possible to revisit old states of the board so we can see what it looked like after any of the previous moves. We're already creating a new <code>squares</code> array each time a move is made, which means we can easily store the past board states simultaneously.

ボード上で繰り広げられる戦いの、過去の状態に戻ることが出来るように機能を追加してみましょう。つまり、過去のある手を打った後に、盤面がどのような状態なのかを確認できるようにする機能です。私達のコードにおいては既に、手を打つ度に新しい squares という配列を作るようにしていますから、過去の盤上の状態を全て保存するのは容易にできるはずです。

Let's plan to store an object like this in state:

次のような形で状態を保持するオブジェクトを作っていきます。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="nx">history</span> <span class="o">=</span> <span class="p">[</span>
  <span class="p">{</span>
    <span class="nx">squares</span><span class="o">:</span> <span class="p">[</span>
      <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
      <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
      <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
    <span class="p">]</span>
  <span class="p">},</span>
  <span class="p">{</span>
    <span class="nx">squares</span><span class="o">:</span> <span class="p">[</span>
      <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
      <span class="kc">null</span><span class="p">,</span> <span class="s1">'X'</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
      <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span> <span class="kc">null</span><span class="p">,</span>
    <span class="p">]</span>
  <span class="p">},</span>
  <span class="c1">// ...</span>
<span class="p">]</span>
</code></pre>
</div>
We'll want the top-level Game component to be responsible for displaying the list of moves. So just as we pulled the state up before from Square into Board, let's now pull it up again from Board into Game – so that we have all the information we need at the top level.

最上階層にある Game コンポーネントに、打ち手のリストを表示する機能を実装することにしましょう。そのために、先程 Square コンポーネントから Board コンポーネントへ状態を保持する場所を引き上げたように、今回は Board コンポーネントから Game コンポーネントへと状態を保持する場所を引き上げます。つまり、全ての必要な情報を、最上階層が持つようにするということです。

First, set up the initial state for Game by adding a constructor to it:

まずは Game コンポーネントにコンストラクターを追加して、初期状態を設定します。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Game</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
<span class="hll">  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
</span><span class="hll">    <span class="kr">super</span><span class="p">();</span>
</span><span class="hll">    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">history</span><span class="o">:</span> <span class="p">[{</span>
</span><span class="hll">        <span class="nx">squares</span><span class="o">:</span> <span class="nb">Array</span><span class="p">(</span><span class="mi">9</span><span class="p">).</span><span class="nx">fill</span><span class="p">(</span><span class="kc">null</span><span class="p">),</span>
</span><span class="hll">      <span class="p">}],</span>
</span><span class="hll">      <span class="nx">xIsNext</span><span class="o">:</span> <span class="kc">true</span><span class="p">,</span>
</span><span class="hll">    <span class="p">};</span>
</span><span class="hll">  <span class="p">}</span>
</span>
  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game"</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game-board"</span><span class="o">&gt;</span>
          <span class="o">&lt;</span><span class="nx">Board</span> <span class="o">/&gt;</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game-info"</span><span class="o">&gt;</span>
          <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span><span class="p">{</span><span class="cm">/* status */</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
          <span class="o">&lt;</span><span class="nx">ol</span><span class="o">&gt;</span><span class="p">{</span><span class="cm">/* TODO */</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/ol&gt;</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
Then change Board so that it takes <code>squares</code> via props and has its own <code>onClick</code> prop specified by Game, like the transformation we made for Square earlier. You can pass the location of each square into the click handler so that we still know which square was clicked. Here is a list of steps you need to do:

次に Board コンポーネントを変更していきます。まずは Board コンポーネントが props を介して Game コンポーネントから squares を(訳注：状態の中のhistoryの中にあるsquares) 受け取れるようにします。また Board コンポーネントが onClick というこれまた Game コンポーネント内で設定された関数を、prop 経由で受け取れるようにします。(訳注：Game コンポーネントの中で) それぞれ何番目のマス目なのかを特定できる情報を、click ハンドラーに渡す予定です。そうすることで、どのマス目がクリックされたかがわかるようになります。

次のリストは、上記の作業をまとめたものです。一つ一つ作業していってください。
<ul>
 	<li>Delete the <code>constructor</code> in Board.
Borad コンポーネント内のコンストラクターを削除する</li>
 	<li>Replace <code>this.state.squares[i]</code> with <code>this.props.squares[i]</code> in Board's <code>renderSquare</code>.
<code>this.state.squares[i]</code> を変更し、 <code>this.props.squares[i]</code> へ置き換える。これは Board コンポーネント内の <code>renderSquare</code> にある。</li>
 	<li>Replace <code>this.handleClick(i)</code> with <code>this.props.onClick(i)</code> in Board's <code>renderSquare</code>.
<code>this.handleClick(i)</code> を変更し、<code>this.props.onClick(i)</code> へと置き換える。これも同じく Board コンポーネント内の <code>renderSquare</code> にある。</li>
</ul>
Now the whole Board component looks like this:

この作業を終えると、Board コンポーネントは以下のようになっているはずです。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript"><span class="kr">class</span> <span class="nx">Board</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
    <span class="k">if</span> <span class="p">(</span><span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">squares</span><span class="p">)</span> <span class="o">||</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">])</span> <span class="p">{</span>
      <span class="k">return</span><span class="p">;</span>
    <span class="p">}</span>
    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">;</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
      <span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span><span class="p">,</span>
      <span class="nx">xIsNext</span><span class="o">:</span> <span class="o">!</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span><span class="p">,</span>
    <span class="p">});</span>
  <span class="p">}</span>

  <span class="nx">renderSquare</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">Square</span>
<span class="hll">        <span class="nx">value</span><span class="o">=</span><span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]}</span>
</span><span class="hll">        <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">props</span><span class="p">.</span><span class="nx">onClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)}</span>
</span>      <span class="o">/&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>

  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">winner</span> <span class="o">=</span> <span class="nx">calculateWinner</span><span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">squares</span><span class="p">);</span>
    <span class="kd">let</span> <span class="nx">status</span><span class="p">;</span>
    <span class="k">if</span> <span class="p">(</span><span class="nx">winner</span><span class="p">)</span> <span class="p">{</span>
      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Winner: '</span> <span class="o">+</span> <span class="nx">winner</span><span class="p">;</span>
    <span class="p">}</span> <span class="k">else</span> <span class="p">{</span>
      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: '</span> <span class="o">+</span> <span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">);</span>
    <span class="p">}</span>

    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"status"</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">status</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">0</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">1</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">2</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">3</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">4</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">5</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">6</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">7</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">8</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre>
</div>
Game's <code>render</code> should look at the most recent history entry and can take over calculating the game status:

Game コンポーネントの render 内で、直近の履歴をチェックして、ゲームの勝者を判定する機能 (訳注：原文に正確には状態を判定する機能) を持つべきですので、次のように変更します。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">history</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">history</span><span class="p">;</span>
</span><span class="hll">    <span class="kr">const</span> <span class="nx">current</span> <span class="o">=</span> <span class="nx">history</span><span class="p">[</span><span class="nx">history</span><span class="p">.</span><span class="nx">length</span> <span class="o">-</span> <span class="mi">1</span><span class="p">];</span>
</span><span class="hll">    <span class="kr">const</span> <span class="nx">winner</span> <span class="o">=</span> <span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">);</span>
</span>
<span class="hll">    <span class="kd">let</span> <span class="nx">status</span><span class="p">;</span>
</span><span class="hll">    <span class="k">if</span> <span class="p">(</span><span class="nx">winner</span><span class="p">)</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Winner: '</span> <span class="o">+</span> <span class="nx">winner</span><span class="p">;</span>
</span><span class="hll">    <span class="p">}</span> <span class="k">else</span> <span class="p">{</span>
</span><span class="hll">      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: '</span> <span class="o">+</span> <span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">);</span>
</span><span class="hll">    <span class="p">}</span>
</span>
    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game"</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game-board"</span><span class="o">&gt;</span>
<span class="hll">          <span class="o">&lt;</span><span class="nx">Board</span>
</span><span class="hll">            <span class="nx">squares</span><span class="o">=</span><span class="p">{</span><span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">}</span>
</span><span class="hll">            <span class="nx">onClick</span><span class="o">=</span><span class="p">{(</span><span class="nx">i</span><span class="p">)</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)}</span>
</span><span class="hll">          <span class="o">/&gt;</span>
</span>        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game-info"</span><span class="o">&gt;</span>
<span class="hll">          <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">status</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
</span>          <span class="o">&lt;</span><span class="nx">ol</span><span class="o">&gt;</span><span class="p">{</span><span class="cm">/* TODO */</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/ol&gt;</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
</code></pre>
</div>
Since Game is now rendering the status, we can delete <code>&lt;div className="status"&gt;{status}&lt;/div&gt;</code> and the code calculating the status from the Board's <code>render</code> function:

Game コンポーネントが状態をレンダリングする機能を持ったので (訳注：次に誰がプレイする番か、誰が勝ったかを表示するエリア) 、Board コンポーネントの render 内から、<code>&lt;div className="status"&gt;{status}&lt;/div&gt;</code> を削除し、判定機能も削除します。
<div class="highlight">
<pre><code class="language-js" data-lang="js"><span class="hll">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
</span><span class="hll">    <span class="k">return</span> <span class="p">(</span>
</span><span class="hll">      <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span>
</span><span class="hll">        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
</span>          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">0</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">1</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">2</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">3</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">4</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">5</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"board-row"</span><span class="o">&gt;</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">6</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">7</span><span class="p">)}</span>
          <span class="p">{</span><span class="k">this</span><span class="p">.</span><span class="nx">renderSquare</span><span class="p">(</span><span class="mi">8</span><span class="p">)}</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
</code></pre>
</div>
Next, we need to move the <code>handleClick</code> method implementation from Board to Game. You can cut it from the Board class, and paste it into the Game class.

次に handleClick メソッドの実装箇所を、Board コンポーネントから Game コンポーネントへと移し替えます。Board クラスからその箇所をカットして、Game クラスへとペーストしてください。

We also need to change it a little, since Game state is structured differently. Game's <code>handleClick</code> can push a new entry onto the stack by concatenating the new history entry to make a new history array.

単にカット・アンド・ペーストしただけではだめで、もう少し変更が必要です。というのも、Game コンポーネントで設定した状態は、Board コンポーネントが持っていたものとは少し違うからです。Game コンポーネント内の handleClick メソッドを変更して、新しく状態の値が生まれた際に、それを既存の状態に対して積み重ねて保存するようにします。つまり、新しい history を古い history へと連結させ、新しい history 配列を作り出します。(訳注：history: history.concat([{squares: squares,}])この部分ですね。)
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">history</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">history</span><span class="p">;</span>
</span><span class="hll">    <span class="kr">const</span> <span class="nx">current</span> <span class="o">=</span> <span class="nx">history</span><span class="p">[</span><span class="nx">history</span><span class="p">.</span><span class="nx">length</span> <span class="o">-</span> <span class="mi">1</span><span class="p">];</span>
</span><span class="hll">    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
</span>    <span class="k">if</span> <span class="p">(</span><span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">squares</span><span class="p">)</span> <span class="o">||</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">])</span> <span class="p">{</span>
      <span class="k">return</span><span class="p">;</span>
    <span class="p">}</span>
    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">;</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
<span class="hll">      <span class="nx">history</span><span class="o">:</span> <span class="nx">history</span><span class="p">.</span><span class="nx">concat</span><span class="p">([{</span>
</span><span class="hll">        <span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span><span class="p">,</span>
</span><span class="hll">      <span class="p">}]),</span>
</span>      <span class="nx">xIsNext</span><span class="o">:</span> <span class="o">!</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span><span class="p">,</span>
    <span class="p">});</span>
  <span class="p">}</span>
</code></pre>
</div>
At this point, Board only needs <code>renderSquare</code> and <code>render</code>; the state initialization and click handler should both live in Game.

この時点で、Board には <code>renderSquare</code> and <code>render</code>しかありません。つまり状態の初期化とクリックハンドラーは、どちらもGameの中にあります。

<a href="https://codepen.io/gaearon/pen/EmmOqJ?editors=0010">View the current code.</a>
<h3><a class="anchor" name="showing-the-moves"></a>Showing the Moves</h3>
手を表示する

Let's show the previous moves made in the game so far. We learned earlier that React elements are first-class JS objects and we can store them or pass them around. To render multiple items in React, we pass an array of React elements. The most common way to build that array is to map over your array of data. Let's do that in the <code>render</code> method of Game:

では先程 Game コンポーネント内で作成した moves = 手(訳注：つまり盤上の状態の変遷) を表示してみましょう。React エレメンが非常に素晴らしい JS オブジェクトであることは既に皆さんご理解いただけたと思うのですが、更に今回は React エレメントを保持して、他の場所へと渡す、という方法をご紹介します。React において複数の項目をレンダリングする場合には、単に React エレメントの配列を渡すだけでいいのです。そのような配列を作る一般的に取られる手法は、map メソッドを用いて、配列のデータを処理するものです。(訳注：<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map" target="_blank" rel="noopener noreferrer">Array.prototype.map()</a> メソッドについてはこちらを参照) Game コンポーネントの render メソッド内でこれを実行しましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">history</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">history</span><span class="p">;</span>
    <span class="kr">const</span> <span class="nx">current</span> <span class="o">=</span> <span class="nx">history</span><span class="p">[</span><span class="nx">history</span><span class="p">.</span><span class="nx">length</span> <span class="o">-</span> <span class="mi">1</span><span class="p">];</span>
    <span class="kr">const</span> <span class="nx">winner</span> <span class="o">=</span> <span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">);</span>

<span class="hll">    <span class="kr">const</span> <span class="nx">moves</span> <span class="o">=</span> <span class="nx">history</span><span class="p">.</span><span class="nx">map</span><span class="p">((</span><span class="nx">step</span><span class="p">,</span> <span class="nx">move</span><span class="p">)</span> <span class="o">=&gt;</span> <span class="p">{</span>
</span><span class="hll">      <span class="kr">const</span> <span class="nx">desc</span> <span class="o">=</span> <span class="nx">move</span> <span class="o">?</span>
</span><span class="hll">        <span class="s1">'Move #'</span> <span class="o">+</span> <span class="nx">move</span> <span class="o">:</span>
</span><span class="hll">        <span class="s1">'Game start'</span><span class="p">;</span>
</span><span class="hll">      <span class="k">return</span> <span class="p">(</span>
</span><span class="hll">        <span class="o">&lt;</span><span class="nx">li</span><span class="o">&gt;</span>
</span><span class="hll">          <span class="o">&lt;</span><span class="nx">a</span> <span class="nx">href</span><span class="o">=</span><span class="s2">"#"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">jumpTo</span><span class="p">(</span><span class="nx">move</span><span class="p">)}</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">desc</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/a&gt;</span>
</span><span class="hll">        <span class="o">&lt;</span><span class="err">/li&gt;</span>
</span><span class="hll">      <span class="p">);</span>
</span><span class="hll">    <span class="p">});</span>
</span>
    <span class="kd">let</span> <span class="nx">status</span><span class="p">;</span>
    <span class="k">if</span> <span class="p">(</span><span class="nx">winner</span><span class="p">)</span> <span class="p">{</span>
      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Winner: '</span> <span class="o">+</span> <span class="nx">winner</span><span class="p">;</span>
    <span class="p">}</span> <span class="k">else</span> <span class="p">{</span>
      <span class="nx">status</span> <span class="o">=</span> <span class="s1">'Next player: '</span> <span class="o">+</span> <span class="p">(</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">);</span>
    <span class="p">}</span>

    <span class="k">return</span> <span class="p">(</span>
      <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game"</span><span class="o">&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game-board"</span><span class="o">&gt;</span>
          <span class="o">&lt;</span><span class="nx">Board</span>
            <span class="nx">squares</span><span class="o">=</span><span class="p">{</span><span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">}</span>
            <span class="nx">onClick</span><span class="o">=</span><span class="p">{(</span><span class="nx">i</span><span class="p">)</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)}</span>
          <span class="o">/&gt;</span>
        <span class="o">&lt;</span><span class="err">/div&gt;</span>
        <span class="o">&lt;</span><span class="nx">div</span> <span class="nx">className</span><span class="o">=</span><span class="s2">"game-info"</span><span class="o">&gt;</span>
          <span class="o">&lt;</span><span class="nx">div</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">status</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/div&gt;</span>
<span class="hll">          <span class="o">&lt;</span><span class="nx">ol</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">moves</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/ol&gt;</span>
</span>        <span class="o">&lt;</span><span class="err">/div&gt;</span>
      <span class="o">&lt;</span><span class="err">/div&gt;</span>
    <span class="p">);</span>
  <span class="p">}</span>
</code></pre>
</div>
<a href="https://codepen.io/gaearon/pen/EmmGEa?editors=0010">View the current code.</a>

For each step in the history, we create a list item <code>&lt;li&gt;</code> with a link <code>&lt;a&gt;</code> inside it that goes nowhere (<code>href="#"</code>) but has a click handler which we'll implement shortly. With this code, you should see a list of the moves that have been made in the game, along with a warning that says:

history の中の各ステップおいて (訳注：つまり、historyには全ての手が入っているわけですが、その各回において) 、それぞれ&lt;li&gt;要素を作成します。その中にはどこにも移動しない&lt;a&gt;リンク(href="#"なので) を入れます。その代わりに後ほど実装するクリックハンドラーを持たせておきます。ここまでコードを書くと、move のリストが Game コンポーネント内に表示されるはずです。ただし、次のような警告も出ているはずです。

Warning: Each child in an array or iterator should have a unique "key" prop. Check the render method of "Game".

警告：配列やイテレーター内の各要素は、それぞれ異なる"key" prop を持つ必要があります。Game コンポーネント内の render メソッドを確認してください。

(訳注：英辞郎より引用：イテレーター、反復子◆複数の要素の集まりと見なせる対象（配列・リストなど）で、その各要素に順次アクセスするための変数や言語機能。)

Let's talk about what that warning means.

ではこの警告が何を意味しているのか、お話しましょう。
<h3><a class="anchor" name="keys"></a>Keys</h3>
When you render a list of items, React always stores some info about each item in the list. If you render a component that has state, that state needs to be stored – and regardless of how you implement your components, React stores a reference to the backing native views.

(訳注：このセンテンス、抽象的すぎて、よくわからない。)

あなたが複数のアイテムが含まれたリストをレンダリングする際には、React は常にそれぞれのアイテムの情報を保持しています。状態をもったコンポーネントをレンダリングする際には、その状態は保持されなくてはいけません。そして、どのようにあなたがコンポーネントを実装したとしても、React は backing native views への参照を保持しています。

When you update that list, React needs to determine what has changed. You could've added, removed, rearranged, or updated items in the list.

あなたがリストを更新した際に、React は何が変更されたのかを判断しなくてはいけません。追加、削除、順番を変える、アイテムを更新する。一体どの操作をしたのかを判断する必要があります。

Imagine transitioning from

ある偏移について考えてみましょう。この状態から、
<div class="highlight">
<pre><code class="language-html" data-lang="html"><span class="nt">&lt;li&gt;</span>Alexa: 7 tasks left<span class="nt">&lt;/li&gt;</span>
<span class="nt">&lt;li&gt;</span>Ben: 5 tasks left<span class="nt">&lt;/li&gt;</span>
</code></pre>
</div>
to

以下のような状態へ推移するとしましょう。
<div class="highlight">
<pre><code class="language-html" data-lang="html"><span class="nt">&lt;li&gt;</span>Ben: 9 tasks left<span class="nt">&lt;/li&gt;</span>
<span class="nt">&lt;li&gt;</span>Claudia: 8 tasks left<span class="nt">&lt;/li&gt;</span>
<span class="nt">&lt;li&gt;</span>Alexa: 5 tasks left<span class="nt">&lt;/li&gt;</span>
</code></pre>
</div>
To a human eye, it looks likely that Alexa and Ben swapped places and Claudia was added – but React is just a computer program and doesn't know what you intended it to do. As a result, React asks you to specify a <em>key</em> property on each element in a list, a string to differentiate each component from its siblings. In this case, <code>alexa</code>, <code>ben</code>, <code>claudia</code> might be sensible keys; if the items correspond to objects in a database, the database ID is usually a good choice:

人間がこれを見た場合には、Alexa と Ben が席を変えて、さらに Claudia が追加されたのだろうと、考えることでしょう。でも React は単なるコンピューターのプログラムですから、あなたがどう意図しているのかなんていうことはわかりません。結果として、React はあなたに、リスト内のそれぞれの要素に対して "key"  プロパティを付けるよう要求します。これを用いて、兄弟要素内の識別を行うのです。 このケースの場合であれば、 <code>alexa</code>, <code>ben</code>, <code>claudia</code> を key に用いるのがふさわしいでしょう。その他のケース、例えばデータベースを用いていて、データベースに記録されているオブジェクトと、React の中で使われる各項目が一致しているのであれば、データベース内の各項目の ID を用いるのも、常に良い選択肢です。
<div class="highlight">
<pre><code class="language-html" data-lang="html"><span class="nt">&lt;li</span> <span class="na">key=</span><span class="s">{user.id}</span><span class="nt">&gt;</span>{user.name}: {user.taskCount} tasks left<span class="nt">&lt;/li&gt;</span>
</code></pre>
</div>
<code>key</code> is a special property that's reserved by React (along with <code>ref</code>, a more advanced feature). When an element is created, React pulls off the <code>key</code> property and stores the key directly on the returned element. Even though it may look like it is part of props, it cannot be referenced with <code>this.props.key</code>. React uses the key automatically while deciding which children to update; there is no way for a component to inquire about its own key.

React において "key" は特別なプロパティで、予約語となっています。(他にも予約後になっているものとして ref などがあります。これはより高度な機能ですが) element が生成される時に、React は key プロパティを取り出して、その key をreturn で返される element の中に埋め込みます。key は props の一部のように見えますが、this.props.key で参照することはできません。React は特に設定をしなくても、どの要素を更新すべきなのかを判断するために、 key を用います。ただし、コンポーネント自身が自分のキーを問い合わせる方法は存在しません。

When a list is rerendered, React takes each element in the new version and looks for one with a matching key in the previous list. When a key is added to the set, a component is created; when a key is removed, a component is destroyed. Keys tell React about the identity of each component, so that it can maintain the state across rerenders. If you change the key of a component, it will be completely destroyed and recreated with a new state.

再レンダリングの際に React がおこなっていることを説明しましょう。React は新しいリストを取り込むと、それと一つ前のリストとを比較して、リストの中の各要素につき、一致するものを見つけようとします。新しい key が追加されていれば、新しいコンポーネントを作成します。反対に、取り除かれた key があれば、その key を持っていたコンポーネントは破壊されます。Key を用いて React は、それぞれのコンポーネントの同一性を把握しており、その結果として レンダリング前後で state を保持することができるのです。もしコンポーネントが持つ key を変更してしまうと、そのコンポーネントは完全に破壊され、新しい状態をもった別のコンポーネントが生成されます。

<strong>It's strongly recommended that you assign proper keys whenever you build dynamic lists.</strong>If you don't have an appropriate key handy, you may want to consider restructuring your data so that you do.

<strong>これは非常に大切なことですが、動的に生成されるリストにおいても、適切な key を与えるようにしてください。</strong>もし適切な key をうまく与えれない場合には、そもそもデーター構造を見直す必要があります。

If you don't specify any key, React will warn you and fall back to using the array index as a key – which is not the correct choice if you ever reorder elements in the list or add/remove items anywhere but the bottom of the list. Explicitly passing <code>key={i}</code> silences the warning but has the same problem so isn't recommended in most cases.

Key を与えなかった場合、React はあなたに警告を出し、仕方なく配列のインデックスをkeyとして用います。これは適切な方法ではないので、要素の順番を変える場合や、要素の最下部以外に要素を追加したり削除したりする場合に、問題が発生します。明示的に key={i} をわたすことで警告はなくなりますが、しかし問題が解決されたわけではありませんので、この方法は推奨できません。

Component keys don't need to be globally unique, only unique relative to the immediate siblings.

コンポーネントに与える key は、グローバル環境においてユニークである必要はなく、単に特定の空間の兄弟要素内でユニークになるようにしてください。
<h3><a class="anchor" name="implementing-time-travel"></a>Implementing Time Travel</h3>
タイムトラベルを実装する

For our move list, we already have a unique ID for each step: the number of the move when it happened. In the Game's <code>render</code> method, add the key as <code>&lt;li key={move}&gt;</code> and the key warning should disappear:

さて、私達が作成したリストはしっかりと、ユニークなIDをそれぞれのステップが持っています。その手が打たれた時の番号がIDとして使われていますので。ですので次は、Game コンポーネントの render メソッド内に、key を追加した <code>&lt;li key={move}&gt;</code> を加えましょう。そうすれば警告は消えるはずです。
<div class="highlight">
<pre><code class="language-js" data-lang="js">    <span class="kr">const</span> <span class="nx">moves</span> <span class="o">=</span> <span class="nx">history</span><span class="p">.</span><span class="nx">map</span><span class="p">((</span><span class="nx">step</span><span class="p">,</span> <span class="nx">move</span><span class="p">)</span> <span class="o">=&gt;</span> <span class="p">{</span>
      <span class="kr">const</span> <span class="nx">desc</span> <span class="o">=</span> <span class="nx">move</span> <span class="o">?</span>
        <span class="s1">'Move #'</span> <span class="o">+</span> <span class="nx">move</span> <span class="o">:</span>
        <span class="s1">'Game start'</span><span class="p">;</span>
      <span class="k">return</span> <span class="p">(</span>
<span class="hll">        <span class="o">&lt;</span><span class="nx">li</span> <span class="nx">key</span><span class="o">=</span><span class="p">{</span><span class="nx">move</span><span class="p">}</span><span class="o">&gt;</span>
</span>          <span class="o">&lt;</span><span class="nx">a</span> <span class="nx">href</span><span class="o">=</span><span class="s2">"#"</span> <span class="nx">onClick</span><span class="o">=</span><span class="p">{()</span> <span class="o">=&gt;</span> <span class="k">this</span><span class="p">.</span><span class="nx">jumpTo</span><span class="p">(</span><span class="nx">move</span><span class="p">)}</span><span class="o">&gt;</span><span class="p">{</span><span class="nx">desc</span><span class="p">}</span><span class="o">&lt;</span><span class="err">/a&gt;</span>
        <span class="o">&lt;</span><span class="err">/li&gt;</span>
      <span class="p">);</span>
    <span class="p">});</span>
</code></pre>
</div>
<a href="https://codepen.io/gaearon/pen/PmmXRE?editors=0010">View the current code.</a>

Clicking any of the move links throws an error because <code>jumpTo</code> is undefined. Let's add a new key to Game's state to indicate which step we're currently viewing.

move リストのリンクをクリックすると、エラーが出てしまいます。何故なら  jumpTo メソッドが定義されていないからです。では Game コンポーネントの state に新しい項目を追加して、どのステップを今我々が見ようとしているかを判断するために用いましょう。

First, add <code>stepNumber: 0</code> to the initial state in Game's <code>constructor</code>:

まず、Game コンストラクターの中で、stepNumber: 0 という初期状態を与えます。
<div class="highlight">
<pre><code class="language-js" data-lang="js"><span class="kr">class</span> <span class="nx">Game</span> <span class="kr">extends</span> <span class="nx">React</span><span class="p">.</span><span class="nx">Component</span> <span class="p">{</span>
  <span class="nx">constructor</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">super</span><span class="p">();</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">state</span> <span class="o">=</span> <span class="p">{</span>
      <span class="nx">history</span><span class="o">:</span> <span class="p">[{</span>
        <span class="nx">squares</span><span class="o">:</span> <span class="nb">Array</span><span class="p">(</span><span class="mi">9</span><span class="p">).</span><span class="nx">fill</span><span class="p">(</span><span class="kc">null</span><span class="p">),</span>
      <span class="p">}],</span>
<span class="hll">      <span class="nx">stepNumber</span><span class="o">:</span> <span class="mi">0</span><span class="p">,</span>
</span>      <span class="nx">xIsNext</span><span class="o">:</span> <span class="kc">true</span><span class="p">,</span>
    <span class="p">};</span>
  <span class="p">}</span>
</code></pre>
</div>
Next, we'll define the <code>jumpTo</code> method in Game to update that state. We also want to update <code>xIsNext</code>. We set <code>xIsNext</code> to true if the index of the move number is an even number.

次に、jumpTo メソッドを Game コンポーネントの中で定義して、このメソッドによって状態を更新することにしましょう。その際に xIsNext も変更することにします。xIsNext を、move number が偶数の場合には、true にします。

Add a method called <code>jumpTo</code> to the Game class:

では jumpTo メソッドを Game クラスに追加しましょう。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
    <span class="c1">// this method has not changed</span>
  <span class="p">}</span>

<span class="hll">  <span class="nx">jumpTo</span><span class="p">(</span><span class="nx">step</span><span class="p">)</span> <span class="p">{</span>
</span><span class="hll">    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
</span><span class="hll">      <span class="nx">stepNumber</span><span class="o">:</span> <span class="nx">step</span><span class="p">,</span>
</span><span class="hll">      <span class="nx">xIsNext</span><span class="o">:</span> <span class="p">(</span><span class="nx">step</span> <span class="o">%</span> <span class="mi">2</span><span class="p">)</span> <span class="o">===</span> <span class="mi">0</span><span class="p">,</span>
</span><span class="hll">    <span class="p">});</span>
</span><span class="hll">  <span class="p">}</span>
</span>
  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="c1">// this method has not changed</span>
  <span class="p">}</span>
</code></pre>
</div>
Then update <code>stepNumber</code> when a new move is made by adding <code>stepNumber: history.length</code> to the state update in Game's <code>handleClick</code>:

新しい手が打たれた時に、stepNumber を更新するようにしましょう。Gameコンポーネントの <code>handleClick</code>内で状態を変更するために、 <code>stepNumber: history.length</code> を加えます。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">handleClick</span><span class="p">(</span><span class="nx">i</span><span class="p">)</span> <span class="p">{</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">history</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">history</span><span class="p">.</span><span class="nx">slice</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">stepNumber</span> <span class="o">+</span> <span class="mi">1</span><span class="p">);</span>
</span>    <span class="kr">const</span> <span class="nx">current</span> <span class="o">=</span> <span class="nx">history</span><span class="p">[</span><span class="nx">history</span><span class="p">.</span><span class="nx">length</span> <span class="o">-</span> <span class="mi">1</span><span class="p">];</span>
    <span class="kr">const</span> <span class="nx">squares</span> <span class="o">=</span> <span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">.</span><span class="nx">slice</span><span class="p">();</span>
    <span class="k">if</span> <span class="p">(</span><span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">squares</span><span class="p">)</span> <span class="o">||</span> <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">])</span> <span class="p">{</span>
      <span class="k">return</span><span class="p">;</span>
    <span class="p">}</span>
    <span class="nx">squares</span><span class="p">[</span><span class="nx">i</span><span class="p">]</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span> <span class="o">?</span> <span class="s1">'X'</span> <span class="o">:</span> <span class="s1">'O'</span><span class="p">;</span>
    <span class="k">this</span><span class="p">.</span><span class="nx">setState</span><span class="p">({</span>
      <span class="nx">history</span><span class="o">:</span> <span class="nx">history</span><span class="p">.</span><span class="nx">concat</span><span class="p">([{</span>
        <span class="nx">squares</span><span class="o">:</span> <span class="nx">squares</span>
      <span class="p">}]),</span>
<span class="hll">      <span class="nx">stepNumber</span><span class="o">:</span> <span class="nx">history</span><span class="p">.</span><span class="nx">length</span><span class="p">,</span>
</span>      <span class="nx">xIsNext</span><span class="o">:</span> <span class="o">!</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">xIsNext</span><span class="p">,</span>
    <span class="p">});</span>
  <span class="p">}</span>
</code></pre>
</div>
Now you can modify Game's <code>render</code> to read from that step in the history:

さらに Game コンポーネントの render メソッドを変更することで、history 内のstep を読み取るようにします。
<div class="highlight">
<pre><code class="language-javascript" data-lang="javascript">  <span class="nx">render</span><span class="p">()</span> <span class="p">{</span>
    <span class="kr">const</span> <span class="nx">history</span> <span class="o">=</span> <span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">history</span><span class="p">;</span>
<span class="hll">    <span class="kr">const</span> <span class="nx">current</span> <span class="o">=</span> <span class="nx">history</span><span class="p">[</span><span class="k">this</span><span class="p">.</span><span class="nx">state</span><span class="p">.</span><span class="nx">stepNumber</span><span class="p">];</span>
</span>    <span class="kr">const</span> <span class="nx">winner</span> <span class="o">=</span> <span class="nx">calculateWinner</span><span class="p">(</span><span class="nx">current</span><span class="p">.</span><span class="nx">squares</span><span class="p">);</span>

    <span class="c1">// the rest has not changed</span>
</code></pre>
</div>
<a href="https://codepen.io/gaearon/pen/gWWZgR?editors=0010">View the current code.</a>

If you click any move link now, the board should immediately update to show what the game looked like at that time.

ここまでの作業を終えると、move リンクをクリックしたときに、盤上の状態が瞬時に変化して、その手が打たれた瞬間の状態へと更新されます。

You may also want to update <code>handleClick</code> to be aware of <code>stepNumber</code> when reading the current board state so that you can go back in time then click in the board to create a new entry. (Hint: It's easiest to <code>.slice()</code> off the extra elements from <code>history</code> at the very top of <code>handleClick</code>.)

!!何言ってるのかわからないので飛ばす
<h3><a class="anchor" name="wrapping-up"></a>Wrapping Up</h3>
まとめ

Now, you've made a tic-tac-toe game that:

さて、三目並べゲームを以下のような手順をおって作成してきました。
<ul>
 	<li>lets you play tic-tac-toe,
三目並べゲームがプレイできるようにし、</li>
 	<li>indicates when one player has won the game,
どちらかのプレイヤーが勝利した場合にそれを表示できるようにし、</li>
 	<li>stores the history of moves during the game,
ゲーム中の全ての手を履歴として保持するようにし、</li>
 	<li>allows players to jump back in time to see older versions of the game board.
プレイヤーに過去の盤上の状態に戻れるようにしました。</li>
</ul>
Nice work! We hope you now feel like you have a decent grasp on how React works.

お疲れ様でした！React がどのように機能するのか、かなり理解できたのではないでしょうか。

Check out the final result here: <a href="https://codepen.io/gaearon/pen/gWWZgR?editors=0010">Final Result</a>.

最終的な結果は次のようになります。

If you have extra time or want to practice your new skills, here are some ideas for improvements you could make, listed in order of increasing difficulty:

時間に余裕があり、さらに新しい技術を身に着けたいのであれば、次のような実装をおこなってみるのはどうでしょうか。このリストは簡単なものから難しいものへと順番に並んでいます。

(!!見ればわかるので訳さない)
<ol>
 	<li>Display the move locations in the format "(1, 3)" instead of "6".</li>
 	<li>Bold the currently-selected item in the move list.</li>
 	<li>Rewrite Board to use two loops to make the squares instead of hardcoding them.</li>
 	<li>Add a toggle button that lets you sort the moves in either ascending or descending order.</li>
 	<li>When someone wins, highlight the three squares that caused the win.</li>
</ol>
Throughout this tutorial, we have touched on a number of React concepts including elements, components, props, and state. For a more in-depth explanation for each of these topics, check out <a href="https://facebook.github.io/react/docs/hello-world.html">the rest of the documentation</a>. To learn more about defining components, check out the <a href="https://facebook.github.io/react/docs/react-component.html"><code>React.Component</code> API reference</a>.

このチュートリアルを通して、React のコンセプトに触れてきました。element, component, props, state などです。より各項目について知識を深めるためには、ドキュメントを参照してください。コンポーネントの定義についてより学びたい場合には、<a href="https://facebook.github.io/react/docs/react-component.html"><code>React.Component</code> API reference</a> を参照してください。

&nbsp;
