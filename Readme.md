說明:此程式利用大數據訓練資料，讓ai程式能夠判斷出圖中資訊。


程式碼簡介:

1. 讀入資料圖檔

這裡把在 GitHub 上 myna.zip 的照片集讀進來。

2. 把照片轉成訓練資料

3. 用 ResNet50 打造我們的神經網路
ResNet50 是 2015 ImageNet 的冠軍, 我們用第二版來試試。
原本 ImageNet 是做了 1,000 個類別的圖形辨識。我們想直接用來辨識八哥, 
就是把最後一層 (通常就 1,000 個輸出的 dense 層) 砍掉 (include_top=False), 然後換我們的就好。
再來我們可以把每個 filter 的結果做個大總合, 例如算每個 filter 計分板的總平均 (global avg pooling), 
這本來該我們自己做, 但是 tf.Keras 是善良無比的幫我們做好。只要下個參數 pooling="avg")。

4. 訓練 fit

5. 預測

對了, 為何這次我們沒有切測試一一資料呢? 那是因為畢竟我們每張八哥沒多少照片...

6. 用 gradio 打造八哥辨識 web app!