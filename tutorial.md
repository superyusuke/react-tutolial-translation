勝手に日本語化シリーズ、今回は React の公式 Tutorial にチャレンジします。例によってわかりづらいところはかなり言葉を足しています。

https://facebook.github.io/react/tutorial/tutorial.html

Tutorial: Intro To React

チュートリアル：React への案内
Before We Start

始める前に

What We're Building

作るもの

Today, we're going to build an interactive tic-tac-toe game.

今日は、3目並べゲームを作っていきます。これはユーザー操作を受付け、それに反応して進んでいく、インタラクティブなゲームです。

If you like, you can check out the final result here: Final Result. Don't worry if the code doesn't make sense to you yet, or if it uses an unfamiliar syntax. We will be learning how to build this game step by step throughout this tutorial.

完成形をこちらから見ることもできます。でも、今のところ、コードが何を意味しているのかわからなくても、使われているシンタックスが見慣れないものであっても、心配しないで大丈夫です。これから段階的に、このゲームを作る方法を、チュートリアルを通して学んでいきましょう。

Try playing the game. You can also click on a link in the move list to go "back in time" and see what the board looked like just after that move was made.

まずは実際にゲームをプレイしてみてください。右側にある「move list」をクリックして、「時間を逆戻し」することもできます。これは使えば、その手を打った直後の状態に戻ることができます。

Once you get a little familiar with the game, feel free to close that tab, as we'll start from a simpler template in the next sections.

ゲームの概要が大体理解できたら、タブを閉じて、まずはシンプルなテンプレートを作るところから始めていきましょう。

Prerequisites

前準備

We'll assume some familiarity with HTML and JavaScript but you should be able to follow along even if you haven't used them before.

ある程度 HTML と JavaScript に慣れている前提で進めていきますが、全くそれらの知識がないかたも理解することは出来ると思います。

If you need a refresher on JavaScript, we recommend reading this guide. Note that we're also using some features from ES6, a recent version of JavaScript. In this tutorial, we're using arrow functions, classes, let, and const statements. You can use Babel REPL to check what ES6 code compiles to.

過去に JS を書いていたけれどしばらく離れていて、久しぶりに JS に戻ってきた人には、このガイドを読むことをおすすめします。直近の JS バージョンである ES6 をの機能を使っていきますので。このチュートリアルでは、ES6の機能から、arrow functions, classes, それから let と const よる変数の宣言を用いていきます。Babel REPLを使えば ES6 のコードがどのようにコンパイルされるか確認するこができます。(訳注：フロントエンドをされている人には特に説明は必要ないとは思いますが、現在 gulp 等のタスクマネージャーを用いて、先行して策定されたバージョンであるES6で書いたJSを、ブラウザが認識できる現行のJSへとトランスコンパイルするのが標準的なワークフローです。ES6に馴染みがない、Gulp等に馴染みがない、という人は上記のガイドを参照するといいよ、とのことです。)



How to Follow Along

作業方法

There are two ways to complete this tutorial: you could either write the code right in the browser, or you could set up a local development environment on your machine. You can choose either option depending on what you feel comfortable with.

このチュートリアルに取り組むための方法は2つあります。コードをブラウザで直接書く方法(訳注：Codepenを使っていく方法です)、もしくはローカル開発環境をつくってそこでコーディングする方法の２つです。自分が好きな方を選択してください。

IF YOU PREFER TO WRITE CODE IN THE BROWSER

ブラウザでコーディングしたい場合

This is the quickest way to get started!

これが、一番早く始めることのできる方法です。

First, open this starter code in a new tab. It should display an empty tic-tac-toe field. We will be editing that code during this tutorial.

まずはこのリンクを開いてください。中に何も記録されていない、三目揃えゲームが表示されます。このコードをチュートリアルの中で書き換えていきます。

You can now skip the next section about setting up a local development environment and head straight to the overview.

この方法を選ぶ場合は、次のローカル開発環境のセクションは飛ばして、overvieまで進みましょう。

IF YOU PREFER TO WRITE CODE IN YOUR EDITOR

自分のエディターでコーディングしたい場合

Alternatively, you can set up a project on your computer.

自分のコンピューター内にプロジェクトを立ち上げてコーディングする方法もあります。

Note: this is completely optional and not required for this tutorial!

アドバイス：このチュートリアルをおこなうためには必須ではありません。任意の選択肢です。

This is more work, but lets you work from the comfort of your editor.

これを選択する場合にはブラウザでコーディングする場合よりも追加の作業が必要になりますが、しかし慣れ親しんだエディターで作業をすることができます。

If you want to do it, here are the steps to follow:

その場合には、次の作業をおこなってください。

Make sure you have a recent version of Node.js installed.
最近のバージョンのNode.jsをインストールします。
Follow the installation instructions to create a new project.
次の記事を読んで新しいプロジェクトを作成してください。(訳注：NPMであるcreate-react-appを使ってコマンドラインから一発で開発環境を作成できます)
Delete all files in the src/ folder of the new project.
src/以下のフォルダーを全て削除。
Add a file named index.css in the src/ folder with this CSS code.
index.css という名前のファイルをsrc/の下に配置し、this CSS code の内容をコピー。
Add a file named index.js in the src/ folder with this JS code, and then add three lines to the top of it:
index.js という名前のファイルをsrc/の下に配置し、this JS code の内容をコピー。さらに次の3行を冒頭に追加してください。
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
Now if you run npm start in the project folder and open http://localhost:3000 in the browser, you should see an empty tic-tac-toe field.

ここまで準備が整ったら、run npm start をして http://localhost:3000 をブラウザで開けば、空の三目並べゲームが現れます。

We recommend following these instructions to configure syntax highlighting for your editor.

次の記事を読んで、エディターのハイライト機能を設定することをおすすめします。

Help, I'm Stuck!

助けて！ハマったよ！

If you get stuck, check out the community support resources. In particular, Reactiflux chat is a great way to get quick help. If you don't get a good answer anywhere, please file an issue, and we'll help you out.

行き詰まってしまった場合に、React コミュニティが用意した様々なリソースを参照してください。とくに、Reactiflux chat はすぐに助けをもらえる素晴らしい方法です。(訳注：英語で質問しないといけないですが…日本のReactコミュニティのslackもきっとあるはず！自分は知らないですが…) もしどのリソースを参照しても解決できない場合には、それをまとめて私たちに送ってください。きっと手助けできるはずです。

With this out of the way, let's get started!

では始めましょう！

Overview

概要

What is React?

React とは？

React is a declarative, efficient, and flexible JavaScript library for building user interfaces.

React は declarative(訳注：宣言的プログラミングという分類があるようですが、わたしにはわからないので原語のままにしておきます)かつフレキシブルなJavaScript ライブラリで、ユーザーインターフェースの作成のために用いることができます。

React has a few different kinds of components, but we'll start with React.Componentsubclasses:

