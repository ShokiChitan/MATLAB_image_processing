# 課題９「メディアンフィルタと先鋭化」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG = imread('../images/ahiru.png'); % 画像の読み込み
ORG = rgb2gray(ORG); % 白黒濃淡画像に変換
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause;

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，ノイズを添付する．

ORG = imnoise(ORG,'salt & pepper',0.02); % ノイズ添付
imagesc(ORG); colormap(gray); colorbar; % 画像の表示
pause;

生成された画像を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/a2.jpg?raw=true)  
図2 ノイズ付き画像

ノイズを添付した画像に対して，平滑化(画素ごとの濃度値の細かな変動をなくす処理)を行う．

IMG = filter2(fspecial('average',3),ORG); % 平滑化フィルタで雑音除去
imagesc(IMG); colormap(gray); colorbar; % 画像の表示
pause;

生成された画像を図3に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/a3.jpg?raw=true)  
図3 平滑化した画像

次に，メディアンフィルタによってノイズ除去を行う．

IMG = medfilt2(ORG,[3 3]); % メディアンフィルタで雑音除去
imagesc(IMG); colormap(gray); colorbar; % 画像の表示
pause;

生成された画像を図4に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/a4.jpg?raw=true)  
図4 メディアンフィルタを通した画像

相関関係によるフィルタを通す．

f=[0,-1,0;-1,5,-1;0,-1,0]; % フィルタの設計
IMG = filter2(f,IMG,'same'); % フィルタの適用
imagesc(IMG); colormap(gray); colorbar; % 画像の表示
pause;

実行結果を図5に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/a5.jpg?raw=true)  
図5 フィルタを通した画像

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図6)として実行した結果を図7～10に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/p1.jpg?raw=true)  
図6 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/p2.jpg?raw=true)  
図7 ノイズ付き画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/p3.jpg?raw=true)  
図8 平滑化した画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/p4.jpg?raw=true)  
図9 メディアンフィルタを通した画像

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/images/p5.jpg?raw=true)  
図10 フィルタを通した画像

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C9/kadai9.m)

### 考察
ノイズを添付した画像に対して平滑化を行うことで，注目した画素を周辺の画素との平均の濃度にすることができるため．ノイズ除去をすることができるが，ノイズが残ってしまう部分や輪郭がぼけてしまう部分があることがわかる．一方，メディアンフィルタを用いることで，ノイズが残ってしまう部分や輪郭がぼけてしまう部分を作らずにノイズ除去することが可能であるとわかる．また，相関関係によるフィルタを通すことで，濃淡ははっきりしなくなってしまうが，ノイズ除去をすることは可能であることもわかる．
