# JJClab_HW7
參考筆記: https://github.com/wsunccake/sle15_notes/blob/master/practice/ch2.md

---------------------------------------------------------------------------
# 練習 8. File Attributes 與 Extended Attributes
## 8-1-1.
把 /etc/hosts 設成 immutable:   
<img width="932" height="154" alt="image" src="https://github.com/user-attachments/assets/6570c38e-11c7-4773-b643-687d1456883c" />

驗證無法被修改、刪除或重新命名:  
<img width="932" height="149" alt="image" src="https://github.com/user-attachments/assets/5d2f4b3e-ee20-4387-8eb1-577db708dbf0" />

測試完成後解鎖:  
<img width="935" height="506" alt="image" src="https://github.com/user-attachments/assets/d0ab833d-3a43-4fcf-aaa2-7814baa6409e" />

## 8-1-2.
建立測試檔:    
<img width="925" height="134" alt="image" src="https://github.com/user-attachments/assets/8c5ab485-5e9d-48b9-925f-b96d03064b74" />

依序測試「可以追加」、「不能覆寫」、「不能清空」:  
<img width="933" height="234" alt="image" src="https://github.com/user-attachments/assets/5cbe4f14-daf0-4166-b4be-b41f6c1487d5" />

## 8-1-3.
先建立一組測試資料，並確認預設attributes: 
<img width="929" height="341" alt="image" src="https://github.com/user-attachments/assets/940124ee-580f-4a97-a8f0-bf48936e61aa" />

遞迴鎖定後，測試是否真的被鎖住:  
<img width="927" height="327" alt="image" src="https://github.com/user-attachments/assets/2356d6ab-511e-4308-b5fc-b7dcf7a41deb" />

## 8-1-4.
模擬故障情境，先建立測試檔案，鎖住後確認:  
<img width="933" height="202" alt="image" src="https://github.com/user-attachments/assets/ae629c57-5988-4d7e-bf76-15a38293c5fc" />

模擬發現故障後，啟動排查，首先確認一般權限，無誤後，確認File Attributes得到immutable:  
<img width="927" height="133" alt="image" src="https://github.com/user-attachments/assets/1ca8644f-2cd2-472c-beee-0874fa05efeb" />

解除鎖定後，再次刪除:  
<img width="928" height="124" alt="image" src="https://github.com/user-attachments/assets/57908cc0-a125-4781-8318-fc69a9204741" />

## 8-2.
準備題目指定的檔案，確認後新增user.author=Alice，再驗證:  
<img width="922" height="196" alt="image" src="https://github.com/user-attachments/assets/d92bf8ec-0388-4513-af66-bb12a5a93353" />

新增 user.security_level=confidential，確認後，查看全部 Extended Attributes:  
<img width="926" height="252" alt="image" src="https://github.com/user-attachments/assets/367acb5e-b41d-46c0-b0d0-776e3e701562" />

作者改成 Bob，安全等級也修改，最後移除user.security_level後，再次確認:  
<img width="923" height="359" alt="image" src="https://github.com/user-attachments/assets/1f89f571-b6ed-4a6f-b1e9-956607eb80eb" />

------------------------------------------------
# 練習 9. vim 進階操作

## 9-1

### 9-1-1. 快速列跳轉與文字定位

| 小題    | 問題                         | 作答 |
| ------- | ---------------------------- | ---- |
| 9-1-1-1 | 直接跳到第 **250** 行？      | 250G or :250      |
| 9-1-1-2 | 跳轉後，快速到該行**行尾**？ |   $  |
| 9-1-1-3 | 快速移到檔案**最後一行**？   |   G  |

### 9-1-2. 高效複製、剪下與刪除

| 小題    | 問題                                       | 作答 |
| ------- | ------------------------------------------ | ---- |
| 9-1-2-1 | 一次剪下（刪除）從目前游標起的 **5 行**？  |   5dd   |
| 9-1-2-2 | 快速刪除游標所在的一個 **word**？          |    dw  |
| 9-1-2-3 | 將剛剪下／複製的內容貼在目前行的**下方**？ |  p    |

### 9-1-3. 全域搜尋與取代

