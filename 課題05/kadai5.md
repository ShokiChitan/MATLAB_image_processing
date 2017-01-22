# 課題５「判別分析法」

フリー画像「ahhiru」を原画像とする．この画像は縦531画素，横800画素のディジタルカラー画像である．

ORG=imread('../images/ahiru.png'); % 原画像の入力
ORG = rgb2gray(ORG); % カラー画像を白黒濃淡画像へ変換
imagesc(ORG); colormap(gray); colorbar;
pause;

によって，原画像を読み込み，表示した結果を図1に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C5/images/a1.jpg?raw=true)  
図1 原画像(ahiru)

原画像に対して，画素数や平均分散を計算し，クラス内分散・クラス間分散を求めることで，判別分析法を用いて2値化できる．

H = imhist(ORG); %ヒストグラムのデータを列ベクトルEに格納
myu_T = mean(H);
max_val = 0;
max_thres = 1;
for i=1:255
C1 = H(1:i); %ヒストグラムを2つのクラスに分ける
C2 = H(i+1:256);
n1 = sum(C1); %画素数の算出
n2 = sum(C2);
myu1 = mean(C1); %平均値の算出
myu2 = mean(C2);
sigma1 = var(C1); %分散の算出
sigma2 = var(C2);
sigma_w = (n1 *sigma1+n2*sigma2)/(n1+n2); %クラス内分散の算出
sigma_B = (n1 *(myu1-myu_T)^2+n2*(myu2-myu_T)^2)/(n1+n2); %クラス間分散の算出
if max_val<sigma_B/sigma_w
max_val = sigma_B/sigma_w;
max_thres =i;
end;
end;

IMG = ORG > max_thres;
imagesc(IMG); colormap(gray); colorbar;
pause;

2値化の結果を図2に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C5/images/a2.jpg?raw=true)  
図2 2値化画像

同様に，フリー画像「pengin」(縦1066画素，横1600画素のディジタルカラー画像)を原画像(図3)として実行した結果を図4に示す．

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C5/images/p1.jpg?raw=true)  
図3 原画像(pengin)

![原画像](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C5/images/p2.jpg?raw=true)  
図4 2値化画像

ソースコードのリンクを以下に添付する．

#### [ソースコード](https://github.com/ShokiChitan/MATLAB_image_processing/blob/master/%E8%AA%B2%E9%A1%8C5/kadai5.m)

### 考察
ahiruの画像では，アヒル自身の色は白で背景は暗い色であるため，背景との違いが分かるように2値化されている．しかし，アヒルの画像のくちばし付近やpenginの画像では，うまく2値化することができていない．これは，体の色や影になった部分と背景の色が近かったためであると思われる．