React はそれほど多くはありませんが、しかし異なる種類のコンポーネントを幾つか持っています。その中からまずは React.component というサブクラスから始めていきましょう。

class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
We'll get to the funny XML-like tags in a second. Your components tell React what you want to render – then React will efficiently update and render just the right components when your data changes.

まずは、ちょっと変わった、しかしXMLに似ているタグを見てきましょう。あなたがコンポーネントを書くと、それは React へ、どのような物をレンダリングしたらいいのかを伝えます。そしてそれを伝え聞いた React はその通りコンポーネントをレンダリングし、またデータに変更があればコンポーネントを効率的に更新し、再レンダリングを行います。

Here, ShoppingList is a React component class, or React component type. A component takes in parameters, called props, and returns a hierarchy of views to display via the rendermethod.

この例では、ShoppingList がReact component クラスです。 もしくは React component 形式であるといってもよいでしょう。Component は props と呼ばれる引数を受取り、render メソッドと、その中にある returnによって、構造化された view を返します。(訳注：view は後にレンダリングされて、表示される内容のこと)

The render method returns a description of what you want to render, and then React takes that description and renders it to the screen. In particular, render returns a React element, which is a lightweight description of what to render. Most React developers use a special syntax called JSX which makes it easier to write these structures. The <div /> syntax is transformed at build time to React.createElement('div'). The example above is equivalent to:

Render メソッドはレンダーする内容を return し、そして React がそれを受け取って、その内容をレンダリングし、スクリーンに表示します。Render メソッドが返しているものは、React element というもので、これにはレンダー内容が含まれているわけですが、軽量な点が特徴です。React 開発者のほとんどは、JSX という専用の構文を使ってこれらの構造を記述します。JSX を使うことでより簡単に書くことが可能になるからです。実際にはこのJSX構文はどのように処理されるのでしょうか。例えば<div/>というJSX構文は、ビルド時にReact.createElement('div') へと変形されます。また、今取り上げているザッカーバーグのショッピングリストクラスのサンプルは、次のように変形されられます。

return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 children ... */),
  React.createElement('ul', /* ... ul children ... */)
);
See full expanded version.

If you're curious, createElement() is described in more detail in the API reference, but we won't be using it directly in this tutorial. Instead, we will keep using JSX.

さらに createElement() へ興味があれば API reference に詳細が書かれていますので参考にしてください。このレクチャーにおいては createElement() ではなくて JSX を用いていくことにします。

You can put any JavaScript expression within braces inside JSX. Each React element is a real JavaScript object that you can store in a variable or pass around your program.

JSX コード内の {} の中には、どのような JavaScript 表現をも書くことができます。 React element は全て純粋な JavaScript オブジェクトなので、変数の中にこれを保持したり、引数として渡すことが可能です。

The ShoppingList component only renders built-in DOM components, but you can compose custom React components just as easily, by writing <ShoppingList />. Each component is encapsulated so it can operate independently, which allows you to build complex UIs out of simple components.

先のShoppingList コンポーネントがレンダリングしているのは、もとから用意されている DOM (訳注：divやh1といったHTMLの規格で元から用意されている要素) しか含まれないコンポーネントですが、このカスタム React component を組み立てる (訳注：単に使うということ) 方法は非常に簡単で、<ShoppingList />と書くだけです。それぞれのコンポーネントはカプセル化されているので、それぞれ独立して運用することが可能で、これによって複雑な UI をシンプルなコンポーネントの組み合わせによって作成することができます。

(訳注(英辞郎からそのままコピペ)：カプセル化する◆オブジェクト指向プログラミングで使用される技法の一つ。薬をカプセルに入れるかのごとく、データとそれらを操作する関数を一つの構造体としてまとめてオブジェクトに格納することにより、内部で行われる処理を外部から隠し、オブジェクトに対するアクセス方法を限定する。)

Getting Started

始めよう

Start with this example: Starter Code.

まずはこのサンプルから始めることにしましょう。

It contains the shell of what we're building today. We've provided the styles so you only need to worry about the JavaScript.

このサンプルには、これから作っていくアプリケーションの骨格だけが含まれています。CSS スタイルも既にこれに含まれていますので、これからの作業においては JavaScript についてだけ考えていだければよいということになります。

In particular, we have three components:

具体的には、3つのコンポーネントについて作業をしていきます。

Square
Board
Game
The Square component renders a single <button>, the Board renders 9 squares, and the Game component renders a board with some placeholders that we'll fill in later. None of the components are interactive at this point.

Square コンポーネントは<button>だけをレンダリングするコンポーネントで、Board コンポーネントは 9個の Square コンポーネントをレンダリングするコンポーネントです。Game コンポーネントは Board を一つレンダリングします。これには幾つかの情報を表示するエリアを持っていて、後ほど実装することになります。

Passing Data Through Props

データを Props を用いて渡す

Just to get our feet wet, let's try passing some data from the Board component to the Square component.

さあまずは、データを渡してみることにしましょう。Board コンポーネントから Square コンポーネントへとデータをわたします。

In Board's renderSquare method, change the code to pass a value prop to the Square:

Board コンポーネント内にある renderSquare メソッドに変更を加え、value という名前の prop (訳注：何かを支えたり、助けるために使う棒のこと)　を Square コンポーネントに渡すようにします。

class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;
  }
Then change Square's render method to show that value by replacing {/* TODO */} with {this.props.value}:

次に Square コンポーネント内の render メソッドを変更します。受け取った値を表示できるように、{/* TODO */} を {this.props.value}へと変更してください。

class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
Before:

変更前



After: You should see a number in each square in the rendered output.

変更後：レンダリング結果をみると、それぞれのマスに数字が表示されているはずです。



View the current code.

An Interactive Component

インタラクティブなコンポーネント(訳注：ユーザー操作を受け付け、それに反応するコンポーネント)

Let's make the Square component fill in an "X" when you click it. Try changing the button tag returned in the render() function of the Square like this:

では次に、クリックした時に"X"が表示されるよう Square コンポーネントを変更していきましょう。Square コンポーネント内の render 関数が返す(訳注：JSのreturnで返してくる部分です) button タグに変更を加えます。

class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
If you click on a square now, you should get an alert in your browser.

すると、マス目をクリックした際に、アラートがブラウザに表示されるはずです。

This uses the new JavaScript arrow function syntax. Note that we're passing a function as the onClick prop. Doing onClick={alert('click')} would alert immediately instead of when the button is clicked.

このコードは JavaScript の新しいアローファンクション構文を使っています。注意してほしいでのですが、ここで渡しているのは関数です。もし onClick={alert('click')} としてしまうと(訳注：関数ではなくて直接 alert の実行文を書いてしまうと) ボタンがクリックした時に動作するのではなく、即座にアラートが発生してしまいます。

React components can have state by setting this.state in the constructor, which should be considered private to the component. Let's store the current value of the square in state, and change it when the square is clicked.

