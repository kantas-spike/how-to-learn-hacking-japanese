# ハッキングの学び方(How To Learn Hacking)

Eric Steven Raymond
[Thyrsus Enterprises](http://catb.org/~esr/)

<esr@thyrsus.com>

Copyright 2014 Eric S. Raymond

---

|Revision History|    |   |
|:---------------|:--:|:--:|
|Revision 1.2    | 2014-11-30| esr |
|New section on being original.| | |
|Revision 1.1    | 2014-11-23 | esr |
| Incorporated feedback from G+, including good suggestions by Peter da Silva and John D. Bell.| | |
|Revision 1.0 | 2014-11-21 | esr |
| Initial version | | |

---

<!--
## Table of Contents
- [What is Hacking?](#what-is-hacking)
- [Stages of Learning How To Hack](#stages-of-learning-how-to-hack)
- [The Incremental-Hacking Cycle](#the-incremental-hacking-cycle)
- [Developing Your Design Sense](#developing-your-design-sense)
- [Being original](#being-original)
 -->

目次
- [ハッキングの学び方(How To Learn Hacking)](#ハッキングの学び方how-to-learn-hacking)
  - [ハッキングって何ですか?](#ハッキングって何ですか)
  - [ハッキングの学習段階](#ハッキングの学習段階)
  - [インクリメンタル ハッキングサイクル](#インクリメンタル-ハッキングサイクル)
  - [デザインセンスを磨く](#デザインセンスを磨く)
  - [独創的であること](#独創的であること)

<!--
## What is Hacking?
 -->
## ハッキングって何ですか?

<!--
The “hacking” we'll be talking about in this document is exploratory programming in an open-source environment.
If you think “hacking” has anything to do with computer crime or security breaking and came here to learn that, you can go away now. There's nothing for you here.
 -->
この文書で話題にする「ハッキング」は、オープンソース環境での探索的プログラミングのことです。
もし、「ハッキング」をコンピュータ犯罪やセキュリティ破りと関係があると思って、ここに学びに来たのなら、もう帰っていいです。ここに、あなたが望むものはありません。

<!--
Translations of this document are available in: Hungarian
 -->
この文書の翻訳は、ハンガリー語版が利用できます。

<!--
Hacking is primarily[1] a style of programming, and following the recommendations in this document can be an effective way to acquire general-purpose programming skills.
This path is not guaranteed to work for everybody;
 it appears to work best for those who start with an above-average talent for programming and a fair degree of mental flexibility.
 People who successfully learn this style tend to become generalists with skills that are not strongly tied to a particular application domain or language.
 -->
ハッキングは、本来 [^1] 、プログラミングスタイルのことです。
この文書の推奨事項に従うことは、汎用的なプログラミングスキルを習得する効果的な方法になります。
この方法は全ての人に有効であると保証するものではありません。
プログラミングの才能が平均以上で、精神的にかなり柔軟な人に向いているようです。
このスタイルを上手く習得する人は、特定の応用分野や言語に決して限定されないスキルを持つゼネラリストになる傾向があります。

<!--
Note that one can be doing hacking without being a hacker.
 “Hacking”, broadly speaking, is a description of a method and style;
 “hacker” implies that you hack, and are also attached to a particular culture or historical tradition that uses this method.
 Properly, “hacker” is an honorific bestowed by other hackers.
 -->
 ハッカーにならなくても、ハッキングをすることは可能です。
「ハッキング」とは、広い意味で、方法やスタイルを表す言葉です。
「ハッカー」は、ハッキングすること、そして、[ハッキングの文化](http://catb.org/~esr/faqs/hacker-howto.html)や歴史的伝統に愛着があること、を意味します。
正しくは、「ハッカー」は他のハッカーたちから贈られる敬称です。

<!--
Hacking doesn't have enough formal apparatus to be a full-fledged methodology in the way the term is used in software engineering, but it does have some characteristics that tend to set it apart from other styles of programming.
 -->
ハッキングは、ソフトウェア工学で使われるような本格的な方法論と言えるほど、十分に組織化されていませんが、他のプログラミングスタイルとは異なる、いくつかの特徴を持っています。

<!--
- Hacking is done on open source. Today, hacking skills are the individual micro-level of what is called “open source development” at the social macro-level. [2] A programmer working in the hacking style expects and readily uses peer review of source code by others to supplement and amplify his or her individual ability.
 -->
 - ハッキングはオープンソースで行われます。
   今日では、ハッキングスキルは、社会的にマクロなレベルで「オープンソース開発」と呼ばれるものを、個人的でミクロなレベルにしたものです。[^2] ハッキングスタイルで働くプログラマは、自分自身の能力を補完し増幅させるために、他の人にソースコードのピアレビューを求め、進んで実施します。

<!--
- Hacking is lightweight and exploratory. Rigid procedures and elaborate a-priori specifications have no place in hacking; instead, the tendency is try-it-and-find-out with a rapid release tempo.
-->
- ハッキングは、軽量で探索的です。厳格な手順と、精巧で演繹的な仕様には、ハッキングの余地がありません。その代りに、ハッキングで好まれるのは、早いリリーステンポで「実行と理解」を繰り返すことです。

<!--
- Hacking places a high value on modularity and reuse. In the hacking style, you try hard never to write a piece of code that can only be used once. You bias towards making general tools or libraries that can be specialized into what you want by freezing some arguments/variables or supplying a context.
 -->
- ハッキングでは部品化と再利用を重要視します。
  ハッキングスタイルでは、一度しか使わないコードも書かないように努力します。
  引数や変数、コンテキストを埋め込んで自分専用にしたツールやライブラリを作ることに偏見を持っています。

<!--
- Hacking favors scrap-and-rebuild over patch-and-extend.
  An essential part of hacking is ruthlessly throwing away code that has become overcomplicated or crufty, no matter how much time you have invested in it.
 -->
- ハッキングは微修正と機能追加よりも、破棄と再作成を好みます。
  ハッキングの本質は、どんなに時間をかけて作ったものでも、複雑になりすぎたり、陳腐化したコードは冷酷に捨てることです。

<!--
The hacking style has been closely associated with the technical tradition of the Unix operating system[3]
 -->
 ハッキングスタイルは、UNIXオペレーティングシステムの技術的伝統と密接に関係しています。[^3]

 <!--
 Recently it has become evident that hacking blends well with the “agile programming” style. Agile techniques such as pair programming and feature stories adapt readily to hacking and vice-versa. In part this is because the early thought leaders of agile were influenced by the open source community. But there has since been traffic in the other direction as well, with open-source projects increasingly adopting techniques such as test-driven development. -->
 最近では、ハッキングは「アジャイルプログラミング」というスタイルに、上手く調和することがわかってきました。
ペアプログラミングやフィーチャーストーリーのようなアジャイル技術は、ハッキングに容易に適応しました。その逆もまた然りです。
これは、アジャイルの初期の思想的リーダーがオープンソースコミュニティーの影響を受けていたことも一因です。
しかし、その後、オープンソースプログラミングがテスト駆動開発のような手法を採用するようになり、別方向への動きも見られるようになりました。

<!--
## Stages of Learning How To Hack
 -->
## ハッキングの学習段階

<!--
Learning to compose music has three stages.
First, you have to learn the basic mechanical technique of an instrument — fingering and how to play scales.
Then you have to train your ear to understand musical patterns.
Finally, you must learn how to recombine musical patterns into original creations. Hacking is similar.
 -->
作曲を学ぶには3つの段階があります。
まず、楽器の基本的で機械的な技術、つまり指使いや音階の弾き方を学ぶ必要があります。
次に、音楽のパターンを理解するために、耳を訓練する必要があります。
最後に、音楽のパターンを組み合せてオリジナルの作品を作る方法を学びます。
ハッキングも同じです。

<!--
The hacking equivalent of fingering is learning the capabilities of programming languages, and the mechanics of using tools like editors, interpreters, and compilers.
(If you don't understand these terms, see The Unix and Internet Fundamentals HOWTO.)
We won't cover those mechanics here as they vary too much according to what language you're using.
Tutorials for all the languages you might want to use are available on the Web; use a search engine.
 -->
「楽器の指使いの学習」は、ハッキングでは、プログラミング言語の機能や、エディタ、インタプリターや、コンパイラなどのツールの使い方を学ぶことに相当します。
(もし、これらの用語を知らないのなら、「[ザ UNIXアンドインターネットファンダメンタルズハウツー](https://tldp.org/HOWTO/Unix-and-Internet-Fundamentals-HOWTO/index.html)」を参照してください。)

使用する言語によって大きく異なるので、これらの仕組みはここでは説明しません。
あなたが使いたいと思う言語のチュートリアルはウェブ上で利用できます。検索してください。

<!--
The equivalent of playing scales is writing small programs, alone. Unfortunately, playing scales (a) doesn't teach you anything about music, and (b) is boring as hell. Similarly, writing toy programs doesn't tend to teach you much about hacking, and (b) will tend to de-motivate you unless the program immediately solves a problem you care about.
 -->
「音階を弾くこと」は、一人で小さなプログラムを書くことに相当します。
残念ながら、「音階を弾くこと」は (a) 音楽について何も教えてくれませんし、(b) 地獄のように退屈です。
同様に、おもちゃのプログラムを書いても、(a) ハッキングの勉強にならないし、(b) そのプログラムが、自分が関心のある問題をすぐに解決しない限り、やる気をなくしがちです。

<!--
Most formal programming instruction gets to playing scales and stops. Thus, it tends to produce coders who are poor at collaborating with each other and have the equivalent of no ear for music — a poor feel for software design and architecture.
 -->
公式なプログラミング教育では、「音階の演奏と停止」をすることがほとんどです。
そのため、お互いに協力することが苦手で、ソフトウェアの設計やアーキテクチャに対する感覚が乏しい、コーダーが生まれる傾向があります。これは「音楽を聞く耳がない」に相当します。

<!--
## The Incremental-Hacking Cycle
 -->
## インクリメンタル ハッキングサイクル

<!--
There is a better way to learn. I call it the incremental-hacking cycle.
 -->
より良い学習方法があります。私はこれを、インクリメンタル ハッキングサイクルと呼んでいます。

<!--
1. First, pick a program that does something you are interested in. Ideally, it should be a program you use regularly and have opinions about. The next best thing is a program you don't normally use, but that does something you think is interesting. For this learning method to work, you should avoid trying to hack on code that bores you.

The program you choose doesn't have to do anything serious. Many programmers have honed their skills by improving games that they enjoyed. The only drawback to this is that modern games are often quite large and complicated, and may be beyond the grasp of a raw beginner.
 For this reason, you may want to investigate one of the classic text-oriented games that still survive; nethack is a prime example, and there are many others.

 -->
1. 最初に、あなたが興味のある機能を持つプログラムを選びます。理想的には、あなたが普段から使い、意見を持つプログラムです。そうでなければ、普段は使っていないけれど、興味のある機能を持つプログラムです。この学習方法を成功させるためには、退屈なコードをハックしようとするのは避けるべきです。

   選ぶプログラムは本格的なものである必要はないです。多くのプログラマは、自分が楽しんだゲームを改良することで技術を磨いてきました。唯一の欠点は、最近のゲームはかなり大規模で複雑なものが多く、本当の初心者には手に負えないかもしれないです。
   そのため、今でも生き残っているクラシックなテキスト指向のゲームについて調べるのもよいでしょう。「ネットハック」はその代表例ですし、ほかにも沢山あります。

<!--
2. If you don't already know the program, learn how to use it. Read the documentation. Develop a mental model of how it works.
 -->
2. まだそのプログラムを知らないなら、そのプログラムの使い方を学びましょう。ドキュメントを読みましょう。どのように動作するかのメンタルモデルをつくりましょう。

<!--
3. Pick a small feature to change or add.
 -->
3. 変更したり追加する、小さな機能を選びましょう。

<!--
4. Search the code until you find the part you need to modify.
   Note: you should specifically not try to read the entire program. You will just exhaust and frustrate yourself if you do that. Instead, use the module structure of the code to zero in on just the part you need to understand. Along the way, you will learn things about how the whole program fits together.

   It's a good exercise to add explanatory comments and notes to the code as you figure out things about it. This will help your memory, and will help you organize your thoughts as well.
 -->
4. 変更すべき場所が見つかるまで、コードを探しましょう。

   注意: プログラム全体を読もうとしないことです。そんなことをしても、疲弊し、挫折するだけです。その代わりに、コードのモジュールを使って、理解する必要のある部分にだけに集中しましょう。その過程で、プログラム全体がどのように組み合さっているのか、いろいろ学ぶことができます。
   コードについていろいろなことが分かってきたら、説明のコメントやメモを書き加えることは良い練習になります。これはあなたの記憶を助け、考えの整理にも役立ちます。

<!--
5. Make, test, debug, and document your change.
   Documenting your change is important. If you develop the habit of doing this early, you'll produce much higher-quality work.
 -->

5. コードを変更し、テストし、デバッグし、変更内容を文書化しましょう

   変更の文書化は重要です。もし、早くからこの習慣を身につけることで、より質の高い仕事ができるようになるでしょう。

<!--
1. Send your change as a patch to the program maintainers. See the Software Release Practice HOWTO for tips on how to do this in an effective and polite way.
  I originally described this as an optional step; a wise friend pointed out that probably I shouldn't have. Solitary noodling on your instrument is all very well for practice, but music is completed and validated when the creativity in it is heard by other people. Solitary noodling on your computer is similarly good for practice, but hacking is completed when other people use what you wrote. That real-world test is important.
  Sometimes (oftener when you are just starting) your patches will be rejected. You need to learn to cope with this. It doesn't mean you're doomed to fail in your quest; usually what it does mean is that you have not read the code carefully enough, or (just as usually) you have missed something important aboout the culture and practices of the developmemt group you are trying to contribute to. These mistakes can be repaired.
 -->
6. あなたの変更をパッチとしてプログラムのメンテナに送付してください。これを効果的で丁寧に行うための助言については、「[ソフトウェアリリースプラクティスハウツー](https://tldp.org/HOWTO/Software-Release-Practice-HOWTO/index.html)」を参照してください。

   私は当初、このステップをオプションとして説明しましたが、賢明な友人からオプションにするべきではないと指摘されました。練習のために楽器を一人で演奏することはとても良いことです。しかし、音楽は、その創造性を他の人に聴いてもらうことで完成し、評価されるものなのです。
   コンピュータで一人でプログラミングすることも、同じように良い練習になります。しかし、ハッキングは自分の書いたものを他の人が使って初めて完成します。その現実世界で試されることが大切です。
   時には、(初めたばかりの頃はよくあることですが)、あなたのパッチが拒否されることもあります。これに対処することを学ぶ必要があります。
   それは、あなたの探求の旅が失敗の運命にあることを意味するのではありません。
   大抵の場合、コードを十分に注意深く読んでいなかったり、あなたが貢献しようとしている開発グループの文化や慣習について何か重要なことを見逃していたりすることを意味します。
   このような間違いは、修正可能です。

<!--
7. Now, ask yourself: do I understand this entire program?

   If yes, you're done. If no, go back to step 3. This time, pick a different and perhaps slightly more difficult thing to change.
 -->
7. さあ、自問してください。私はこのプログラム全体を理解できていますか?

   もし、Yesなら、ハッキングサイクルは完了です。もし、Noならステップ3に戻りましょう。今度は、別の、少し難しそうな、変更したい機能を選びましょう。

<!--
The point of this exercise is to learn how to sneak up on the problem of understanding a program, rather than trying to tackle all of the complexity at once. As you go through this loop several times, you will gradually develop a more complete representation in your mind of the way the whole program fits together. At some point you will reach a threshold where you understand it all — or anyway enough of it for whatever your final purpose is.
 -->
 この訓練のポイントは、複雑なプログラムに、全て一度に取り組もうとするのではなく、プログラムを理解するという課題にそっと近づく方法を学ぶことです。
このループを何度か繰り返すうちに、プログラム全体がどのように組み合わされているのか、徐々に頭の中で完全に描くことができるようになります。
ある時点で、全てを理解する領域に到達します。とにかく、あなたの最終目的がなんであれ、それで十分です。

<!--
## Developing Your Design Sense
 -->
## デザインセンスを磨く
<!--
To train yourself, start small. If possible, first do the incremental-hacking cycle as an exercise on very small programs or scripts, 10-50 lines. These may be hard to find, as most programs of any use are larger than this. Most programs this small are scripts in shell, Perl, Python, or Tcl; that's a trait to look for when trawling the Web for them.
 -->
自分を鍛えるためには、まずは小さなことから初めること。
可能であれば、まず、10〜50行程度のとても小さなプログラムやスクリプトで、インクリメンタルハッキングサイクルを訓練として実施してください。
ほとんどの実用的なプログラムはこれより大きいので、これらを見付けるのが難しいかもしれません。
このような小さなプログラムのほとんどは、シェルや、Perl、Python、またはTclによるスクリプトです。これは、小さなプログラムをWebで検索するときに、調べるべき特徴です。

<!--
When you have done the incremental-hacking cycle on several very small programs (or if you are unlucky enough to not find any suitable very small ones), try it on slightly larger programs. Look for codebases in the range of 100-500 lines.
 -->

いくつかの、とても小さなプログラムで、インクリメンタルハッキングサイクルを実行したら、(あるいは、運悪く適当な小さなプログラムを見つけられなかったら)、少し大きなプログラムに対して、サイクルを実施してください。100〜500行程度のコードベースを探してみてください。

<!--
When you master that level, go to the order of magnitude, 1000-5000 lines. By the time you master the 1K-5K level, you will have entered the bottom end of the capability range of what is usually considered a skilled programmer.
 -->
そのレベルをマスターしたら、次は1000〜5000行という桁違いのレベルに進みます。
1000〜5000行のレベルをマスターする頃には、熟練のプログラマと呼ばれる人の能力の末端レベルに、あなたの能力は到達しているでしょう。

<!--
At or before the 1K-5K level, you should occasionally begin to notice that you are having itches to change the structure or organization of a program, not just its features. You may find yourself thinking “This code is ugly” and having feelings about making it prettier and cleaner.
 -->
1000〜5000行のレベルでは、プログラムの機能だけでなく、構造や構成を変更したくなることがあるはずです。「このコードは醜い」と思い、もっと美しく、もっとクリーンにしたいという気持ちになることがあります。

<!--
When this happens, pay attention. This is your design sense trying to wake up.
Don't rush to patch in another feature. Instead, start to explore the program that gives you this itch at a higher level.
Now might be a good time to try to read all the code, but don't be too concerned if you can't;
most programs are just too big and messy for gulping them down all at once to work. Just try to get a grip on what you need to know to clean things up.
 -->
そんな時は、注意してください。これは、あなたのデザインセンスが目覚めようとしているのです。
慌てて、別の機能を追加する必要はありません。より高いレベルの変更が必要な、このプログラムの探索を開始しましょう。
今こそ、すべてのコードを読もうとする良い機会かもしれません。しかし、読めなくても、あまり気にしないでください。
ほとんどのプログラムは、一度に理解するには、あまりにも大きく、厄介なものです。
ただ、コードをクリーンにするために知っておく必要のあることを把握するように努力してください。

<!--
You are now entering the intermediate portion of learning to hack. This involves not merely changing surface-visible features but doing what is called “refactoring” — reorganizing the code internally so that it is cleaner and has better architecture (better hiding of data, narrower interfaces between different parts, more functional separation among modules).
 -->
あなたは今、ハッキング学習の中級編に突入しています。
これは、単に表面的な機能を変更するだけでなく、「リファクタリング」を実施しています。「リファクタリング」は、より綺麗に、より良いアーキテクチャ (データの隠蔽化や部品間のインターフェイスの簡潔化やモジュール間の機能分離の推進) になるようにコードを再編成することです。

<!--
Once your design sense (your equivalent of musical ear) is activated, you'll often find that you start refactoring each program you work on as rapidly as the third or fourth time around the incremental-hacking cycle.
 -->
デザインセンス(音楽分野の音楽を聞く耳に相当) が活性化すると、インクリメンタルハッキングサイクルを3回、4回と繰り返すうちに、各プログラムのリファクタリングを開始することが多いようです。

<!--
In fact, this is exactly how skilled hackers normally approach learning the code of large programs — by tinkering and refactoring and rewriting until they grok what is going on. You make small changes in order to learn how to make large ones.
 -->
 実際、熟練のプログラマが大規模なプログラムコードを習得する方法は、まさにこの方法です。
 何が起っているのか理解できるまで、いじって、リファクタリングし、書き直すのです。
 大きな変更を加える方法を学ぶために、小さな変更を加えるのです。

 <!--
 If you successfully refactor three or four large systems, you will not just develop strong programming skills, you will be on your way to something much more rare and powerful: becoming a software architect, one who can do original design of large software systems.
   -->
もし、あなたが3つか4つの大きなシステムのリファクタリングに成功したなら、
あなたは単に、協力なプログラミングスキルを身に付けただけではなく、もっと希少で強力な何かへの道を進んでいるでしょう。それはソフトウェアアーキテクト、つまり大規模なソフトウェアシステムの独自設計をできる人になる道です。

<!--
This is the only way I know of for fledgling software architects to train their design sense. It may be the only way there is.
 -->
 これは、私が知る限り、駆け出しのソフトウェアアーキテクトがデザインセンスを鍛えるための唯一の方法です。もしかしたら、これしかないのかもしれません。

<!--
## Being original
 -->
## 独創的であること

<!--
In my analogy with music, I said that you eventually need to learn how to recombine musical patterns (which you have learned by listening to music and practicing performance) into original compositions. I chose that way of describing creativity carefully, because it applies to software even more than it does to music.
 -->
私の音楽を使った例え話では、最終的には音楽のパターン (音楽を聴き、演奏の練習をすることで身につけたもの) を組み合せてオリジナルの作品を作る方法を学ぶ必要があると言いました。
創造力を表現する方法として、この例えを選んだのは、音楽以上にソフトウェアに当てはまるからです。

<!--
Before you have read and absorbed the lessons of a lot of code, you will probably not have in your head the pattern library you need to be creative on scales larger than very small ones. One purpose of doing the incremental-hacking cycle is to immerse yourself in a lot of code — at increasing complexity scales — under circumstances that provide you with motivation to keep reading.
 -->
多くのコードを読み、その教訓を吸収しなければ、より大きなプログラムを創造するために必要なパターンは身に付いていないでしょう。
インクリメンタルハッキングサイクルの目的の一つは、コードを読むモチベーションを維持できる環境下で、複雑さの規模を拡大しながら、多くのコードに没頭することです。

<!--
Eventually you will lead group projects and do entirely original work. Do not feel you have to rush this or force it; if you give your skills time to mature, your first original composition will be better for it. By contributing effectively to existing open-source projects you will learn the skills (including the communications skills) that you need to run your own projects.
 -->
最終的には、グループプロジェクトのリーダーとして、完全にオリジナルな仕事をするようになります。
これを急いだり、無理強いしたりする必要はありません。
もし、あなたのスキルの成熟に時間ををかけるなら、あなたの最初のオリジナル作品はより良いものになるでしょう。
既存のオープンソースプロジェクトに効果的に貢献することで、あなた自身のプロジェクトを運営するためのスキル (コミュニケーションスキルを含む) を学ぶことができます。

---

<!-- [1]: It is certainly possible to hack things other than software, and people in the maker culture do it.
But the term “hacking” originated among people who tinkered with software and still radiates out from there.
Besides, the author is not really qualified to write about learning other kinds. -->

[^1]: もちろん、ソフトウェア以外のものハックすることは可能で、メーカー文化の人々はやっています。しかし、もともとの「ハッキング」という言葉は、ソフトウェアをいじくっていた人々の間で生まれたものですが、今もなお、そこから派生しています。それに、著者は他分野のハッキングの学び方を書く資格はないでしょう。

<!--
[2] In former times, people hacked on closed source, when they could, because there was no alternative. Things have changed for the better.
 -->
[^2]: かつては、クローズドソースをハックしていました。代替手段がなかったからです。状況は良い方向に変わりました。

<!--
[3] Before 1983 or so the association between hacking and Unix was less strong, but the details of how that changed are now mainly relevant only to historians.
 -->
[^3]: 1983年以前は、ハッキングとUNIXの関係はそれほど強くありませんでした。どのように変化したかの詳細については、歴史家の分野です。
