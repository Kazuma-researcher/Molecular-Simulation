# GROMACSの導入
このマニュアルでは、最も有名なMDシミュレーションソフトの一つであるGROMACSの導入を解説する。GROMACSは生体分子の分子動力学に特化したソフトであり、特にタンパク質や脂質のシミュレーションによく用いられる。それらに比べると多糖のシミュレーションは出遅れている感があるが、外部アプリと組み合わせることで多糖のシミュレーションも可能。GROMACSの導入は基本的にCUIで行うため、以下では多数のコマンドが出てくるが、各コマンドの意味については別途ドキュメントを作成する予定なので、ここでは解説しない。  

## 参考サイト
GROMACSの導入や使い方の習得には、[MDNOTES](https://onefive13.github.io/homepage/index.html "MDNOTES")というサイトを参考にすることをおすすめする。シミュレーション初心者向けに基礎的な事項から説明しており、とても参考になる。特にチュートリアルが充実しており、これらを理解すれば様々なシミュレーションに応用することができると思われる。シミュレーションそのもの以外にも、Linuxやデータ解析、関連アプリなどについても解説されており、初心者が一通りのことを覚えるのに役立つ。  

## GROMACSのインストール
GROMACSのインストールはターミナルを用いたコマンド操作で行うが、結構ややこしいので筆者もすべての操作の意味を理解できていない。それらの意味を詳しく理解しようとしてもしょうがないと思うので、参考サイトに書いてある通りにインストールを進める。まずはブラウザでGROMACSをダウンロードするが、この操作はマウスを使ったGUIでOK。[GROMACSのダウンロードサイト](https://manual.gromacs.org/documentation/ "GROMACS documentation")を開き、いずれかのバージョンの「Download」をクリックする。最新のバージョンでもいいかもしれないが、筆者は2024.5版を使っている。  

![タイトルなし](https\://github.com/user-attachments/assets/08620374-77b4-4f20-bcbc-13ecd32c3166)

「Source code」の`https://ftp.gromacs.org/gromacs/gromacs-XXX.tar.gz`をクリックする。「gromacs-XXX.tar.gz」という名前のファイルがダウンロードされるはずである。XXXはバージョン番号。

![タイトルなし](https://github.com/user-attachments/assets/35e235ee-0574-4321-85ac-e7f03ff72515)


ターミナルを開き、以下のコマンドを順に実行して、ホームディレクトリに「GROMACS」という名前のフォルダを作成する。  

```bash
mkdir ~/GROMACS
```

次に、以下のコマンドを実行し、「ダウンロード」ディレクトリに移動する。※[仮想Linux環境の構築](./Virtual-Linux.md)の「Ubuntuの日本語化」を行う際に、標準フォルダの名前の変更を行わなかった場合は「Downloads」という名前になっている。

```bash
cd ~/ダウンロード
```

以下のコマンドを実行し、ダウンロードしたgromacsのファイルを上記で作成した「GROMACS」ディレクトリに移動させる。  

```bash
mv gromacs-XXX.tar.gz ~/GROMACS
```

以下のコマンドを実行し、「GROMACS」ディレクトリに移動する。  

```bash
cd ~/GROMACS
```

このディレクトリ内で`ls`コマンドを実行すれば、移動させたGROMACSの存在が確認できるはずである。次に、以下のコマンドを実行し、「gromacs-XXX.tar.gz」ファイルを展開する。  

```bash
tar -xzvf gromacs-XXX.tar.gz
```

これにより、「gromacs-XXX」というフォルダができているはずなので、以下のコマンドでそのディレクトリに移動する。

```bash
cd gromacs-XXX
```

以下のコマンドを実行し、GROMACSのビルド先フォルダとインストール先フォルダを作っておく。   

```bash
mkdir build
mkdir gmx_install
```

以下のコマンドを実行し、「build」ディレクトリに移動する。

```bash
cd build
```

以下のコマンドを実行し、cmakeを行う。-が付いている部分では、GROMACSのインストールをする際のオプションを指定している。すべてのオプションについての詳細は筆者もよくわからない。`-DCMAKE_INSTALL_PREFIX`ではインストール先のディレクトリを指定している。`-DGMX_MPI`は並列計算を仕様するかどうか、`-DGMX_GPU`はGPUを使用した計算を行うためのオプションである。ここでは手元のPCでの練習という位置づけなのでいずれもOFFとしているが、スパコンを仕様した高速計算を行う場合はこれらをONとする。高速計算を行うためのオプションは[こちらのページ](https://onefive13.github.io/homepage/GROMACS/GROMACSinstall.html "GROMACSのインストール")を参照。

```bash
cmake ../ \
-DGMX_BUILD_OWN_FFTW=ON \
-DREGRESSIONTEST_DOWNLOAD=ON \
-DCMAKE_INSTALL_PREFIX=${HOME}/GROMACS/gromacs-XXX/gmx_install \
-DGMX_MPI=OFF \
-DGMX_DOUBLE=OFF \
-DGMX_GPU=OFF
```

以下のコマンドを実行する。

```bash
make -j 4
```

以下のコマンドを実行し、GROMACSをインストールする。

```bash
make install
```

上述したようにGROMACSのインストール先を「gmx_install」ディレクトリに指定したので、インストールが成功していればこのディレクトリにGROMACSの実行ファイルが存在するはずである。左メニューから「ファイル」を開き、`ホーム/GROMACS/gromacs-XXX/gmx_install`の中に「bin」などのフォルダがあればOK。「bin」の中に「gmx」という名前でGROMACSの実行ファイルが入っている。  
以下のコマンドを実行し、.bashrcファイルにGROMACSのパスを通す。これにより、どのディレクトリからでもGROMACSコマンドを実行することができる。  

```bash
export PATH=${HOME}/GROMACS/gromacs-XXX/gmx_install/bin:${PATH}
```

>[!NOTE]
>パスとはファイルやディレクトリの場所を指定する文字列であり、.bashrcファイルに書かれているパスをPATHや環境変数と呼ぶ。通常`$gmx`のように特定の実行ファイル名をコマンド入力して実行する際、今いるディレクトリ（カレントディレクトリ）に該当の実行ファイルがなければ実行できない。しかし、.bashrcファイルのPATHにその実行ファイルのパスを記載していれば、カレントディレクトリに該当のファイルが無くても実行することができる。したがって、PATHに書かれているディレクトリにある実行ファイルは、どこのディレクトリからでも実行することが可能である。これは、コンピュータが実行コマンドを受けた際、まずカレントディレクトリに該当の実行ファイルがあるかを探し、なければPATHに書かれているディレクトリを探しに行くためである。

このままではPATHの追記がまだ反映されていないので、以下のコマンドを実行して.bashrcファイルを更新する。

```bash
source ~/.bashrc
```

以下のコマンドを実行してGROMACSのバージョンが表示されれば、問題なくインストールできている。

```bash
gmx --version
```