React のコンポーネントは、コンストラクター内に this.state を設置することで、状態=stateを保持することができます。これは他のコンポーネントに対して private です。では、マス目の現在の値を state 内に保持し、クリックされたときには変更されるように、コードを書き換えていきましょう。

(英辞郎より引用：プライベートな◆あるオブジェクトに属するメンバーが、そのオブジェクトの内部でのみアクセス可能であること。訳さずに「privateな」と表現されることも多い。)

First, add a constructor to the class to initialize the state:

まずはコンストラクタをクラス内に追加して、state 状態を初期化するようにします。

class Square extends React.Component {
  constructor() {
    super();
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
In JavaScript classes, you need to explicitly call super(); when defining the constructor of a subclass.

JSのクラスにおいては、コンストラクタを、あるクラスのサブクラスのコンストラクタとして定義するためには、明示的にsuper();を宣言する必要があります。

Now change the Square render method to display the value from the current state, and to toggle it on click:

では Square コンポーネント内の render メソッドを変更して、現在の状態 state を表示し、またクリックされた際には状態が変更されるようにしましょう。

Replace this.props.value with this.state.value inside the <button> tag.
this.props.valueを変更し、this.state.valueにしてください。これは<button>タグの中にあります。
Replace the () => alert() event handler with () => this.setState({value: 'X'}).
() => alert() というイベントハンドラーの内容を変更して、 () => this.setState({value: 'X'}) とします。
Now the <button> tag looks like this:

この変更を加えると、<button>タグは次のようになっているはずです。

class Square extends React.Component {
  constructor() {
    super();
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => this.setState({value: 'X'})}>
        {this.state.value}
      </button>
    );
  }
}
Whenever this.setState is called, an update to the component is scheduled, causing React to merge in the passed state update and rerender the component along with its descendants. When the component rerenders, this.state.value will be 'X' so you'll see an X in the grid.

this.setState メソッドが実行されると、コンポーネントへのアップデートが予定に組み込まれます。そしてそれによって React は、受け取った状態 state への更新を、現在の state へとマージした上で、コンポーネントをその子コンポーネントも含めて、再レンダリングします。このコンポーネントの再レンダリングの際には、this.state.value の値は "X" へと変更されているので、結果としてグリッド内には X が表示されることになります。

If you click on any square, an X should show up in it.

どのマス目をクリックしても、X が現れるようになりました。

View the current code.

Developer Tools

開発者用ツール

The React Devtools extension for Chrome and Firefox lets you inspect a React component tree in your browser devtools.

React 用の開発者向け拡張機能が、Chrome と Firefox において用意されています。これを使うと、リアクトコンポーネントのツリーをブラウザから確認することができます。



It lets you inspect the props and state of any of the components in your tree.

コンポーネントツリー内の、全ての props と 状態 state を確認することができます。

After installing it, you can right-click any element on the page, click "Inspect" to open the developer tools, and the React tab will appear as the last tab to the right.

ツールの使い方ですが、まずこのツールをインストールした後、ページ上の要素の上で右クリックをして、"検証する"を選んでディベロッパーツールを開きます。その後、React tab がタブの一番右側にあるはずなので、これを開きます。

However, note there are a few extra steps to get it working with CodePen:

ただしCodePen内でこのツールを使うためには、いくつか追加の設定が必要です。

Log in or register and confirm your email (required to prevent spam).
ログインもしくは新しくアカウントを登録した上で、アカウントの Email 確認を済ませておく。(これはスパムだと認定されないために必要です)
Click the "Fork" button.
Fork ボタンを押す
Click "Change View" and then choose "Debug mode".
Change View ボタンを押して、その後にDebug mode を選ぶ。
In the new tab that opens, the devtools should now have a React tab.
それによって開いた新しいタブの中では、ディベロッパーツールがReact タブを表示してくれます。
Lifting State Up

状態を保持する階層を上の階層へ持ち上げる

We now have the basic building blocks for a tic-tac-toe game. But right now, the state is encapsulated in each Square component. To make a fully-working game, we now need to check if one player has won the game, and alternate placing X and O in the squares. To check if someone has won, we'll need to have the value of all 9 squares in one place, rather than split up across the Square components.

さあここまでの作業で、基本的なゲームの構造を作り終えました。しかし現時点では、状態はそれぞれ Square コンポーネントの内部にカプセル化されています。このゲームが意図したとおりに動いてもらうためには、さらに機能を追加しないといけません。どのプレイヤーが勝ったのかをチェックする機能と、それからプレイヤーがクリックした時に現れるマークを、XマークとOマークへと交互に入れ替える機能です。誰が勝者なのかを判断する機能をつけるためには、9個のマス目の値を全て、1箇所で保持する必要があります。それぞれの Square コンポーネントに散在していていはいけまんせん。

You might think that Board should just inquire what the current state of each Square is. Although it is technically possible to do this in React, it is discouraged because it tends to make code difficult to understand, more brittle, and harder to refactor.

そんなことをしなくても、Board コンポーネントが、Square の中にある現在の状態 state を全て問い合わせればいいではないか、と考えたかもしれません。もちろん技術的にそうすることは可能ですが、あまりおすすめできません。何故かというと、そうしてしまうとコードが複雑になって理解しづらく、容易に破綻しやすくなってしまい、リファクタリングもやりにくいコードになってしまいます。

Instead, the best solution here is to store this state in the Board component instead of in each Square – and the Board component can tell each Square what to display, like how we made each square display its index earlier.

ではどうするのがいいかというと、状態を Board コンポーネントに持たせればよいのです。つまり Square コンポーネントそれぞれには、状態を持たせません。そのうえで、Board コンポーネントが、それぞれの Square コンポーネントに対して、何を表示すべきなのかその内容を伝えるようにします。これはちょうど、我々が既に作業した Square に 自分の番号を表示させた時にやり方と似ています。

(訳注：一つ階層上にあるBoardからpropsを受取り、Square はそれをthis.props.valueという構文によってそれを表示していた)

<button className="square">
        {this.props.value}
      </button>
When you want to aggregate data from multiple children or to have two child components communicate with each other, move the state upwards so that it lives in the parent component. The parent can then pass the state back down to the children via props, so that the child components are always in sync with each other and with the parent.

複数の子コンポーネントが持つデータを集計したり、２つの子コンポーネント同士がお互いにデータをやり取りする必要がある場合には、状態 State を上の階層へと譲渡していき、親コンポーネントが状態を持つようにしましょう。親コンポーネントは、子コンポーネントへと props を用いて、下へと伝えて行くことが出来るので、子コンポーネントはいつでも子コンポーネント同士で同期することができます。また子コンポーネントは親コンポーネントとも同期することができます。

Pulling state upwards like this is common when refactoring React components, so let's take this opportunity to try it out. Add a constructor to the Board and set its initial state to contain an array with 9 nulls, corresponding to the 9 squares:

このように、状態を上へと引き上げていく手法は、React のリファクタリングにおいて一般的なものです。良い機会ですから、やってみましょう。Board コンポーネントにコンストラクターを追加し、9マスあるので9つの null 配列を、初期状態として持つように設定します。

