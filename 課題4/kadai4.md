# 課題４「画像のヒストグラム」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG=imread('../images/pengin.png'); % 原画像の入力
ORG=rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換
imagesc(ORG); colormap(gray); colorbar;
pause;

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C4/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像の濃度ヒストグラムを以下で表示する．

imhist(ORG); % ヒストグラムの表示

実行結果を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C4/images/a2.jpg?raw=true)  
図2 濃度ヒストグラム

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図3)として実行した結果を図4に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C4/images/p1.jpg?raw=true)  
図3 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C4/images/p2.jpg?raw=true)  
図4 濃度ヒストグラム

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C4/kadai4.m)

### 考察
ahiruの画像の場合，白い部分が多いため，図2からもわかるように200～250の範囲の明るい画素が多いことがわかる。一方，penginの画像の場合、図4からわかるように70～170くらいの範囲が多いため、グレーの画素が多い画像であることがわかる。
