


# D2 Nodes ComfyUI

[<a href="README.md">English</a>][<a href="README_ja.md">日本語</a>][繁體中文]

**D2 Nodes ComfyUI** 是一個使 ComfyUI 變得更加方便的自定義節點集合。

**適合想要創建簡單工作流程的用戶。**

我們整合了之前創建的以下自定義節點，並添加了諸如 D2 KSampler 等節點。  
**如果您已經安裝了以下自定義節點，請刪除它們，因為節點名稱會發生衝突。**

- [ComfyUI-d2-size-selector](https://github.com/da2el-ai/ComfyUI-d2-size-selector)
- [ComfyUI-d2-steps](https://github.com/da2el-ai/ComfyUI-d2-steps)
- [ComfyUI-d2-xyplot-utils](https://github.com/da2el-ai/ComfyUI-d2-xyplot-utils)

## :tomato: 節點

### D2 Regex Switcher
  <img src="./img/regex_switcher_1.png">

  - 使用正則表達式搜索輸入文本，並輸出匹配的文本
  - 還可以進行字符串連接
  
<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  - 主要目的是切換每個 Checkpoint 的質量標籤
  - 當在輸入的 `text` 中發現匹配的字符串時，會輸出目標字符串和它是第幾個匹配（從0開始）
  - 在上面的圖片中，接收到 `ioliPonyMixV4.safetensors`，匹配搜索條件 `pony`，所以輸出 `score_9`
  - 因為匹配了第一個搜索條件，所以 `index` 輸出 `0`
  - 如果不匹配任何條件，則輸出 `-1`
  - 可以進行字符串的前後連接

  #### 輸入

  - `text`
    - 搜索目標字符串
  - `prefix`
    - 前方連接的字符串
  - `suffix`
    - 後方連接的字符串
  - `regex_and_output`
    - 搜索字符串和輸出字符串的列表
    - 按以下格式填寫

  ```
  搜索字符串 1（可以使用正則表達式）
  --
  輸出字符串 1
  --
  搜索字符串 2（可以使用正則表達式）
  --
  輸出字符串 2
  --
  --
  沒有匹配時輸出的字符串
  ```

  #### 輸出

  - `combined_text`
    - 連接 `prefix` + 輸出字符串 + `suffix` 的字符串
  - `prefix` / `suffix`
    - 輸入的直接傳遞

  #### 使用示例

  <img src="./img/regex_switcher_2.png">

  在這個例子中，將匹配的編號（`index`）傳遞給 [Easy Use](https://github.com/yolain/ComfyUI-Easy-Use) 的 Text Index Switch 進行切換。

  因為不匹配時會變成 `-1`，所以使用匹配所有字符串的正則表達式 `.+` 作為默認輸出的替代。
</details>

### D2 Prompt SR

  <img src="./img/prompt_sr.png">

  - 搜索和替換輸入文本並以列表形式返回的節點
  - 用於在 XY Plot 中使用 Prompt S/R 的自定義節點
  - 兼容 [qq-nodes-comfyui](https://github.com/kenjiqq/qq-nodes-comfyui)

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸入

  - `prompt`
    - 提示。可以包含換行
  - `search_txt`
    - 搜索目標文本。可以包含多個單詞。
    - 不能使用換行
  - `replace`
    - 替換用文本
    - 因為用換行分隔，所以即使包含「,」也沒問題

  #### 輸出

  - LIST
    - 以列表形式輸出替換後的文本

</details>

### D2 Multi Output

  <img src="./img/multi.png">

  - 輸出 seed 或 cfg 等通用參數列表的節點

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸入
  - `type`
    - `FLOAT`: 浮點數。例如 CFG
    - `INT`: 整數。例如 steps
    - `STRING`: 字符串。例如 sampler
    - `SEED`: 可以用隨機生成按鈕輸入 seed 值
  - `Add Random`
    - 在輸入欄添加隨機數
    - 只有在 `type` 為 `SEED` 時才顯示

</details>

### D2 Checkpoint Loader

<img src="./img/checkpoint_loader.png">

  - 輸出模型文件完整路徑的 Checkpoint Loader

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸出
  
  - `model` / `clip` / `vae`
    - 與傳統的 CheckpointLoader 相同。
  - `ckpt_name` / `ckpt_hash` / `ckpt_fullpath`
    - Checkpoint 名稱、哈希值、完整路徑。

  實現主要使用了 [mikey_nodes](https://github.com/bash-j/mikey_nodes) 的代碼。

</details>

### D2 KSampler / D2 KSampler(Advanced)

<img src="./img/ksampler.png">

  - 可以以 STRING 形式輸入提示的 KSampler

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸入

  - `model` / `clip` / `vae` / ..etc
    - 與標準 KSampler 相同
  - `negative` / `positive`
    - STRING 格式的提示

  #### 輸出

  - `IMAGE`
    - 圖像輸出
  - `positive` / `negative`
    - 輸入的直接傳遞

</details>

### D2 Size Selector

<img src="./img/sizeselector.png">

  - 可以從預設中選擇圖像尺寸的節點

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸入

  - `preset`
    - 尺寸預設
    - 如果想更改預設，請編輯 `/custom_nodes/D2-nodes-ComfyUI/config/sizeselector_config.yaml`
  - `width` / `height`
    - 寬高尺寸
  - `swap_dimensions`
    - 交換 width / height
  - `upscale_factor`
    - 傳遞給其他調整大小相關節點的值
  - `prescale_factor`
    - 調整 width / height 的倍數
  - `batch_size`
    - 設置 empty_latent 的 batch size
  
  #### 輸出
  
  - `width / height`
    - 將輸入的 `width`、`height` 乘以 `prescale_factor`
  - `upscale_factor` / `prescale_factor`
    - 直接傳遞輸入的值
  - `empty_latent`
    - 輸出指定尺寸和 batch size 創建的 latent
  - `batch_size`
    - 直接傳遞輸入的值

</details>

### D2 Refiner Steps

<img src="./img/refiner_steps.png">

  - 輸出 Refiner 用 steps 的節點

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸入

  - `steps`
    - 總步數
  - `start`
    - 第一個 KSampler 開始的步數
  - `end`
    - 第一個 KSampler 結束的步數
  
  #### 輸出
  
  - `steps` / `start` / `end`
    - 輸入的直接傳遞
  - `refiner_start`
    - 第二個 KSampler 開始的步數

</details>

### D2 Refiner Steps A1111

<img src="./img/refiner_a1111.png">

  - 可以為 img2img 的 Refiner 指定 denoise 的節點

<details class="d2-details">
  <summary><strong>詳細信息</strong></summary>

  #### 輸入

  - `steps`
    - 總步數
  - `denoise`
    - 指定 img2img 的 denoise
  - `switch_at`
    - 在總步數的多少比例切換到下一個 KSampler
  
  #### 輸出
  
  - `steps` / 
    - 輸入的直接傳遞
  - `start`
    - 第一個 KSampler 開始的步數
  - `end`
    - 第一個 KSampler 結束的步數
  - `refiner_start`
    - 第二個 KSampler 開始的步數

</details>

### D2 Refiner Steps Tester
  - 用於確認步數的節點

## :card_index_dividers: 示例工作流程
將圖像拖放到 ComfyUI 中可以重現工作流程。

**SDXL 的 XY Plot**

<a href="./workflow/XYPlot_SDXL_20241002.png"><img src="./workflow/XYPlot_SDXL_20241002.png"></a>

**NovelAI 的 XY Plot**
<a href="./workflow/XYPlot_NAI_202401002.png"><img src="./workflow/XYPlot_NAI_202401002.png"></a>

**根據 Checkpoint 的完整路徑名判斷並切換質量標籤**
<a href="./workflow/XYPlot_Checkpoint_20241002.png"><img src="./workflow/XYPlot_Checkpoint_20241002.png"></a>

**在 Refiner 中途切換 Checkpoint**
<a href="./workflow/Refiner_20241002.png"><img src="./workflow/Refiner_20241002.png"></a>

## :computer: 安裝選項

### 1. ComfyUI Manager 安裝
ComfyUI Manager → Custom Node Manager → 搜索 `D2 Nodes` 並安裝

### 2. Git Pull 方法
在 custom_nodes 文件夾中執行 `git clone`
```
> git clone https://github.com/da2el-ai/D2-nodes-ComfyUI.git
```

## :blossom: 更新日誌

**2024.10.02**

- 整合現有節點創建