class Board extends React.Component {
  constructor() {
    super();
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  renderSquare(i) {
    return <Square value={i} />;
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
We'll fill it in later so that a board looks something like

ここには後ほど次のような値が入る予定です。

[
  'O', null, 'X',
  'X', 'X', 'O',
  'O', null, null,
]
Board's renderSquare method currently looks like this:

Board コンポーネント内の renderSquare メソッドは、現在次のようになっています。

  renderSquare(i) {
    return <Square value={i} />;
  }
Modify it to pass a value prop to Square.

変更を加え、value という名前のprop を Square コンポーネントへと渡すようにします。

  renderSquare(i) {
    return <Square value={this.state.squares[i]} />;
  }
View the current code.

Now we need to change what happens when a square is clicked. The Board component now stores which squares are filled, which means we need some way for Square to update the state of Board. Since component state is considered private, we can't update Board's state directly from Square.

では次に、マス目がクリックされた時の挙動を変更しましょう。マス目にどのようなマークが記録されているかは、今や Board コンポーネントが保持しています。ですから、「Square コンポーネント」が「Board コンポーネントの状態を変更する方法」を、用意せねばいけません。コンポーネントの状態は private ですから、Board コンポーネントの状態を、Square コンポーネントから直接更新することはできません。

The usual pattern here is pass down a function from Board to Square that gets called when the square is clicked. Change renderSquare in Board again so that it reads:

こういった場合に使われる典型的な設計パターンは、関数を Board コンポーネントから Square コンポーネントへと渡し、Square コンポーネントがクリックされた際に、その渡された関数が実行されるようにすることです。そうなるように、Board コンポーネント内の renderSquare を再度変更しましょう。

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }
We split the returned element into multiple lines for readability, and added parens around it so that JavaScript doesn't insert a semicolon after return and break our code.

return 内の HTML要素の記述箇所においては、可読性を上げるために、複数行に改行しています。さらに丸括弧でそれをくくっています。これは JavaScript がreturn の後ろに semicolon を追加して、コードが破綻しないようにするためです。(訳注：return 改行 <square/> と書いてしまうと、return の後ろにセミコロンを入れて JS が解釈し意図しない挙動になるため、そのようなトラブルが発生しないように、上記のような記法を取っている、ということ。)

Now we're passing down two props from Board to Square: value and onClick. The latter is a function that Square can call. Let's make the following changes to Square:

さて、2つのpropsを、BoardからSquareへと渡すようになりました。2つのpropsはそれぞれ、valueとonClickでしたね。さらに、onClickがSquareから呼び出すことができるよう、変更を Square に対して加えましょう。

Replace this.state.value with this.props.value in Square's render.
this.state.value を変更し、 this.props.value にする。これは次の場所にある： Square の中の render
Replace this.setState() with this.props.onClick() in Square's render.
this.setState() を変更し、 this.props.onClick() とする。これは次の中にある：Square の中の render.
Delete constructor definition from Square because it doesn't have state anymore.
constructor をSquareコンポーネントから削除する。何故なら Square コンポーネントは状態を既に持っていないので、必要がないから。
After these changes, the whole Square component looks like this:

これらの変更を加えた後、Square コンポーネントの全体像は、このようになっているはずです。

class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => this.props.onClick()}>
        {this.props.value}
      </button>
    );
  }
}
Now when the square is clicked, it calls the onClick function that was passed by Board. Let's recap what happens here:

この状態でマス目をクリックすると、Square コンポーネントは onClick 関数を呼び出します。この呼び出される関数は、Board コンポーネントから渡されたものです。(訳注：this.props.onClick()は、Boardから受けとったpropsの中にある関数。)

では今までやってきたことをおさらいしましょう。

The onClick prop on the built-in DOM <button> component tells React to set up a click event listener.
標準搭載の<button>コンポーネント内に配置された、onClickというpropは、React へ「クリックイベントリスナー」をこのコンポーネントへ設置することを要求する。
When the button is clicked, React will call the onClick event handler defined in Square's render() method.
ボタンがクリックされると、ReactはonClickイベントに紐付けられた関数を呼び出す。このイベントへの紐付けは、Square のrender()メソッド内で定義されている。
This event handler calls this.props.onClick(). Square's props were specified by the Board.
this.props.onClick()を呼び出す。Square が受け取っている props は、Board コンポーネントの中で定義されている。
Board passed onClick={() => this.handleClick(i)} to Square, so, when called, it runs this.handleClick(i) on the Board.
Board コンポーネントは onClick={() => this.handleClick(i)} を、Square コンポーネントへと渡しているので、これが呼び出されると、Board コンポーネント内の this.handleClick(i) を実行する。
We have not defined the handleClick() method on the Board yet, so the code crashes.
まだ handleClick() メソッドを Board コンポーネント内に定義していないので、この時点ではまだクリックするとクラッシュする。
Note that onClick on the DOM <button> component has a special meaning to React, but we could have called onClick prop in Square and handleClick in Board something else. It is, however, a common convention in React apps to use on* names for the handler prop names and handle* for their implementations.

注意してほしいのですが、<button> DOM 内に配置された onClick は、React において特殊な意味を持ちます。しかし同じ onClick という名前をもつ prop を Square コンポーネントにおいて呼び出すことができましたし、handleClick を Board コンポーネントなので呼び出しました。React における慣習として、on* をhandler 用の prop に付け、handle* をその実装に用います。

(訳注：まだ理解が十分ではないが、おそらく標準的なDOM要素、例えばdivやbutton内でonClick={関数}と書いた場合には、これはbuttonへクリックイベントハンドラーを定義する効果がある。しかし、カスタムコンポーネントにおいて、onClick={関数}として渡した場合には、これはクリックイベントハンドラーの指定ではなく、単にpropsとして子コンポーネントに渡される。このようにpropsとして渡す場合にはon*という名前をつけ、実際に実行する関数に関してはhandle*という名前をつけることが慣習になっている。ということだと思われる。)

Try clicking a square – you should get an error because we haven't defined handleClickyet. Add it to the Board class.

この時点でマス目をクリックすると、エラーが発生するはずです。何故ならまだhandleClick を定義していないからです。これを Board クラスに加えましょう。

