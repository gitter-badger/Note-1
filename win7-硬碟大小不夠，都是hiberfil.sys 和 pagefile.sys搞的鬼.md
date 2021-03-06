# win7-硬碟大小不夠，都是hiberfil.sys 和 pagefile.sys搞的鬼
###### tags: `win7` `windows` `硬碟`
 參考至:[http://dreamyeh.pixnet.net/blog/post/28462639-%5B%E6%8A%80%E8%A1%93%5D-%E9%97%9C%E9%96%89windows7%E7%9A%84hiberfil.sys-%E5%92%8C-pagefile.sys](http://dreamyeh.pixnet.net/blog/post/28462639-%5B%E6%8A%80%E8%A1%93%5D-%E9%97%9C%E9%96%89windows7%E7%9A%84hiberfil.sys-%E5%92%8C-pagefile.sys)

#### 一、問題描述

最近買了一顆昂貴的SSD-美光C300，小小64GB就要三千"大爺"，還真是心疼呀～回來後一試用，馬上享受到SSD的飆速快感！一個開機動作，以前非得花個將近一分鐘，現在開機速度卻是以十幾秒來計算！

不過享受速度快感之虞，也發現嚴重問題－硬碟大小不夠用呀![](https://lh4.googleusercontent.com/ydt7-liqfVF5irgeLCELIOMJhCm_TTBOIY1WHHzPThsfdZKhiWMmJP9h6ihFVYmHanvF7jcyduucwgKvdOmUHH5glk_8ZnriJvSzfCDshFQ9gdcQpz_UUoLt-VClp8JqEw9rRaW3)！不過裝個Windows和一些常用的應用程式，64GB硬碟瞬間只剩下10幾GB～雖然還能撐下去，卻差不多甚麼應用程式都不敢再灌！追根究柢原因，在於在沒使用固態硬碟之前，硬碟容量可以說俗又大碗，1TB在現在來說根本是基本單位！但是到SSD後，小小容量就要不少摳摳，這時候容量就變得十分珍貴～解決方法只有兩個，要嘛開源，用小朋友去解決，要嘛就要節流！不過現在只有灌少少系統程式，怎麼會花到這麼多磁碟空間哩？

看一下系統磁碟，再開了一下顯示隱藏檔案，才發現這兩個龐然怪物－hiberfil.sys 和 pagefile.sys，天哪！一個檔案大小就10幾GB（筆者的記憶體擴充到很大），難怪很簡單就把系統磁碟占滿了！想要刪除這兩個檔案？很抱歉！這可是系統檔案，不會這麼簡單就被你刪除的！以下就講解這兩個檔案分別是甚麼，並且教導大家如何去刪除這兩個檔案，好還硬碟一些空間出來！

![00.jpg](https://lh4.googleusercontent.com/4Qic-ewCmB9sX41D_uRWUX5IiWUsDjIdwk0vJ6HaNjhb70HGvJh-8lef8yrrv9IUKaYC3lMrLjIGQ3INIM1PCMhu4YMUfV1KjSTeki_DVih3ikafLmE2IIEqqnLbQfzQAjdLr_kF "00.jpg")

#### 二、hiberfil.sys

hiberfil.sys，這倒底是甚麼碗糕哩？原來，windows7有個功能，叫做「休眠」，他的意思呢、就是讓電腦進入一個休息的狀態，關閉CPU、記憶體、硬碟所有功能，然後將記憶體的所有東西，丟到硬碟裡面，當你要使用時候，電腦只要把記憶體東西從硬碟拿回來，還原工作，就可以快速啟用。不過這麼一來，電腦就必須要硬碟裡面擺放一個空間，好隨時將所有記憶體的東東，給放入硬碟裡面。這就是hiberfil.sys的作用啦！

因此如果你有要用那個休眠功能，或是硬碟空間很吃緊，是可以將這個檔案關閉的！

根據以下步驟關閉並刪除 :

###### (1) 以系統管理員身分執行 [命令提示字元]

![01.jpg](https://lh3.googleusercontent.com/rcmDPTuSrU4MIr3g0vTtDHdCz8s31iR-HUxwVOuKB_9sh0WGHJXf_MgLfwYH10wyxfwZKcqkLQJUkeeF_FAI3buMldPFb06qJv-sbxaV6DbwVle_hJD_hlw9wdo65JNFbHUNChKS "01.jpg")

（點出　開始功能表->附屬應用程式->命令提示字元，按下右鍵，選擇「用系統管理員身分執行」）

###### (2)輸入 powercfg -h off ，按 Enter 鍵即可關閉休眠模式。

![02.jpg](https://lh3.googleusercontent.com/7pNWPc1q89qj9rCzXrttP3hwd4M2_A8fJLVDqvYSSVr1s-mFLgXKJm_rLnOFJLcPJPn_fKKQM-0JFQkwIax7YvGY0zhTt4qBQaTLyPYTdCGyVo3-z8Q17qmCmXwFUV3-DrV-r1oc "02.jpg")

（假如要恢復的話請輸入 powercfg -h on 後按 Enter。）

#### 三、pagefile.sys

pagefile.sys這東西就比較麻煩了，他就是用來配置「虛擬記憶體」的檔案，什麼是虛擬記憶體哩？

這要從頭說起，早年電腦的DRAM記憶體是非常昂貴的，天使記得以前一條128MB的記憶體，竟然就要數千元！因此電腦的記憶體，常常處於不夠用的狀態，以前常見情況是，你只剩不到1GB的記憶體，可是卻要去執行一些吃超過1GB的應用程式，該怎麼辦哩？－就只好跟硬碟借空間了！如前所述，傳統硬碟的容量，都是俗又大碗的～既然如此，就借記憶體一些來用囉～

不過時空轉移，現在DRAM價格屢創新低，以最近的NOVA行情，２GB的DDR2，也不過一個小朋友有找！在這種環境下，配置記憶體超過2GB的比比皆是，甚至索性弄個Windows64位元+4GB以上記憶體！虛擬記憶體派上用處的情況，就變得少啦！如果你又跟筆者一樣，需要硬碟空間，更是可以考慮把虛擬記憶體的配置空間縮小甚至關閉啦！步驟如下：

1. 到 [控制台]、[系統及安全性]、[系統]
1. 點選左邊 [進階系統設定]
1. 出現 [系統內容] 視窗，切換至 [進階] 索引標籤
1. 在 [效能] 群組中，點選 [設定]
1. 出現 [效能選項] 視窗，切換至 [進階] 索引標籤
1. 在 [虛擬記憶體] 群組中，按 [變更]。

![03.jpg](https://lh3.googleusercontent.com/BVG-VcqO8myDBvJwS5xbB-VY761r1CDYzjD8tVEaS70POnHyzBhLdnOhJ-1axbmehfOUWPkJul6fCL_SMihZ4gLigNlbQncODUJIzw5wjXMcZXfsk3oeGrIQU3ycWw5-wssdWuQq "03.jpg")

你可以選擇「自訂大小」，根據你的需求配置虛擬記憶體。也可以勾選 [沒有分頁檔]，按 [確定] 關閉 pagefile.sys 分頁檔。

![04.jpg](https://lh3.googleusercontent.com/MLUuXzoh20tY62NkPL3qpOIsJ45pDSMEPreWMYaMEepF7Uy8BiovEzXYVJgJx3iyRqJnT8M9wGGOG7hvMJBN9NwgCXCd9ESN8qIgCcACIYo4MDsrwJ7S5Hfbu0O4BI7wnW3Xfr5o "04.jpg")

（網路上對於超大記憶體環境是否需要"關閉虛擬記憶體"，也一直有兩派爭論，建議你就選個你喜歡的方式就好！當然你也可以用一些較花記憶體的應用程式或遊戲來測看看囉）

用好這兩項配置，重新開機之後，就可以發現，這兩個檔案，都消失/變小囉！硬碟又多了不少空間出來，是不是比較清爽了呢！