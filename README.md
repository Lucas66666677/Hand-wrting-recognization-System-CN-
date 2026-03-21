# 個人化 AI 手寫辨識系統 (CNN + Gradio)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Lucas66666677/Hand-wrting-recognization-System-CN-/blob/main/AI%E6%89%8B%E5%AF%AB%E8%BE%A8%E8%AD%98%E7%B3%BB%E7%B5%B1%E5%96%AE%E5%80%8B%E6%95%B8%E5%AD%97CNN.ipynb)
* 這是一個基於 TensorFlow/Keras 構建的卷積神經網路（CNN）模型，專門用於辨識 0-9 的手寫數字。訓練完成後，透過 **Gradio** 部署成互動式的網頁應用程式，讓使用者可以直接在畫布上書寫並即時獲得 AI 的預測結果。
## 主要特色與實作細節

除了基本的模型訓練外，這個專案特別針對「真實手寫輸入」做了影像預處理，以解決網頁畫布與 MNIST 訓練集格式不一致的問題：

* **OpenCV 影像預處理**：當使用者在網頁畫布上寫字時，筆跡大小和位置都不固定。程式會透過 `cv2.boundingRect` 自動抓取筆跡邊界，將數字裁切並等比例縮放至 20x20 像素，最後置中貼齊於 28x28 的黑色背景上。這個步驟能大幅提升實際手寫時的辨識準確率。
* **模型架構**：建構了 5 層的 CNN 模型（包含 Conv2D、MaxPooling2D 與 Dropout 等機制），總參數量約 120 萬。
* **模型表現**：在 MNIST 測試集上驗證，準確率可達約 99.16%。

## 如何執行

這份程式碼可以直接在 Google Colab 上完整運行：

1. 點擊上方的 `Open in Colab` 按鈕將 Notebook 在瀏覽器開啟。
2. 依序執行所有程式碼區塊（或點選 `執行階段` -> `全部執行`）。
3. 執行到最後一個儲存格時，Gradio 會在終端機輸出一段公開網址（例如：`https://xxxx.gradio.live`）。
4. 點擊該網址，即可開啟網頁介面開始測試。

## 使用套件

* `tensorflow` (Keras)
* `opencv-python` (cv2)
* `gradio`
* `numpy`, `matplotlib`, `seaborn`
