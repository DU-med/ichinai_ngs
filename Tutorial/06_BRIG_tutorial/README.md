# BRIG_tutorialの内容
**BRIG(BLAST Ring Image Generator)で複数の細菌ゲノムの比較**  

## BRIG
複数のfasta,fna,gbkファイル形式の最近ゲノムやプラスミドを読み込み、参照配列と比較を行う  
[参考サイト](https://brig.sourceforge.net/)    
[github](https://github.com/happykhan/BRIG)  


## 下準備
javaやBLASTの設定を事前に行う必要あり

### Macの下準備

**javaのインストール**  
(サイト: https://www.oracle.com/jp/java/technologies/downloads/#jdk19-mac)  
M1,M2チップ用のインストーラのダウンロードしインストール  
```
wget -c https://download.oracle.com/java/19/latest/jdk%2D19_macos%2Daarch64_bin.dmg
```
Intel CPU用のインストーラのダウンロードしインストール   
```
wget -c https://download.oracle.com/java/19/latest/jdk-19_macos-x64_bin.dmg
```
    
**BLASTのインストール**
(サイト: ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/)  
Mac(M1,M2,Intel)用のインストーラのダウンロード  
解凍したファイルを実行しBLASTをインストールする  
```
wget -c ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST//ncbi-blast-2.13.0+.dmg
```

### Linuxの下準備
**javaのインストール(Linux)**  
```
mamba install -c bioconda java-jdk
```
  
**BLASTのインストール(Linux)**  
```
mamba install -c bioconda blast
```  

### サンプルデータの取得  
肺炎球菌参照ゲノムデータ:   
https://www.ncbi.nlm.nih.gov/nuccore/NZ_CP020549  
肺炎球菌比較ゲノムデータ：  
1:https://www.ncbi.nlm.nih.gov/nuccore/NZ_CP018136  
2:https://www.ncbi.nlm.nih.gov/nuccore/NZ_CP018137  
3:https://www.ncbi.nlm.nih.gov/nuccore/NZ_CP018138   
  
gbファイルの取得方法  
<img src="pics/ncbi.png" width='40%'>

## BRIGの実行ファイルのダウンロード
下記のサイトにアクセスすると必要なファイルが自動的にダウンロードされる  
https://sourceforge.net/projects/brig/files/latest/download  
ダウンロードしたファイルをデスクトップに移動し、解凍する  

## BRIG.jarの実行  
ターミナルを開き、BRIG.jarファイルのあるディレクトリで下記のコマンドラインを実行  
-Xmx以下の数値は割り当てるメモリの大きさ
```
java -Xmx4000M -jar BRIG.jar
```
BRIGのGUIでの操作方法の詳細は下記の動画を参照  
https://www.youtube.com/watch?v=CTugtM1LR0M  

BRIGの入力例  
<img src="pics/brig1.png" height='250'><img src="pics/brig2.png" height='250'><img src="pics/brig3.png" height='250'> 

## BRIGの実行結果の一例  
<img src="pics/strain_Hu17_ref.gb.jpg" width='60%'> 
