# 課題２「階調数と疑似輪郭」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG=imread('../images/pengin.png'); % 原画像の入力
ORG = rgb2gray(ORG); colormap(gray); colorbar; % グレースケール化
imagesc(ORG); axis image; % 画像の表示
pause; % 一時停止

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，元の256階調のうち，0～127は0，128～255は1とすることで，白黒の2階調で表現された画像が生成される．

IMG = ORG>128;
imagesc(IMG); colormap(gray); colorbar;  axis image;
pause;

2階調画像を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/a2.jpg?raw=true)  
図2 2階調画像

同様に，原画像に対して，0～63，64～127，128～191，192～255の4つに分割することで，4階調で表現された画像が生成される．

IMG0 = ORG>64;
IMG1 = ORG>128;
IMG2 = ORG>192;
IMG = IMG0 + IMG1 + IMG2;
imagesc(IMG); colormap(gray); colorbar;  axis image;
pause;

4階調画像を図3に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/a3.jpg?raw=true)  
図3 4階調画像

同様に，原画像に対して，0～31，32～63，64～95，96～127，128～159，160～191，192～223，224～255の8つに分割することで，8階調で表現された画像が生成される．

IMG0 = ORG>32;     
IMG1 = ORG>64;     
IMG2 = ORG>96;     
IMG3 = ORG>128;    
IMG4 = ORG>160;    
IMG5 = ORG>192;     
IMG6 = ORG>224;     
IMG = IMG0 + IMG1 + IMG2 + IMG3 + IMG4 + IMG5 + IMG6;    
imagesc(IMG); colormap(gray); colorbar;  axis image;   

8階調画像を図4に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/a4.jpg?raw=true)  
図4 8階調画像

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図5)として実行した結果を図6～8に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/p1.jpg?raw=true)  
図5 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/p2.jpg?raw=true)  
図6 2階調画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/p3.jpg?raw=true)  
図7 4階調画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/images/p4.jpg?raw=true)  
図8 8階調画像

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C2/kadai2.m)

### 考察
このように階調数が大きくなるほど，グレースケール化した原画像に近くなることがわかる．また，原画像において濃い色で表現された部分は黒で表現され，淡い色で表現されている部分は白で表現される．
