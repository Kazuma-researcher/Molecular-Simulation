# GROMACSチュートリアル
[GROMACSの導入](./Introduction.md "GROMACSの導入")でも紹介したが、[MDNOTES](https://onefive13.github.io/homepage/index.html "MDNOTES")には非常に優れたGROMACSのチュートリアルが掲載されており、特にチュートリアル2は応用範囲の広いものになっていると思う。本マニュアルではMDNOTESと同じチュートリアルの解説は行わないが、MDNOTESのチュートリアルの内容も一通り理解しておくことをおすすめする。ここでは、筆者が行ったセロオリゴ糖1分子のMDシミュレーションをチュートリアルとして解説する。

## 入力ファイルの作成
分子シミュレーションで最初にやらなければいけないことは、入力ファイルの作成である。これは計算そのものではないので本質的ではないただの前処理のように思えるが、実は**シミュレーションにおいて最も重要なプロセス**と言っても過言ではない。MDそのものは指定された計算方法に従って、入力された分子の運動を計算するだけであるから、得られた結果が現実と合わない場合、間違っているのは計算ではなく入力の方である。つまり、シミュレーションの結果が現実を再現するためには適切な入力ファイルの作成が必要である。また、全原子MDの計算可能な時間スケールはせいぜいナノ秒程度であり、入力された初期構造が自分の興味のある瞬間の構造からかけ離れていると、その構造に至る前にシミュレーションが終了してしまうことになる。したがって、興味のある瞬間の直前の構造を初期構造として入力することが求められる。以上の点から、入力ファイルの作成はシミュレーションの結果を大きく左右する極めて重要なプロセスである。

MDシミュレーションの入力ファイルの作成は、一から手で行うと大変な作業になる。そのため、入力ファイル作成のための様々な支援ツールが開発されており、有償のものもあれば無償で配布されているものもある。GROMACSやAMBERのような広く使用されているシミュレーションソフトには、基本的に入力ファイル作成支援ツールが付属している。例えばGROMACSの場合、まず計算を行いたい分子のPDBファイルを入手し、以下のコマンドを実行することで、PDBファイルをGROMACS用入力ファイルに変換してくれる。

```bash
gmx pdb2gmx -f XXX.pdb -o XXX.gro
```

MDNOTESのチュートリアルでもこのツールを使用して入力ファイルの作成を行っている。ただ、GROMACSやAMBERは核酸や脂質やタンパク質のシミュレーションに特化していることから、多糖の入力ファイル作成にはあまり強くない。そこでこのチュートリアルでは、セロオリゴ糖のGROMACS用入力ファイルの作成に、**CHARMM-GUI**というオンラインの支援ツールを利用する。
