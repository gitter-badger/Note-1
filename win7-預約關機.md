# win7-預約關機
###### tags: `cmd` `windows` `win7` `預約關機`
 參考至:[http://dreamtails.pixnet.net/blog/post/26178309-windows-7-%E4%BD%BF%E7%94%A8%E6%8C%87%E4%BB%A4%E8%AE%93%E5%AE%83%E9%A0%90%E7%B4%84%E9%97%9C%E6%A9%9F%21](http://dreamtails.pixnet.net/blog/post/26178309-windows-7-%E4%BD%BF%E7%94%A8%E6%8C%87%E4%BB%A4%E8%AE%93%E5%AE%83%E9%A0%90%E7%B4%84%E9%97%9C%E6%A9%9F%21)

#### step 1.

開啟「命令提示字元」   或 點選「開始」→「執行」→輸入`cmd`

step 2.

輸入`shutdown -s -t 60`

//若要5分鐘後自動關機，那就60 × 5 = 300(秒)

//step 2 的 60 指的是60秒，也就是一分鐘後會自動關機的意思!

#### 取消預約關機：

#### step 1.

開啟「命令提示字元」   或 點選「開始」→「執行」→輸入`cmd`

step 2.

輸入`shutdown -a`

#### 註：

-s 指的是將電腦關機。

-t 指的是將關機前的等候逾時時間設定為 xxx 秒，正確的範圍是 0-315360000，所以預約關機最久可以設定10年後電腦自己關機

-r 指的是將電腦關機並重新啟動。

-a 指的是中止系統關機。只有在等候逾時期間可以使用這個選項。

shutdown此指令所在位置為`C:\Windows\System32\shutdown.exe`