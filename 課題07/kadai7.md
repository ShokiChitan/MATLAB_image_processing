# 課題７「ダイナミックレンジの拡大」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG = imread('../images/ahiru.png'); % 画像の読み込み
ORG = rgb2gray(ORG); % 白黒濃淡画像に変換
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause;

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，濃度ヒストグラムを生成する．

imhist(ORG); % 濃度ヒストグラムを生成、表示
pause;

生成された画像を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/a2.jpg?raw=true)  
図2 濃度ヒストグラム

次に，原画像をダイナミックレンジに拡大する．

ORG = double(ORG);
mn = min(ORG(:)); % 濃度値の最小値を算出
mx = max(ORG(:)); % 濃度値の最大値を算出
ORG = (ORG-mn)/(mx-mn) * 255;
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause;

実行結果を図3に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/a3.jpg?raw=true)  
図3 ダイナミックレンジでの画像

図3に対して，濃度ヒストグラムを生成する．

ORG = uint8(ORG);
imhist(ORG); % 濃度ヒストグラムを生成、表示

生成された画像を図4に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/a4.jpg?raw=true)  
図4 濃度ヒストグラム

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図5)として実行した結果を図6～8に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/p1.jpg?raw=true)  
図5 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/p2.jpg?raw=true)  
図6 濃度ヒストグラム

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/p3.jpg?raw=true)  
図7 ダイナミックレンジでの画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/images/p4.jpg?raw=true)  
図8 濃度ヒストグラム

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C7/kadai7.m)

### 考察
濃度ヒストグラムの結果を比較してみると、若干ではあるが，ダイナミックレンジに変換した方が範囲が広がっていることがわかる．
また，
ORG = uint8(ORG);
は，濃度を8ビット符号なし整数に変換している．これによって濃度範囲を拡大し，ヒストグラムにおいて濃度範囲を拡大することができる．