class Board extends React.Component {
  constructor() {
    super();
    this.state = {
      squares: Array(9).fill(null),
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = 'X';
    this.setState({squares: squares});
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: X';

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
View the current code.

We call .slice() to copy the squares array instead of mutating the existing array. Jump ahead a section to learn why immutability is important.

訳注：飛ばす

Now you should be able to click in squares to fill them again, but the state is stored in the Board component instead of in each Square, which lets us continue building the game. Note how whenever Board's state changes, the Square components rerender automatically.

改めてマス目をクリックしてその中にマークが付くようになりました。Square コンポーネントをクリックしていますが、しかし状態は Board コンポーネントに保持されており、Square コンポーネントには保持されていません。これによってゲームの開発をさらに進めていけるようになりました。Board コンポーネントの状態が変更されると、どんなときでも自動的に Square コンポーネントが更新されていることに注目してください。

Square no longer keeps its own state; it receives its value from its parent Board and informs its parent when it's clicked. We call components like this controlled components.

Square コンポーネントは最早自分自身で状態を保持していません。つまり、値を親コンポーネントである Board から受け取って、親コンポーネントに対して、クリックされた時にその旨を告げているにすぎません。このようなコンポーネントをコントロールドコンポーネントと名付けることにします。

Why Immutability Is Important

(訳注: イミュータブルは重要な概念且つ、中身が正確にわからないと誤訳しそうなので飛ばす。簡単に言えば、this.state.value = 4 と直接変更するのではなく、一回コピーしたものを変更して、それを代入する手法を取ること。)

In the previous code example, we suggest using the .slice() operator to copy the squaresarray prior to making changes and to prevent mutating the existing array. Let's talk about what this means and why it is an important concept to learn.

There are generally two ways for changing data. The first method is to mutate the data by directly changing the values of a variable. The second method is to replace the data with a new copy of the object that also includes desired changes.

DATA CHANGE WITH MUTATION

var player = {score: 1, name: 'Jeff'};
player.score = 2;
// Now player is {score: 2, name: 'Jeff'}
DATA CHANGE WITHOUT MUTATION

var player = {score: 1, name: 'Jeff'};

var newPlayer = Object.assign({}, player, {score: 2});
// Now player is unchanged, but newPlayer is {score: 2, name: 'Jeff'}

// Or if you are using object spread syntax proposal, you can write:
// var newPlayer = {...player, score: 2};
The end result is the same but by not mutating (or changing the underlying data) directly we now have an added benefit that can help us increase component and overall application performance.

EASIER UNDO/REDO AND TIME TRAVEL

Immutability also makes some complex features much easier to implement. For example, further in this tutorial we will implement time travel between different stages of the game. Avoiding data mutations lets us keep a reference to older versions of the data, and switch between them if we need to.

TRACKING CHANGES

Determining if a mutated object has changed is complex because changes are made directly to the object. This then requires comparing the current object to a previous copy, traversing the entire object tree, and comparing each variable and value. This process can become increasingly complex.

Determining how an immutable object has changed is considerably easier. If the object being referenced is different from before, then the object has changed. That's it.

DETERMINING WHEN TO RE-RENDER IN REACT

The biggest benefit of immutability in React comes when you build simple pure components. Since immutable data can more easily determine if changes have been made it also helps to determine when a component requires being re-rendered.

To learn more about shouldComponentUpdate() and how you can build pure componentstake a look at Optimizing Performance.

Functional Components

ファンクショナル・コンポーネント

We've removed the constructor, and in fact, React supports a simpler syntax called functional components for component types like Square that only consist of a render method. Rather than define a class extending React.Component, simply write a function that takes props and returns what should be rendered.

すでにコンストラクタを取り除いてしまいましたが、React は ファンクショナル・コンポーネントを書くためのシンプルな構文を持っていますので、これは適切な処置です。ファンクショナル・コンポーネントというのは、今回の Square のように render メソッドしかもっていないコンポーネントです。　React.Component を拡張してクラスを規定するのではなく、単に props を引数に取り、レンダーされる内容を返す、そのような関数を書くことができます。

Replace the whole Square class with this function:

Square クラスを変更し、ファンクショナル・コンポーネントにしてしまいましょう。

function Square(props) {
  return (
    <button className="square" onClick={props.onClick}>
      {props.value}
    </button>
  );
}
You'll need to change this.props to props both times it appears. Many components in your apps will be able to be written as functional components: these components tend to be easier to write and React will optimize them more in the future.

this.props を変更し、props にしましょう。あなたのアプリケーション内の多くのコンポーネントは、ファンクショナルコンポーネントとして書けるはずです。ファンクショナルコンポーネントは書くのが簡単ですし、将来的には React はこれをより活用するようになります。

While we're cleaning up the code, we also changed onClick={() => props.onClick()} to just onClick={props.onClick}, as passing the function down is enough for our example. Note that onClick={props.onClick()} would not work because it would call props.onClickimmediately instead of passing it down.

さらに onClick={() => props.onClick()} を変更し onClick={props.onClick} にした点に注目しましょう。関数を Board コンポーネントから Square コンポーネントへと渡したわけですから、これだけで十分です。注意してほしいのは onClick={props.onClick()} と書いてしまうと意図したとおりには機能しません。何故なら、その場合には即座に props.onClick が実行されてしまうからです。

View the current code.

Taking Turns

プレイヤーが交代する

An obvious defect in our game is that only X can play. Let's fix that.

さて我々のゲームにある明らかな欠点は、X のプレイヤーしかプレイできない点です。直していきましょう。

Let's default the first move to be by 'X'. Modify our starting state in our Board constructor.

まず最初の手は、X から始まるようにしましょう。Board コンポーネント内の初期状態の設定を変更します。

class Board extends React.Component {
  constructor() {
    super();
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  }
Each time we move we shall toggle xIsNext by flipping the boolean value and saving the state. Now update Board's handleClick function to flip the value of xIsNext.

手をプレイする度に、xIsNext を true と false の間でひっくり返して、そして状態に記録します。では handleClick ファンクションを変更して、xIsNext がそのように変更されるようにしましょう。

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }
Now X and O take turns. Next, change the "status" text in Board's render so that it also displays who is next.

さあ、X と O が順番にプレイできるようになりました。次に、Board コンポーネント内の "status" と書かれたテキスト部分に、次に誰がプレイする番なのかを表示するようにしましょう。

  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');

    return (
      // the rest has not changed
After these changes you should have this Board component:

この変更を加えると、Board コンポーネントは以下の用になっているはずです。

class Board extends React.Component {
  constructor() {
    super();
    this.state = {
      squares: Array(9).fill(null),
      xIsNext: true,
    };
  }

  handleClick(i) {
    const squares = this.state.squares.slice();
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.state.squares[i]}
        onClick={() => this.handleClick(i)}
      />
    );
  }

  render() {
    const status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
View the current code.

Declaring a Winner

勝利者の宣言

Let's show when a game is won. Add this helper function to the end of the file:

次に、勝者が決まった場合に、それを表示するようにしましょう。そのために、次の関数をファイルの最後に追加します。

function calculateWinner(squares) {
  const lines = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  for (let i = 0; i < lines.length; i++) {
    const [a, b, c] = lines[i];
    if (squares[a] && squares[a] === squares[b] && squares[a] === squares[c]) {
      return squares[a];
    }
  }
  return null;
}
You can call it in Board's render function to check if anyone has won the game and make the status text show "Winner: [X/O]" when someone wins.

この関数を Board コンポーネントの render 関数の中で呼び出すことで、誰が勝ったかを判断することができます。さらに勝者を ステータス表示部分に"Winner: [X/O]"と表示するために次のように変更を加えます。

Replace the status declaration in Board's render with this code:

Board コンポーネントの render 内の status 部分を、次のようにします。

  render() {
    const winner = calculateWinner(this.state.squares);
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      // the rest has not changed
You can now change handleClick in Board to return early and ignore the click if someone has already won the game or if a square is already filled:

さらに Board コンポーネント内の handleClick に変更を加えて、既に勝者が決まっていたり、もしくは既にクリックしたマス目が埋まっていた場合に、return を返して処理を無視するようにします。

  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }
Congratulations! You now have a working tic-tac-toe game. And now you know the basics of React. So you're probably the real winner here.

おめでとうございます！あなたは、三目並べを作るワークショップに勝利しました。そして React の基礎を身につけることができました。ある意味で真の勝者です。

View the current code.

Storing a History

履歴を表示する

Let's make it possible to revisit old states of the board so we can see what it looked like after any of the previous moves. We're already creating a new squares array each time a move is made, which means we can easily store the past board states simultaneously.

ボード上で繰り広げられる戦いの、過去の状態に戻ることが出来るように機能を追加してみましょう。つまり、過去のある手を打った後に、盤面がどのような状態なのかを確認できるようにする機能です。私達のコードにおいては既に、手を打つ度に新しい squares という配列を作るようにしていますから、過去の盤上の状態を全て保存するのは容易にできるはずです。

Let's plan to store an object like this in state:

次のような形で状態を保持するオブジェクトを作っていきます。

history = [
  {
    squares: [
      null, null, null,
      null, null, null,
      null, null, null,
    ]
  },
  {
    squares: [
      null, null, null,
      null, 'X', null,
      null, null, null,
    ]
  },
  // ...
]
We'll want the top-level Game component to be responsible for displaying the list of moves. So just as we pulled the state up before from Square into Board, let's now pull it up again from Board into Game – so that we have all the information we need at the top level.

最上階層にある Game コンポーネントに、打ち手のリストを表示する機能を実装することにしましょう。そのために、先程 Square コンポーネントから Board コンポーネントへ状態を保持する場所を引き上げたように、今回は Board コンポーネントから Game コンポーネントへと状態を保持する場所を引き上げます。つまり、全ての必要な情報を、最上階層が持つようにするということです。

First, set up the initial state for Game by adding a constructor to it:

まずは Game コンポーネントにコンストラクターを追加して、初期状態を設定します。

class Game extends React.Component {
  constructor() {
    super();
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      xIsNext: true,
    };
  }

  render() {
    return (
      <div className="game">
        <div className="game-board">
          <Board />
        </div>
        <div className="game-info">
          <div>{/* status */}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
}
Then change Board so that it takes squares via props and has its own onClick prop specified by Game, like the transformation we made for Square earlier. You can pass the location of each square into the click handler so that we still know which square was clicked. Here is a list of steps you need to do:

次に Board コンポーネントを変更していきます。まずは Board コンポーネントが props を介して Game コンポーネントから squares を(訳注：状態の中のhistoryの中にあるsquares) 受け取れるようにします。また Board コンポーネントが onClick というこれまた Game コンポーネント内で設定された関数を、prop 経由で受け取れるようにします。(訳注：Game コンポーネントの中で) それぞれ何番目のマス目なのかを特定できる情報を、click ハンドラーに渡す予定です。そうすることで、どのマス目がクリックされたかがわかるようになります。

次のリストは、上記の作業をまとめたものです。一つ一つ作業していってください。

Delete the constructor in Board.
Borad コンポーネント内のコンストラクターを削除する
Replace this.state.squares[i] with this.props.squares[i] in Board's renderSquare.
this.state.squares[i] を変更し、 this.props.squares[i] へ置き換える。これは Board コンポーネント内の renderSquare にある。
Replace this.handleClick(i) with this.props.onClick(i) in Board's renderSquare.
this.handleClick(i) を変更し、this.props.onClick(i) へと置き換える。これも同じく Board コンポーネント内の renderSquare にある。
Now the whole Board component looks like this:

この作業を終えると、Board コンポーネントは以下のようになっているはずです。

class Board extends React.Component {
  handleClick(i) {
    const squares = this.state.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      squares: squares,
      xIsNext: !this.state.xIsNext,
    });
  }

  renderSquare(i) {
    return (
      <Square
        value={this.props.squares[i]}
        onClick={() => this.props.onClick(i)}
      />
    );
  }

  render() {
    const winner = calculateWinner(this.state.squares);
    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div>
        <div className="status">{status}</div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
}
Game's render should look at the most recent history entry and can take over calculating the game status:

Game コンポーネントの render 内で、直近の履歴をチェックして、ゲームの勝者を判定する機能 (訳注：原文に正確には状態を判定する機能) を持つべきですので、次のように変更します。

  render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />
        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{/* TODO */}</ol>
        </div>
      </div>
    );
  }
Since Game is now rendering the status, we can delete <div className="status">{status}</div> and the code calculating the status from the Board's render function:

Game コンポーネントが状態をレンダリングする機能を持ったので (訳注：次に誰がプレイする番か、誰が勝ったかを表示するエリア) 、Board コンポーネントの render 内から、<div className="status">{status}</div> を削除し、判定機能も削除します。

  render() {
    return (
      <div>
        <div className="board-row">
          {this.renderSquare(0)}
          {this.renderSquare(1)}
          {this.renderSquare(2)}
        </div>
        <div className="board-row">
          {this.renderSquare(3)}
          {this.renderSquare(4)}
          {this.renderSquare(5)}
        </div>
        <div className="board-row">
          {this.renderSquare(6)}
          {this.renderSquare(7)}
          {this.renderSquare(8)}
        </div>
      </div>
    );
  }
Next, we need to move the handleClick method implementation from Board to Game. You can cut it from the Board class, and paste it into the Game class.

次に handleClick メソッドの実装箇所を、Board コンポーネントから Game コンポーネントへと移し替えます。Board クラスからその箇所をカットして、Game クラスへとペーストしてください。

We also need to change it a little, since Game state is structured differently. Game's handleClick can push a new entry onto the stack by concatenating the new history entry to make a new history array.

単にカット・アンド・ペーストしただけではだめで、もう少し変更が必要です。というのも、Game コンポーネントで設定した状態は、Board コンポーネントが持っていたものとは少し違うからです。Game コンポーネント内の handleClick メソッドを変更して、新しく状態の値が生まれた際に、それを既存の状態に対して積み重ねて保存するようにします。つまり、新しい history を古い history へと連結させ、新しい history 配列を作り出します。(訳注：history: history.concat([{squares: squares,}])この部分ですね。)

  handleClick(i) {
    const history = this.state.history;
    const current = history[history.length - 1];
    const squares = current.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      history: history.concat([{
        squares: squares,
      }]),
      xIsNext: !this.state.xIsNext,
    });
  }
