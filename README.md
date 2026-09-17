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



