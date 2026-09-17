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