At this point, Board only needs renderSquare and render; the state initialization and click handler should both live in Game.

この時点で、Board には renderSquare and renderしかありません。つまり状態の初期化とクリックハンドラーは、どちらもGameの中にあります。

View the current code.

Showing the Moves

手を表示する

Let's show the previous moves made in the game so far. We learned earlier that React elements are first-class JS objects and we can store them or pass them around. To render multiple items in React, we pass an array of React elements. The most common way to build that array is to map over your array of data. Let's do that in the render method of Game:

では先程 Game コンポーネント内で作成した moves = 手(訳注：つまり盤上の状態の変遷) を表示してみましょう。React エレメンが非常に素晴らしい JS オブジェクトであることは既に皆さんご理解いただけたと思うのですが、更に今回は React エレメントを保持して、他の場所へと渡す、という方法をご紹介します。React において複数の項目をレンダリングする場合には、単に React エレメントの配列を渡すだけでいいのです。そのような配列を作る一般的に取られる手法は、map メソッドを用いて、配列のデータを処理するものです。(訳注：Array.prototype.map() メソッドについてはこちらを参照) Game コンポーネントの render メソッド内でこれを実行しましょう。

  render() {
    const history = this.state.history;
    const current = history[history.length - 1];
    const winner = calculateWinner(current.squares);

    const moves = history.map((step, move) => {
      const desc = move ?
        'Move #' + move :
        'Game start';
      return (
        <li>
          <a href="#" onClick={() => this.jumpTo(move)}>{desc}</a>
        </li>
      );
    });

    let status;
    if (winner) {
      status = 'Winner: ' + winner;
    } else {
      status = 'Next player: ' + (this.state.xIsNext ? 'X' : 'O');
    }

    return (
      <div className="game">
        <div className="game-board">
          <Board
            squares={current.squares}
            onClick={(i) => this.handleClick(i)}
          />
        </div>
        <div className="game-info">
          <div>{status}</div>
          <ol>{moves}</ol>
        </div>
      </div>
    );
  }
