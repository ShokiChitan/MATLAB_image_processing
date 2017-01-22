# 課題８「ラベリング」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG = imread('../images/ahiru.png'); % 画像の読み込み
ORG = rgb2gray(ORG); % 白黒濃淡画像に変換
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause;

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，閾値128によって2値化する。

IMG = ORG > 128; % 閾値128で二値化
imagesc(IMG); colormap(gray); colorbar; % 画像の表示
pause;

2値化した画像を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/images/a2.jpg?raw=true)  
図2 2値化画像

次に，ラベリング(同じ連結成分に属する画素ごとに番号を付ける処理)を行う．

IMG = bwlabeln(IMG);
imagesc(IMG); colormap(jet); colorbar; % 画像の表示
pause;

実行結果を図3に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/images/a3.jpg?raw=true)  
図3 ラベリング画像

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図4)として実行した結果を図5～6に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/images/p1.jpg?raw=true)  
図4 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/images/p2.jpg?raw=true)  
図5 2値化画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/images/p3.jpg?raw=true)  
図6 ラベリング画像

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C8/kadai8.m)

### 考察
ラベリングによって同じ連結成分に属する画素には同一の番号，ことらる連結成分に属する画素には異なった番号が割り振られていることが，ラベリングを行った画像の色分けからわかる．
