# Richart 

遮蔽 Richart app 偵測越獄設備, 使得禁用某些功能<br>
此專案只是一個學術研究, 請勿作為商業用途<br>

# 思路

找出 Richart app 中檢測的代碼, 在修改為通過檢測, 即完成遮蔽<br>

### 使用工具
1. [frida-ios-dump](https://github.com/AloneMonkey/frida-ios-dump) (敲殼工具)
2. [IDA PRO](https://www.hex-rays.com/products/ida/) (反編譯工具)
3. [MonkeyDev](https://github.com/AloneMonkey/MonkeyDev) 自帶的 Logos Tweak (打包插件工具)
4. [Cydia BigBoss源](http://thebigboss.org/hosting-repository-cydia/submit-your-app) (上架插件)

### 操作

1. 使用 frida-ios-dump 導出敲殼後的 Richart.ipa, 使用方式請查看 frida-ios-dump 的相關解說, 這邊再說明
2. 將取得的 Richart.ipa 右鍵解壓縮, 得到 Richart.app, 在右鍵顯示套件內容, 找到 Richart(Unix 執行檔)
3. 將第二步取得的 "執行檔", 使用 IDA PRO 開啟反編譯
4. 在 IDA PRO function 視窗中, 搜索相關方法, 這邊運氣很好, 直接搜索 "jail", 就找出相關方法了
5. 打開 Xcode 創建 MonkeyDev 自帶的 Logos Tweak 專案
6. 在 ".xm" 中撰寫需修改的方法
![撰寫](https://github.com/s2339956/RichartNotJailbroken/blob/master/image/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202018-09-18%20%E4%B8%8B%E5%8D%884.05.53.png?raw=true)
7. Package -> Library -> MobileSubstrate -> DynamicLibraries -> ".plist" 設置目標 app Bundle
![設置目標appBundle](https://github.com/s2339956/RichartNotJailbroken/blob/master/image/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202018-09-18%20%E4%B8%8B%E5%8D%884.05.02.png?raw=true)
8. 運行專案
9. 打開專案資料夾 Packages, 找到 ".deb" 
10. 上傳至 BigBoss源
![BigBoss源](https://github.com/s2339956/RichartNotJailbroken/blob/master/image/%E8%9E%A2%E5%B9%95%E5%BF%AB%E7%85%A7%202018-09-18%20%E4%B8%8B%E5%8D%884.06.40.png?raw=true)
<br>
以上步驟就完成了 一個插件的開發<br>
<br>