View the current code.

For each step in the history, we create a list item <li> with a link <a> inside it that goes nowhere (href="#") but has a click handler which we'll implement shortly. With this code, you should see a list of the moves that have been made in the game, along with a warning that says:

history の中の各ステップおいて (訳注：つまり、historyには全ての手が入っているわけですが、その各回において) 、それぞれ<li>要素を作成します。その中にはどこにも移動しない<a>リンク(href="#"なので) を入れます。その代わりに後ほど実装するクリックハンドラーを持たせておきます。ここまでコードを書くと、move のリストが Game コンポーネント内に表示されるはずです。ただし、次のような警告も出ているはずです。

Warning: Each child in an array or iterator should have a unique "key" prop. Check the render method of "Game".

警告：配列やイテレーター内の各要素は、それぞれ異なる"key" prop を持つ必要があります。Game コンポーネント内の render メソッドを確認してください。

(訳注：英辞郎より引用：イテレーター、反復子◆複数の要素の集まりと見なせる対象（配列・リストなど）で、その各要素に順次アクセスするための変数や言語機能。)

Let's talk about what that warning means.

ではこの警告が何を意味しているのか、お話しましょう。

Keys

When you render a list of items, React always stores some info about each item in the list. If you render a component that has state, that state needs to be stored – and regardless of how you implement your components, React stores a reference to the backing native views.

(訳注：このセンテンス、抽象的すぎて、よくわからない。)

あなたが複数のアイテムが含まれたリストをレンダリングする際には、React は常にそれぞれのアイテムの情報を保持しています。状態をもったコンポーネントをレンダリングする際には、その状態は保持されなくてはいけません。そして、どのようにあなたがコンポーネントを実装したとしても、React は backing native views への参照を保持しています。

When you update that list, React needs to determine what has changed. You could've added, removed, rearranged, or updated items in the list.

あなたがリストを更新した際に、React は何が変更されたのかを判断しなくてはいけません。追加、削除、順番を変える、アイテムを更新する。一体どの操作をしたのかを判断する必要があります。

Imagine transitioning from

ある偏移について考えてみましょう。この状態から、

<li>Alexa: 7 tasks left</li>
<li>Ben: 5 tasks left</li>
to

以下のような状態へ推移するとしましょう。

<li>Ben: 9 tasks left</li>
<li>Claudia: 8 tasks left</li>
<li>Alexa: 5 tasks left</li>
To a human eye, it looks likely that Alexa and Ben swapped places and Claudia was added – but React is just a computer program and doesn't know what you intended it to do. As a result, React asks you to specify a key property on each element in a list, a string to differentiate each component from its siblings. In this case, alexa, ben, claudia might be sensible keys; if the items correspond to objects in a database, the database ID is usually a good choice:

人間がこれを見た場合には、Alexa と Ben が席を変えて、さらに Claudia が追加されたのだろうと、考えることでしょう。でも React は単なるコンピューターのプログラムですから、あなたがどう意図しているのかなんていうことはわかりません。結果として、React はあなたに、リスト内のそれぞれの要素に対して "key"  プロパティを付けるよう要求します。これを用いて、兄弟要素内の識別を行うのです。 このケースの場合であれば、 alexa, ben, claudia を key に用いるのがふさわしいでしょう。その他のケース、例えばデータベースを用いていて、データベースに記録されているオブジェクトと、React の中で使われる各項目が一致しているのであれば、データベース内の各項目の ID を用いるのも、常に良い選択肢です。

<li key={user.id}>{user.name}: {user.taskCount} tasks left</li>
key is a special property that's reserved by React (along with ref, a more advanced feature). When an element is created, React pulls off the key property and stores the key directly on the returned element. Even though it may look like it is part of props, it cannot be referenced with this.props.key. React uses the key automatically while deciding which children to update; there is no way for a component to inquire about its own key.

React において "key" は特別なプロパティで、予約語となっています。(他にも予約後になっているものとして ref などがあります。これはより高度な機能ですが) element が生成される時に、React は key プロパティを取り出して、その key をreturn で返される element の中に埋め込みます。key は props の一部のように見えますが、this.props.key で参照することはできません。React は特に設定をしなくても、どの要素を更新すべきなのかを判断するために、 key を用います。ただし、コンポーネント自身が自分のキーを問い合わせる方法は存在しません。

When a list is rerendered, React takes each element in the new version and looks for one with a matching key in the previous list. When a key is added to the set, a component is created; when a key is removed, a component is destroyed. Keys tell React about the identity of each component, so that it can maintain the state across rerenders. If you change the key of a component, it will be completely destroyed and recreated with a new state.

再レンダリングの際に React がおこなっていることを説明しましょう。React は新しいリストを取り込むと、それと一つ前のリストとを比較して、リストの中の各要素につき、一致するものを見つけようとします。新しい key が追加されていれば、新しいコンポーネントを作成します。反対に、取り除かれた key があれば、その key を持っていたコンポーネントは破壊されます。Key を用いて React は、それぞれのコンポーネントの同一性を把握しており、その結果として レンダリング前後で state を保持することができるのです。もしコンポーネントが持つ key を変更してしまうと、そのコンポーネントは完全に破壊され、新しい状態をもった別のコンポーネントが生成されます。

