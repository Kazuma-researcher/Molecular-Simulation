# 仮想Linux環境の構築
LinuxはオープンソースのOSであり、ソフト開発などの目的に応じてユーザーが自由にカスタマイズすることを想定して、最低限の機能だけを備えた土台となるOSである。Linuxを土台として開発された様々な派生的なOSは**ディストリビューション**と呼ばれ、代表的なものとしてUbuntu、CentOS、Debianなどがある。Windowsがマウスを介したグラフィックベースの操作（GUI）をメインとするのに対し、Linuxはターミナルを介したコマンドベースの操作（CUI）がメインである。Linuxでもマウスによる操作は可能であるが、多くの場合コマンドによって操作を実行することになる。  

Linuxは上述のような柔軟性やカスタマイズ性に加え、高いセキュリティ性や安定性などの面から、サーバーのOSとして採用されることが多い。**シミュレーションソフトは基本的にサーバーを介した大規模・高速計算を想定していることから、Linux向けに作られたものがほとんどである。** したがって、WindowsPCでMDシミュレーションを行うには、Windows上に仮想的なLinux環境を構築する必要がある。これはWindowsPCの中に仮想的なPCを作成し、その中にLinuxをインストールするようなイメージである。この仮想的なPCのことを**仮想マシン**と呼ぶ。

Windows11にはLinux環境を提供するための仮想マシンである**Windows Subsystem for Linux (WSL)** がデフォルトで入っており、これを利用した仮想Linux環境の構築を解説しているサイトが多い。筆者も最初はWSLを利用していたが、WSLからインターネットにアクセスするとファイアウォールに引っかかってしまうためプロキシを通す必要があることや、Windows updateのたびに仮想Linux環境が壊れてしまうなどの問題点があったため、あまりおすすめしない。筆者はWSLに代わる仮想マシンとして、**VirtualBox**を使用した。VirtualBoxは使い方が非常に簡単で、その見た目から仮想マシンのイメージもつきやすいのでおすすめ。  

