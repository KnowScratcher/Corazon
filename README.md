# 共寫更新
最新版本請寫在最上面

# 24/03/02 更新進度
`JT_0`
`version v0.6.4 (Main : Terminal!)`
- Main
  - 更新終端機輸出模式，使用 f 字串 (Line 214)

# 24/03/01 更新進度
`Kai`
`version v0.6.4 (Light Engine : DynaMarkX i)`
- Kernel
  - `DynaMarkX i`再次縮減啟動所需時間 (相較DMX減少80%以上啟動時間)
  - 修正cv2無法正常關閉Bug
- UI_Beta2
  - 移除`快速啟動` (註：目前開啟速度與`快速啟動`相同)
  - `快速啟動`改為`略過動態效能追蹤` (註：對效能影響極小，僅在啟動問題時開啟)
- Main
  - 開啟`自動曝光`
  - 新增DMXi進行`動態效能追蹤`
  - DMX現在目標更新率為5FPS(原為10FPS)
## DynaMarkX i (intelligent)
- 新增偵測閥，僅在幀間時間超過限定次數後強制關閉
- 新增DMX開關，可在啟動前控制開閉
![DMXi](https://github.com/nKiux/Bio-HRMonitor/assets/46084374/dde6edc8-95eb-43a3-b384-a2454408254b)



# 24/02/29 更新進度
`Kai`
`version v0.6.3 (Light Engine : DynaMarkX!)`
- UI_Beta2
  - 修復Benchmark呼叫失敗Bug
- main
  - 修復模式選擇Bug
  - 新增DynaMarkX
- Kernel
  - 縮減啟動所需步驟
## 隆重介紹：DynaMarkX!
在安全啟動下減少60%以上的啟動時間！ (完整啟動，即未開啟`KernelSpeedUP!`)

透過**動態追蹤每一幀所花費的時間**進行判斷電腦效能是否符合需求

若偵測到效能問題則自動停止偵測

目前`DynaMarkX`可允許的最小更新速度為10FPS

`註：在開啟KernelSpeedUP的情況下仍會執行DMX`
![DMX](https://github.com/nKiux/Bio-HRMonitor/assets/46084374/813947f6-3af5-469f-ad49-199493767256)

# 24/02/28 更新進度
`Kai`
`version v0.6.2(Light Engine : UI Update!)`
- Kernel
  - 新增`模式選擇`
  - 改進開啟前清空檔案方式，空白檔案由第一行開始
  - 相機啟動失敗回傳`False`
- UI_Beta2
  - 新增模式變數
  - 重新設計UI
  - 新增`相機選擇`轉盤(及函式)
  - 新增`模式選擇`轉盤(及函式)
  - `Result`於相機失敗時顯示相關訊息
  - 新增`測試結束BPM顯示`，由`result.txt`讀取
- main
  - 若相機失敗回傳`False`
  - 新增`模式轉譯`，減少架構改變
  - 將BPM即時寫入`result.txt`，結束後轉交給UI輸出(UI_Beta2更新第6點) (註：需要算法配合，請於設定時間測試結束後將OpenCV結束，以便輸出)
  - 新增`模式選擇即時輸出`

- 舊UI

![image](https://github.com/nKiux/Bio-HRMonitor/assets/46084374/d867ca59-8eeb-4e03-8ae1-c6f1d45c3a58)

- 新UI

![image](https://github.com/nKiux/Bio-HRMonitor/assets/46084374/850a845a-efb8-4e04-bb13-5d9ccecbb0ae)

`Kai`
`vesion v0.6.1(HotFix)`
- Kernel
  - 更新`FPS檢查`測試方式，避免除以0的情況發生
- UI_Beta2
  - 更新按鍵操作機制，避免重複點擊出現Bug

# 24/02/27 更新進度

`JT_0`
`version v0.6(Light Engine : Algorithm)`
- Main
  - 加入 `time` 函式庫。 (Line 4)
  - `benchmark()` 函式為舊版本，本次更新只對 `start()` 做更新。
  - 更改手指偵測的判斷方式。 (Line 156, 160)
  - 加入紀錄亮度值的陣列 `bright_rec`，紀錄的為 `bright` (浮點數, A)。 (Line 176)
  - 加入 `passed`，使用於時間計算。 (Line 177)
  - 修改終端機輸出方式，改為刷新，但未來需更改。 (Line 211)
  - 算法
    - 新增算法及心跳偵測。 (Line 190~207)
    - 新增 `HR_monitor()`心跳偵測函式。 (Line 219~251)

# 
`Kai`
`version v0.5.1(Light Engine : Performance Check)`
- Kernel
  - `Fast Start`設定為`False`時，自動**新增**與 **!清空!** `Test.txt`存放亮度資料
- main
  - `Benchmark`內新增`FPS檢查`，檢查完畢的FPS數據將於終端機輸出以及存至`FPS`變數
  - 將亮度資料寫入`Test.txt` (僅在Finger_Detect = True時進行寫入，手離開後自動清空)


# 24/02/24 更新進度
`Kai`
`version v0.5.0(Light Engine : NewUI!)`
- Kernel
  - 修改為**以函式啟動**，由`UI_Beta2`開啟
  - 將**效能測試**與**正規啟動**分開宣告
  - 新增 `cv2.destroyAllWindows()` 正確關閉cv2視窗
- Main
  - 30行新增 `cv2.destroyAllWindows()`
  - 31行新增 `exit()`
- UI_Beta2
  - 使用**PyQt5**
  - **啟動主程式**
  - 基礎UI設計
  - `Start`連接至`kernel_LightEngine.start`
  - `Benchmark`連接至`kernel_LightEngine.pure_benchmark`
  - `Result`顯示`Benchmark`結果
  - `Fast Start`勾選框控制**快速啟動開關**
  - *`BPM`待接入*
 
`備註：目前相機只能使用相機0，需要自行在kernel_LightEngine和UI_Beta2內進行修改`

# 24/02/21 更新進度
`Kai`
`no version has been updated.`
- Kernel
  - 移除**舊Kernel**

# 24/02/20 更新進度
`Kai`
`version v0.4.3(Light Engine : FiX!)`
- Kernel
  - 修復 **程式無法運作**
  - 新增一些註解
  - 移除 **舊相機控制方法**
  - 移除 **Kernel** 的性能測試選項，若未開啟 **Kernel SpeedUP!** 將會自動執行 **Benchmark**
- Main
  - 移除 **舊相機控制方法**
  - 移除 **舊馬賽克方法**
#
`Kai`
`version v0.4.2(Light Engine : Cam_Beta)`
- Kernel
  - 新增**性能測試**至啟動 `若未通過性能測試則程式自動關閉`
  - 若**快速啟動**為`False`且**性能測試**為`False`，則程式將不會運作(bug，將會修復)
- Main
  - **性能測試**將不會開啟相機預覽 `減少非必要閃爍與開啟視窗`
  - 新增**所有webcam通用控制項**，需要自行下載插件放入與程式相同資料夾 `控制相機參數確保可以運作`
- cam_sett.cfg
  - 新增相機控制項
  - [cfg_cam下載](https://github.com/SuslikV/cfg-cam)
  - 將此程式與`cam_sett.cfg`放入與Main, kernel_LightEngine相同資料夾

# 24/02/18 更新進度
`Kai`
`version v0.4.1 (Light Engine : SPD)`
- Kernel
  - 新增**性能測試** `統計10次計算共花時間(需在3秒內完成) 並顯示測試成果`
  - 新增**Kernel_speedup!** `略過啟動部分項目，共減少約50%啟動時間`
- Main
  - 拆分**Kernel**檔案至**Main** `加強易讀性`
  - 新增**benchmark** `使用簡易算法，配合上述說明使用`

# 24/02/15 更新進度
`Kai`
`version v0.4 (Light Engine : Initial)`
- Kernel
  - 新增**確信度評分** `等待10次update才開始進行校準`
  - 新增**自動校準** `每30次偵測到手指的update自動重設平均亮度最大值與最小值`
  - 新增**重新設定解析度** `統一偵測的畫面長寬`
  - 修改**降噪算法** `使用單色與模糊進行畫面模擬，更易觀察亮度變化`
  - 關閉**馬賽克降噪** `此方法已不再適用`

# 24/02/10 更新進度
`Kai`
`version v0.3.1`
- Kernel
  - 新增牛逼進度條

# 24/02/09 更新進度
`Kai`
`version v0.3`
- Kernel
  - 新增除錯訊息
  - 相機曝光鎖定
  - 相機對比鎖定
  - 相機銳利度鎖定 (未確認此項功能正常運作)
  - 開啟前檢測cv2
  - 開啟前相機設定與檢測
  - 馬賽克尺寸重新調整
- 需改進
  - 相機降噪算法
  - 是否移動至開發手機app (電腦平台感光元件實在是太小，無法捕捉細微脈搏)

# 24/02/08 更新進度
`Kai`
`version v0.2`
- Kernel  
  - 手指偵測
  - 馬賽克
  - 相機開啟
  - R、G、B、Brightness 平均值計算

- 需要改進
  - 相機降噪算法
  - 算法
