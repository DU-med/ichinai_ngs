# seqkit_tutorialの内容
**seqkitでfasta、fastqファイルの操作**  

## seqkit
fasta、fastqファイルから特定の配列、情報を抽出する   
[github](https://github.com/shenwei356/seqkit)   
[参考サイト1](https://kazumaxneo.hatenablog.com/entry/2017/08/08/235042)  
[参考サイト2](https://bioinfo-nanihitotsu.weebly.com/software/category/seqkit)  

## seqkitのインストール
```
mamba install -c bioconda seqkit
```

## サンプルファイル
virus.fna.gz: 30のウイルスゲノム配列が保存されているファイル  

## 具体的な使用方法
**配列IDの抽出**
```
seqkit seq -n virus.fna.gz
```

**IDリストから当該IDの配列を抽出する**
```
seqkit grep -f list.txt virus.fna.gz
```

**特定の文字列を含むIDの配列を抽出**
```
seqkit grep -nrp NC_013590.2 input.fasta
```

**fastaファイル内のIDの抽出**
```
seqkit seq -ni input.fasta
```

**ファイルの塩基の情報についての簡単な情報**
```
seqkit stat input.fasta
```
