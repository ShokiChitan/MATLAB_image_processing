# 課題１０「画像のエッジ抽出」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG = imread('../images/ahiru.png'); % 原画像の入力
ORG = rgb2gray(ORG); %カラーからグレイへの変換
imagesc(ORG); colormap('gray'); colorbar;% 画像表示
pause; % 一時停止

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，プレウィット法を用いたエッジ抽出を行う．

IMG = edge(ORG,'prewitt'); % エッジ抽出（プレウィット法）
imagesc(IMG); colormap('gray'); colorbar;% 画像表示
pause; % 一時停止

実行結果を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/a2.jpg?raw=true)  
図2 プレウィット法の結果

次に，原画像に対して，ソルベ法を用いたエッジ抽出を行う．

IMG = edge(ORG,'sobel'); % エッジ抽出（ソベル法）
imagesc(IMG); colormap('gray'); colorbar;% 画像表示
pause; % 一時停止

実行結果を図3に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/a3.jpg?raw=true)  
図3 ソルベ法の結果

同様に，原画像に対して，キャニー法を用いたエッジ抽出を行う．

IMG = edge(ORG,'canny'); % エッジ抽出（キャニー法）
imagesc(IMG); colormap('gray'); colorbar;% 画像表示
pause; % 一時停止

実行結果を図4に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/a4.jpg?raw=true)  
図4 キャニー法の結果

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図5)として実行した結果を図6～8に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/p1.jpg?raw=true)  
図5 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/p2.jpg?raw=true)  
図6 プレウィット法の結果

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/p3.jpg?raw=true)  
図7 ソルベ法の結果

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/images/p4.jpg?raw=true)  
図8 キャニー法の結果

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C10/kadai10.m)

### 考察
結果からわかるように，
(プレウィット法)＜(ソルベ法)＜(キャニー法)
の順で多くのエッジを抽出していることがわかる．特に，キャニー法については非常に多くのエッジを抽出しているため，プレウィット法，ソルベ法よりも優れた方法であることがわかる．
