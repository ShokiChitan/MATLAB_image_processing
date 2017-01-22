# 課題３「閾値処理」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG=imread('../images/pengin.png'); % 原画像の入力
ORG= rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause;

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，輝度値64を閾値として，画素の輝度値が63以下の場合に0，64以上の場合に1とする．

IMG = ORG > 64;
imagesc(IMG); colormap(gray); colorbar;
pause;

生成された画像を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/a2.jpg?raw=true)  
図2 閾値64

同様に，輝度値96，128，192を閾値とする．

IMG = ORG > 96;
imagesc(IMG); colormap(gray); colorbar;
pause;

IMG = ORG > 128;
imagesc(IMG); colormap(gray); colorbar;
pause;

IMG = ORG > 192;
imagesc(IMG); colormap(gray); colorbar;

生成された画像を図3～5に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/a3.jpg?raw=true)  
図3 閾値96

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/a4.jpg?raw=true)  
図4 閾値128

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/a5.jpg?raw=true)  
図5 閾値192

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図6)として実行した結果を図7～10に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/p1.jpg?raw=true)  
図6 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/p2.jpg?raw=true)  
図7 閾値64

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/p3.jpg?raw=true)  
図8 閾値96

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/p4.jpg?raw=true)  
図9 閾値128

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/images/p5.jpg?raw=true)  
図10 閾値192

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C3/kadai3.m)

### 考察
このように閾値の設定によって白黒画像における白い部分、黒い部分の割合が変化することがわかる。また，原画像によって輝度値の設定を変更しないと，図2のようにほとんど白だけの画像や図10のようにほとんど黒だけの画像になってしまい，元の画像を認識することが困難になってしまう．
