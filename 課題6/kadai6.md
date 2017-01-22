# 課題６「画像の二値化」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

clear; % 変数のオールクリア
ORG=imread('../images/pengin.png'); % 原画像の入力
ORG = rgb2gray(ORG);
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause; % 一時停止

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，閾値を128として，127以下の場合に0，128以上の場合に1とする．

IMG = ORG>128; % 128による二値化
imagesc(IMG); colormap(gray); colorbar; % 画像の表示
pause;

生成された画像を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/images/a2.jpg?raw=true)  
図2 閾値による2値化

また，ディザ法(ある決められた階調でより豊富な階調を表現する技法．(例)白と黒しか使えない状態でさまざまな濃さの灰色を表現する)によって2値化を行う．

IMG = dither(ORG); % ディザ法による二値化
imagesc(IMG); colormap(gray); colorbar; % 画像の表示

生成された画像を図3に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/images/a3.jpg?raw=true)  
図3 ディザ法による2値化

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図4)として実行した結果を図5～6に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/images/p1.jpg?raw=true)  
図4 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/images/p2.jpg?raw=true)  
図5 閾値による2値化

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/images/p3.jpg?raw=true)  
図6 ディザ法による2値化

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C6/kadai6.m)

### 考察
結果を見るとわかるように，閾値を用いて2値化を行うよりもディザ法を用いて2値化を行った方が原画像に近い画像を得ることができている．これは，ディザ法は各画素ごとに濃度が決められるため，原画像において明るい部分では白，暗い部分では黒が多くなっているからである.
