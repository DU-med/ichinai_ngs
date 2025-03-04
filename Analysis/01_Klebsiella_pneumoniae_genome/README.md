# Klebsiella_pneumoniae_genomeの内容  
肺炎球菌サンプルのマッピング  
肺炎球菌のサンプルfastqファイルを肺炎球菌の参照配列に対してマッピングを行う  

## 参考論文  
[Genomic epidemiology and temperature dependency of hypermucoviscous Klebsiella pneumoniae in Japan](https://pubmed.ncbi.nlm.nih.gov/35622495/)  
肺炎桿菌ゲノムをショート・ロングリードでDe novo assemblyし配列を決定  
genotypeごとに分類

## 論文内のサンプルデータ情報
https://www.ncbi.nlm.nih.gov/Traces/study/?acc=DRP007748&o=acc_s%3Aa

## 上記のサイトの情報をもとにDRRのIDリストを作成した
**samples.txt**: 論文内で解析されているすべてのサンプルのDRRのIDを記載  

## 解析の下準備
Rast-tkの設定
https://github.com/TheSEED/RASTtk-Distribution/releases  
上記サイトからrasttk-v1.3.0.debをダウンロード  
```
# 一行目のコマンドで多くのエラーが出力されるが、気にせず二行目を実行
sudo dpkg -i rasttk-v1.2.0.deb 
sudo apt-get install -f
```
## 解析のフロー
1. parallel-fastq-dumpを使い各サンプルのfastqファイルの取得 
2. shovillでDe novo assembly  
3. phameで系統樹作成に必要なfasttreeファイルを作成
4. FigTreeでfasttreeファイルから系統樹を作成


### 1. parallel-fastq-dumpを使い各サンプルのfastqファイルの取得
DRRのID(samples.txt)をもとにparallel-fastq-dumpを使ってfastq.gzファイルをダウンロード  
ダウンロード後のファイル合計サイズは58G程度  
```
parallel -j 5 parallel-fastq-dump --threads 8 --split-files --gzip --outdir fastq --sra-id {} :::: sample.txt
```

### 2. shovillでDe novo assembly
```
shovill --outdir DRR320006 --R1 fastq/DRR320006_1.fastq.gz --R2 fastq/DRR320006_2.fastq.gz --ram 8 --cpus 4
```

### 3. phameで系統樹作成に必要なfasttreeファイルを作成
[phameの実行](https://github.com/utsumidaisuke/ichinai_ngs/tree/main/Tutorial/12_phame_tutorial)  

### 4. FigTreeでfasttreeファイルから系統樹を作成
[FigTree](https://github.com/rambaut/figtree/releases)