| 小題    | 問題                                     | 作答 |
| ------- | ---------------------------------------- | ---- |
| 9-1-3-1 | 整份文件所有 `abc` 取代為 `xyz`          |   :%s/abc/xyz/g   |
| 9-1-3-2 | 只取代第 **10～50** 行之間               |    :10,50s/abc/xyz/g  |
| 9-1-3-3 | 每次取代前要 **Confirm**，應加什麼參數？ |   :%s/abc/xyz/gc   |

補充9-1-3-1: 
| 指令   | 指令內容                                     | 
| ------- | ---------------------------------------- | 
|%|整份文件|
|s|substitute|
|abc|搜尋文字|
|xyz|取代文字|
|g|同一行中全部符合項目都取代|

### 9-1-4. 區塊選擇與多行批次編輯
先建立測試用檔案:  
<img width="926" height="51" alt="image" src="https://github.com/user-attachments/assets/d14a73ed-569f-49f3-8a22-ff787ffae2aa" />

一次插入所有被選取行的開頭，流程:  
5G → 0 → Ctrl-v → 選到15行 → I → "# " → Esc

### 9-1-5. 多檔案與視窗分割
使用<vim -O /etc/hosts /etc/resolv.conf>垂直分割：  
<img width="928" height="1005" alt="image" src="https://github.com/user-attachments/assets/30c5640c-c39e-45c4-bab0-0c3a5f183dd2" />

使用<vim -o /etc/hosts /etc/resolv.conf>垂直分割： 
<img width="932" height="1002" alt="image" src="https://github.com/user-attachments/assets/af7ddd70-5a3c-4232-b775-24fa281189ad" />

其他指令與內容:  
| 目的   | 指令                                     | 
| ------- | ---------------------------------------- | 
|視窗切換|Ctrl+w w|
| 左|Ctrl+w h  |
| 下|Ctrl+w j  |
| 上|Ctrl+w k   |
| 右|Ctrl+w l   |
|只存目前窗格|:w|
|全部存|:wa|
|全部離開|:qa|

------------------------------------------------
# 練習 10. 管線、重導向與區間擷取

## 參照表
| 符號 | 意義 |
|---|---|
| `\|` | 前一個指令的輸出交給下一個指令 |
| `>` | 覆蓋寫入檔案 |
| `>>` | 追加到檔案尾端 |
| `2>` | 將錯誤訊息 stderr 重導向 |
| `/dev/null` | 丟棄資料 |

## 10-1. 系統日誌即時擷取與轉向寫入
題目要求從系統 log 的最後 50 行找出包含 CRON 的行，而且不分大小寫，最後覆蓋寫入 /tmp/cron_recent.log。SLES 上可能使用 /var/log/messages，題目也允許依實際環境調整:  
<img width="928" height="165" alt="image" src="https://github.com/user-attachments/assets/2af2ab66-f50f-41ce-bd3b-2ea6c6e1dfe9" />

## 10-2. 歷史資料附加與統計累計
確認帳號數後，因為 /var/log/ 通常需要 root 權限，使用<wc -l /etc/passwd | sudo tee -a /var/log/user_count.log>，再寫入寫時間戳:  
<img width="929" height="233" alt="image" src="https://github.com/user-attachments/assets/2648e916-71f6-4815-83e2-0baf409d9a0b" />

## 10-3. 檔案指定區間擷取
在家目錄建立測試資料後，執行測試:  
<img width="932" height="594" alt="image" src="https://github.com/user-attachments/assets/b3438283-48e9-4e25-b0a9-e972fce7a138" />
<img width="929" height="253" alt="image" src="https://github.com/user-attachments/assets/6d141348-2889-46d9-bd85-353fba604f56" />

## 10-4. 錯誤訊息分離與重導向
<img width="927" height="83" alt="image" src="https://github.com/user-attachments/assets/ba9fde5d-461d-4490-a367-26a7115aa8a1" />

終端畫面沒有輸出，再次確認:  
<img width="931" height="756" alt="image" src="https://github.com/user-attachments/assets/3fa72f4d-6657-4541-8514-9d18a0cef30b" />




