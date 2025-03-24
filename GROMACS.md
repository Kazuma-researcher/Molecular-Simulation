# GROMACSの導入
このマニュアルでは、最も有名なMDシミュレーションソフトの一つであるGROMACSの導入を解説する。GROMACSは生体分子の分子動力学に特化したソフトであり、特にタンパク質や脂質のシミュレーションによく用いられる。それらに比べると多糖のシミュレーションは出遅れている感があるが、外部アプリと組み合わせることで多糖のシミュレーションも可能。GROMACSの導入は基本的にCUIで行うため、以下では多数のコマンドが出てくるが、各コマンドの意味については別途ドキュメントを作成する予定なので、ここでは解説しない。  

## 参考サイト
GROMACSの導入や使い方の習得には、[こちらのサイト](https://onefive13.github.io/homepage/index.html "MDNOTES")を参考にすることをおすすめする。シミュレーション初心者向けに基礎的な事項から説明しており、とても参考になる。特にチュートリアルが充実しており、これらを理解すれば様々なシミュレーションに応用することができると思われる。シミュレーションそのもの以外にも、Linuxやデータ解析、関連アプリなどについても解説されており、初心者が一通りのことを覚えるのに役立つ。  

## GROMACSのインストール
GROMACSのインストールはターミナルを用いたコマンド操作で行うが、結構ややこしいので筆者もすべての操作の意味を理解できていない。それらの意味を詳しく理解しようとしてもしょうがないと思うので、参考サイトに書いてある通りにインストールを進める。まずはブラウザでGROMACSをダウンロードするが、この操作はマウスを使ったGUIでOK。[GROMACSのダウンロードサイト](https://manual.gromacs.org/documentation/ "GROMACS documentation")を開き、いずれかのバージョンの「Download」をクリックする。最新のバージョンでもいいかもしれないが、筆者は2024.5版を使っている。  

![タイトルなし](https\://github.com/user-attachments/assets/08620374-77b4-4f20-bcbc-13ecd32c3166)

「Source code」の`https://ftp.gromacs.org/gromacs/gromacs-XXX.tar.gz`をクリックする。「gromacs-XXX.tar.gz」という名前のファイルがダウンロードされるはずである。XXXはバージョン番号。

![タイトルなし](https://github.com/user-attachments/assets/35e235ee-0574-4321-85ac-e7f03ff72515)


ターミナルを開き、以下のコマンドを順に実行して、ホームディレクトリに「GROMACS」という名前のフォルダを作成する。  

```bash
$mkdir ~/GROMACS
```

次に、以下のコマンドを実行し、「ダウンロード」ディレクトリに移動する。※仮想Linux環境の構築で[Ubuntuの日本語化](https://github.com/Kazuma-researcher/Molecular-Simulation/blob/5cb10d49663b86a2c77e4bfe8710d1978c5001fa/Virtual-Linux.md#ubuntu%E3%81%AE%E6%97%A5%E6%9C%AC%E8%AA%9E%E5%8C%96)  

```bash
$cd ~/ダウンロード
```
