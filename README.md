# 分子シミュレーション導入マニュアル  
このマニュアルでは、分子シミュレーション（主にMD）の導入や使い方、チュートリアルについてまとめる。Windows上にLinux仮想環境を構築してシミュレーションを行うことを想定しているため、本格的な高速計算はできない。実際のLinux環境やサーバを使用した実践的なシミュレーションの前に、手元のPCで行う練習という位置づけ。  
  
MDシミュレーションそのものだけでなく、MDの導入に必要な仮想Linux環境の構築やコマンド、初期構造の作成やシミュレーション結果の可視化アプリケーション、入力ファイル作成のためのエディタなど、シミュレーション周辺の事項についても解説する。  
  
以下に、本マニュアルで主に使用する仮想環境、MDエンジン、エディタ、MD周辺アプリを記す。各項目の詳細についてはそれぞれのドキュメントを参照。  

- 仮想環境
  - Ubuntu（仮想マシンにはVirtualBoxを使用）
- MDエンジン　　
  - GROMACS
  - LAMMPS
- エディタ
  - VSCode
  - Vim
- MD周辺アプリ
  - PyMOL
  - Packmol
  - VMD
  - CHARMMGUI(オンライン)
- その他
  - Miniconda3
  - Cellulose Builder