It's strongly recommended that you assign proper keys whenever you build dynamic lists.If you don't have an appropriate key handy, you may want to consider restructuring your data so that you do.

これは非常に大切なことですが、動的に生成されるリストにおいても、適切な key を与えるようにしてください。もし適切な key をうまく与えれない場合には、そもそもデーター構造を見直す必要があります。

If you don't specify any key, React will warn you and fall back to using the array index as a key – which is not the correct choice if you ever reorder elements in the list or add/remove items anywhere but the bottom of the list. Explicitly passing key={i} silences the warning but has the same problem so isn't recommended in most cases.

Key を与えなかった場合、React はあなたに警告を出し、仕方なく配列のインデックスをkeyとして用います。これは適切な方法ではないので、要素の順番を変える場合や、要素の最下部以外に要素を追加したり削除したりする場合に、問題が発生します。明示的に key={i} をわたすことで警告はなくなりますが、しかし問題が解決されたわけではありませんので、この方法は推奨できません。

Component keys don't need to be globally unique, only unique relative to the immediate siblings.

コンポーネントに与える key は、グローバル環境においてユニークである必要はなく、単に特定の空間の兄弟要素内でユニークになるようにしてください。

Implementing Time Travel

タイムトラベルを実装する

For our move list, we already have a unique ID for each step: the number of the move when it happened. In the Game's render method, add the key as <li key={move}> and the key warning should disappear:

さて、私達が作成したリストはしっかりと、ユニークなIDをそれぞれのステップが持っています。その手が打たれた時の番号がIDとして使われていますので。ですので次は、Game コンポーネントの render メソッド内に、key を追加した <li key={move}> を加えましょう。そうすれば警告は消えるはずです。

    const moves = history.map((step, move) => {
      const desc = move ?
        'Move #' + move :
        'Game start';
      return (
        <li key={move}>
          <a href="#" onClick={() => this.jumpTo(move)}>{desc}</a>
        </li>
      );
    });
View the current code.

Clicking any of the move links throws an error because jumpTo is undefined. Let's add a new key to Game's state to indicate which step we're currently viewing.

move リストのリンクをクリックすると、エラーが出てしまいます。何故なら  jumpTo メソッドが定義されていないからです。では Game コンポーネントの state に新しい項目を追加して、どのステップを今我々が見ようとしているかを判断するために用いましょう。

First, add stepNumber: 0 to the initial state in Game's constructor:

まず、Game コンストラクターの中で、stepNumber: 0 という初期状態を与えます。

class Game extends React.Component {
  constructor() {
    super();
    this.state = {
      history: [{
        squares: Array(9).fill(null),
      }],
      stepNumber: 0,
      xIsNext: true,
    };
  }
Next, we'll define the jumpTo method in Game to update that state. We also want to update xIsNext. We set xIsNext to true if the index of the move number is an even number.

次に、jumpTo メソッドを Game コンポーネントの中で定義して、このメソッドによって状態を更新することにしましょう。その際に xIsNext も変更することにします。xIsNext を、move number が偶数の場合には、true にします。

Add a method called jumpTo to the Game class:

では jumpTo メソッドを Game クラスに追加しましょう。

  handleClick(i) {
    // this method has not changed
  }

  jumpTo(step) {
    this.setState({
      stepNumber: step,
      xIsNext: (step % 2) === 0,
    });
  }

  render() {
    // this method has not changed
  }
Then update stepNumber when a new move is made by adding stepNumber: history.length to the state update in Game's handleClick:

新しい手が打たれた時に、stepNumber を更新するようにしましょう。Gameコンポーネントの handleClick内で状態を変更するために、 stepNumber: history.length を加えます。

  handleClick(i) {
    const history = this.state.history.slice(0, this.state.stepNumber + 1);
    const current = history[history.length - 1];
    const squares = current.squares.slice();
    if (calculateWinner(squares) || squares[i]) {
      return;
    }
    squares[i] = this.state.xIsNext ? 'X' : 'O';
    this.setState({
      history: history.concat([{
        squares: squares
      }]),
      stepNumber: history.length,
      xIsNext: !this.state.xIsNext,
    });
  }
Now you can modify Game's render to read from that step in the history:

さらに Game コンポーネントの render メソッドを変更することで、history 内のstep を読み取るようにします。

  render() {
    const history = this.state.history;
    const current = history[this.state.stepNumber];
    const winner = calculateWinner(current.squares);

    // the rest has not changed
View the current code.

If you click any move link now, the board should immediately update to show what the game looked like at that time.

ここまでの作業を終えると、move リンクをクリックしたときに、盤上の状態が瞬時に変化して、その手が打たれた瞬間の状態へと更新されます。

You may also want to update handleClick to be aware of stepNumber when reading the current board state so that you can go back in time then click in the board to create a new entry. (Hint: It's easiest to .slice() off the extra elements from history at the very top of handleClick.)

!!何言ってるのかわからないので飛ばす

Wrapping Up

まとめ

Now, you've made a tic-tac-toe game that:

さて、三目並べゲームを以下のような手順をおって作成してきました。

lets you play tic-tac-toe,
三目並べゲームがプレイできるようにし、
indicates when one player has won the game,
どちらかのプレイヤーが勝利した場合にそれを表示できるようにし、
stores the history of moves during the game,
ゲーム中の全ての手を履歴として保持するようにし、
allows players to jump back in time to see older versions of the game board.
プレイヤーに過去の盤上の状態に戻れるようにしました。
Nice work! We hope you now feel like you have a decent grasp on how React works.

お疲れ様でした！React がどのように機能するのか、かなり理解できたのではないでしょうか。

Check out the final result here: Final Result.

最終的な結果は次のようになります。

If you have extra time or want to practice your new skills, here are some ideas for improvements you could make, listed in order of increasing difficulty:

時間に余裕があり、さらに新しい技術を身に着けたいのであれば、次のような実装をおこなってみるのはどうでしょうか。このリストは簡単なものから難しいものへと順番に並んでいます。

(!!見ればわかるので訳さない)

Display the move locations in the format "(1, 3)" instead of "6".
Bold the currently-selected item in the move list.
Rewrite Board to use two loops to make the squares instead of hardcoding them.
Add a toggle button that lets you sort the moves in either ascending or descending order.
When someone wins, highlight the three squares that caused the win.
Throughout this tutorial, we have touched on a number of React concepts including elements, components, props, and state. For a more in-depth explanation for each of these topics, check out the rest of the documentation. To learn more about defining components, check out the React.Component API reference.

このチュートリアルを通して、React のコンセプトに触れてきました。element, component, props, state などです。より各項目について知識を深めるためには、ドキュメントを参照してください。コンポーネントの定義についてより学びたい場合には、React.Component API reference を参照してください。