## VirtualBoxのインストール
[VirtualBoxのダウンロードページ](https://www.virtualbox.org/wiki/Downloads "Download VirtualBox")を開き、「VirtualBox Plaform Packages」の中から「Windows hosts」をクリックし、インストーラをダウンロード。  

![タイトルなし](https://github.com/user-attachments/assets/6cc80717-8179-4468-b224-6a55d77fcf29)
<src >

インストーラを実行し、画面の指示に従ってインストールを進める。基本的に何も変更しなくてよい。インストール完了後、VirutalBoxが自動的に開く。  

## Ubuntuのダウンロードと起動
Ubuntuは最も広く使用されているLinuxディストリビューションである。Ubuntuの日本語Remix版が[こちらのサイト](https://www.ubuntulinux.jp/News/ubuntu2204-ja-remix "Ubuntu 22.04 LTS 日本語 Remix リリース")で配布されている。  

![タイトルなし](https://github.com/user-attachments/assets/60149a19-d218-41bf-be03-6c80e63f8728)

いずれかのミラーサイトを開き、.isoのファイルをダウンロードする。これが、仮想マシンにロードするUbuntuのイメージファイルである。  

![タイトルなし](https://github.com/user-attachments/assets/009952d7-8580-4128-bc8a-52f728e02290)

VirtualBoxを開き、"新規"をクリック。  

![タイトルなし](https://github.com/user-attachments/assets/9f1fdbb4-0181-4180-86ef-ca53ef2457b3)

仮想環境の名前とOSを入力する画面になる。「名前」には"Ubuntu"などの環境名を付ける。「Folder」は仮想環境内で作成されたファイルの保存先と思われる。特に希望がなければそのままでOK。「ISO Image」は、先ほどUbuntuのイメージファイルをダウンロードしたフォルダに移動し、ファイルを選ぶ。これらの入力が終わったら「次へ」をクリック。  

![タイトルなし](https://github.com/user-attachments/assets/b7e32307-84c9-4200-9c3d-42ff2f560f2a)

Ubuntuでログインするときのユーザー名やパスワードを設定する画面になる。「Username and Password」の欄を入力し、「次へ」をクリック。  

![タイトルなし](https://github.com/user-attachments/assets/003b443b-0a5b-4a79-a5ab-f980c1eb4457)

Ubuntuの仮想的なメモリの量とCPUのコア数を設定する画面になる。緑色の領域が推奨設定。筆者はメモリを2048MB、CPUを4としている。設定後、「次へ」をクリック。

![タイトルなし](https://github.com/user-attachments/assets/18a9d26f-cc33-4d1a-a3b4-44084dadce57)

Ubuntuの仮想的なハードディスク容量を設定する画面になる。筆者は25GBとしている。設定後、「次へ」をクリック。

![タイトルなし](https://github.com/user-attachments/assets/5981c4ef-944b-4f03-afae-c6182c35057c)

設定内容を確認する画面になる。問題なければ「完了」をクリック。これで仮想環境の設定が完了。　　

![タイトルなし](https://github.com/user-attachments/assets/915c5192-0631-4f8d-8fa4-45c64394e3b4)

VirtualBoxでUbuntuを選択し、「起動」もしくは起動ボタンの中の「通常起動」をクリック。※初回起動時にエラーが発生する場合があり、その対処法は下の方に記述。  

![タイトルなし](https://github.com/user-attachments/assets/f49b4408-1760-41ca-87c7-ad8908334ea2)

初回起動時は以下のような画面が出るので、"Ubuntu with Japanese input support"を選択し、Enter。インストールが始まるので、完了するまで待つ。

![タイトルなし](https://github.com/user-attachments/assets/64d11791-696f-4d16-b115-0074bb66706b)

インストール完了後、ログイン画面となるので、先ほど設定したユーザー名を選択し、設定したパスワードを入力。

<img src="https://github.com/user-attachments/assets/5703a985-3081-4cff-92f6-ac2b62e2ea1b" width="40%"> <img src="https://github.com/user-attachments/assets/75c9f1ee-9439-47fa-9fb6-e6439f471cc1" width="40%">

以上で、Ubuntuの起動が完了。　　

## 初回起動時のエラーへの対処
VirutualBoxをインストールしてから初めて仮想環境を起動する際、`NtCreateFile(\Device\VBoxDrvStub) failed`のようなエラーダイアログが出ることがある。これはVirtualBoxのドライバが存在しないか起動していないことによるエラーである。以下に対処法を記す。  

powershellを起動し、以下のコマンドを実行してドライバがインストールされているか確認。インストールされていれば概要が表示される。  

```powershell
> sc.exe query vboxsup
```

インストールされていない場合は、`C:\Program Files\Oracle\VirtualBox\drivers\vboxsup`ディレクトリの中にあるinfファイルを右クリックし、インストールを実行後、再起動。インストールされている場合はpowershell（管理者権限）で下記コマンドを実行し、ドライバを起動。  

```powershell
> sc.exe start vboxsup
```

## Ubuntuの日本語化
日本語RemixのUbuntuをインストールしたが、実はこのままでは日本語対応になっていないため、日本語化設定をする必要がある。右上の電源マークから、「Settings」をクリック。  

![タイトルなし](https://github.com/user-attachments/assets/d3fc2344-8434-4d47-b580-8055853ddbbf)

「Region & Language」をクリックし、「Language」で「Japanese」を選択後、「Restart」をクリックして再起動。

![タイトルなし](https://github.com/user-attachments/assets/ab9dbceb-fbf0-4675-92b7-79477da71bab)

標準フォルダの名前を言語に合わせて更新するか選択。

![タイトルなし](https://github.com/user-attachments/assets/9823ded3-bcaf-4667-8a64-4ec5bee972b8)

以上で日本語化完了。

## キーボード割り当ての変更
デフォルトのキーボード割り当ては日本仕様になっていないため、これを変更する必要がある。メニューからターミナルを起動し、以下のコマンドを実行。  

```bash
$ sudo dpkg-reconfigure keyboard-configuration
```
以下のようにいくつかの画面が出るので、画像の通り選択。  

<img src="https://github.com/user-attachments/assets/1c3893cb-df16-4380-ad1b-9fb264d389df" width="40%"> <img src="https://github.com/user-attachments/assets/861babc2-e6d0-4971-9d62-2c6af8cc7fbf" width="40%">
<img src="https://github.com/user-attachments/assets/e8e59684-9163-48b5-9875-f47d44b21ab7" width="40%"> <img src="https://github.com/user-attachments/assets/b0d480ef-8c13-48da-ba43-e1f29eeb4d0b" width="40%">
<img src="https://github.com/user-attachments/assets/3f8822ab-403e-48d8-949e-e6404ea789c6" width="40%"> <img src="https://github.com/user-attachments/assets/a73c2b2d-f486-43f5-9dd4-7252826b373f" width="40%">



