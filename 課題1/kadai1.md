# 課題１「標本化間隔と空間解像度」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG=imread('../images/ahiru.png'); % 原画像の入力  
imagesc(ORG); axis image; % 画像の表示

によって，原画像を読み込み，表示した結果を図１に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/ahiru.png?raw=true)  
図1 原画像(ahiru)

原画像を1/2サンプリングするには，画像を1/2倍に縮小した後，2倍に拡大すればよい．なお，拡大する際には，単純補間するために「box」オプションを設定する．

IMG = imresize(ORG,0.5); % 画像の縮小  
IMG2 = imresize(IMG,2,'box'); % 画像の拡大

1/2サンプリングの結果を図２に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/a1.jpg?raw=true)  
図2 1/2サンプリング

同様に原画像を1/4サンプリングするには，画像を1/2倍に縮小した後，2倍に拡大すればよい．すなわち，

IMG = imresize(ORG,0.5); % 画像の縮小  
IMG2 = imresize(IMG,2,'box'); % 画像の拡大

とする．1/4サンプリングの結果を図３に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/a2.jpg?raw=true)  
図3 1/4サンプリング

同様に，1/8から1/64サンプリングは，

IMG = imresize(ORG,0.5); % 画像の縮小  
IMG2 = imresize(IMG,2,'box'); % 画像の拡大

を繰り返す．サンプリングの結果を図4～7に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/a3.jpg?raw=true)  
図4 1/8サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/a4.jpg?raw=true)  
図5 1/16サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/a5.jpg?raw=true)  
図6 1/32サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/a6.jpg?raw=true)  
図7 1/64サンプリング

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図8)としてサンプリングを行った結果を図9～14に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/pengin.png?raw=true)  
図8 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/p1.jpg?raw=true)  
図9 1/2サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/p2.jpg?raw=true)  
図10 1/4サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/p3.jpg?raw=true)  
図11 1/8サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/p4.jpg?raw=true)  
図12 1/16サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/p5.jpg?raw=true)  
図13 1/32サンプリング

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C1/images/p6.jpg?raw=true)  
図14 1/64サンプリング

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/suke123/matlab_image_processing/blob/master/%E8%AA%B2%E9%A1%8C4/kadai4.m)

### 考察
このようにサンプリング幅が大きくなると，モザイク状のサンプリング歪みが発生することが確認できる．また，ahiruの画像よりもpenginの画像の方が画素数が多いため，サンプリング歪みが大きくなった場合でも、元の画像を多少は認識しやすいことがわかる．
