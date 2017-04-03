長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(rvest)
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
##read_html
##html_nodes
##html_text

nba<-list()
library(rvest)
for(i in 4642:4647){
PTT<-paste("https://www.ptt.cc/bbs/NBA/index",i,".html",sep="" )
PTTContent<-read_html(PTT)
post_title <- PTTContent %>% 
html_nodes(".title") %>% 
html_text() 
num <- PTTContent %>% 
html_nodes(".nrec") %>% 
html_text()
name <- PTTContent %>% 
html_nodes(".author") %>% 
html_text()
dfa<-data.frame(Title = post_title,PushNum=num, Author=name)
nba[[i]]<-dfa
}
data<-rbind(nba[[4642]],nba[[4643]],nba[[4644]],nba[[4645]],nba[[4646]],nba[[4647]])
```

爬蟲結果呈現
------------

``` r
knitr::kable(data)
```

| Title                                                | PushNum | Author       |
|:-----------------------------------------------------|:--------|:-------------|
| \[專欄\] Nash專訪：現在已幾乎無純控衛，對Curry       | 爆      | encorek01231 |
| (本文已被刪除) \[dro001\]                            | 23      | -            |
| \[新聞\] Nash談養生　「季後賽總是很累」              | 20      | zzzz8931     |
| \[情報\] ★今日排名(2017.04.01)★                      | 2       | Rambo        |
| Re: \[討論\] Kansas NCAA Championship 2008           | 9       | nwohippo     |
| \[情報\] NBA Standings(2017.04.01)                   | 36      | kadasaki     |
| (本文已被刪除) \[WangRW\]                            | XX      | -            |
| \[心得\] 詹皇今年真的太操了                          | 57      | checktime    |
| \[花邊\] Tracy McGrady 進入名人堂                    | 爆      | thnlkj0665   |
| \[專欄\] MVP該頒給龜龜的理由… LYS                    | X7      | dora1024     |
| Re: \[專欄\] MVP該頒給龜龜的理由… LYS                | 28      | dragon803    |
| \[討論\] 林書豪 轉型?                                | 3       | godroid      |
| Re: \[專欄\] MVP該頒給龜龜的理由… LYS                | 17      | btm978952    |
| \[情報\] MVP Award Shares 生涯累計                   | 36      | checktime    |
| Re: \[專欄\] MVP該頒給龜龜的理由… LYS                | 16      | sscck5       |
| \[Live\] 湖人 @ 快艇                                 | 10      | Rambo        |
| 龜龜吃藥～                                           | X4      | ixamaron12   |
| \[Live\] 老鷹 @ 公牛                                 | 2       | Rambo        |
| \[Live\] 魔術 @ 籃網                                 | 爆      | Rambo        |
| \[NBA\] 看板 選情報導                                | 7       | \[馬路探子\] |
| \[BOX \] Lakers 104:115 Clippers 數據                | 32      | Rambo        |
| \[新聞\] 和威少從朋友變仇人　杜蘭特：媒體害的        | 37      | JAL96        |
| (本文已被刪除) \[jay0601zzz\]                        | 6       | -            |
| \[BOX \] Hawks 104:106 Bulls 數據                    | 47      | Rambo        |
| \[Live\] 國王 @ 灰狼                                 | 19      | Rambo        |
| \[BOX \] Magic 111:121 Nets 數據                     | 79      | Rambo        |
| Re: \[BOX \] Hawks 104:106 Bulls 數據                | 46      | ericl1234567 |
| \[情報\] 公鹿計畫簽下後衛Gary Payton II              | 22      | Wall62       |
| Re: \[外絮\] 勒布朗IG                                | 82      | bigDwinsch   |
| \[Live\] 太陽 @ 拓荒者                               | 6       | Rambo        |
| Re: \[BOX \] Hawks 104:106 Bulls 數據                | 5       | phoenix286   |
| \[新聞\] 入選名人堂喜極而泣 麥葛雷迪：非常榮譽       | 爆      | DantesChen   |
| \[情報\] 矮湯:他們以為我參加選秀是愚人節玩笑         | 43      | bigDwinsch   |
| \[BOX \] Kings 123:117 Timberwolves 數據             | 78      | Rambo        |
| (本文已被刪除) \[luvstarrysky\]                      |         | -            |
| Re: \[討論\] 老大的帶隊能力其實很強吧                | 12      | alex26       |
| \[新聞\] 生涯第400場出賽 林書豪8助攻率籃網止敗       | 7       | luvstarrysky |
| \[討論\] kobe入NBA後 有刻意學喬丹動作嗎?             | 65      | omare        |
| \[新聞\] 林書豪表現全能，籃網主場拆穿魔術止敗        | 32      | SuperSg      |
| \[BOX \] Suns 117:130 Blazers 數據                   | 26      | Rambo        |
| Re: \[新聞\] 林書豪表現全能，籃網主場拆穿魔術止敗    | 22      | dragon803    |
| \[討論\] 籃網with書豪 vs 騎士without詹皇             | 28      | lebron860330 |
| \[花邊\] 國王官推發C羅雕像圖描述贏球後的心情         | 31      | bigDwinsch   |
| \[情報\] TODAY                                       | 11      | Ivers        |
| \[討論\] Lebron 生涯中最經典的比賽是哪一戰           | 爆      | ericl1234567 |
| \[討論\] Chris Webber沒進名人堂?                     | 38      | Wall62       |
| (本文已被刪除) \[MrSatan\]                           | 76      | -            |
| \[花邊\] Kobe祝福T-Mac：兄弟，這是你理所應得的       | 55      | lovea        |
| Re: \[新聞\] 入選名人堂喜極而泣 麥葛雷迪：非常榮譽   |         | MaligB       |
| Re: \[討論\] Lebron 生涯中最經典的比賽是哪一戰       | X1      | Mingming1258 |
| \[花邊\] 哈登控被打 格林回應：他先捏我               | 52      | adam7148     |
| (本文已被刪除) \[Greatness\]                         |         | -            |
| (本文已被刪除) \[MASAMII\]                           |         | -            |
| (本文已被刪除) \[MrSatan\]                           | 63      | -            |
| \[討論\] 今年的MVP爭奪戰是不是有點像2007年           | 23      | dro001       |
| \[討論\] 最強二哥                                    | 37      | FeiWenKing   |
| Re: \[專欄\] MVP該頒給龜龜的理由… LYS                |         | KDimitrov313 |
| \[新聞\] 快艇添傷兵 小瑞佛斯例行賽報銷               | 39      | Gotham       |
| \[討論\] 公牛怎麼復活了                              | 52      | waiting0212  |
| \[討論\] 求助NBA League Pass 無法登入                | 1       | alex01       |
| \[新聞\] 拓荒者拉尾盤 里拉德射日助隊六連勝           | 5       | zzzz8931     |
| \[外絮\] Stephenson將自己回歸溜馬比喻成Jordan重返NBA | 20      | juniorpenny  |
| \[討論\] 現役球員 進名人堂的機率                     | 爆      | checktime    |
| Re: \[討論\] 公牛怎麼復活了                          | 10      | david1003    |
| Re: \[專欄\] MVP該頒給龜龜的理由… LYS                |         | leyi12       |
| (本文已被刪除) \[overkill0802\]                      |         | -            |
| \[Live\] 超賽 @ 尼克                                 | 9       | Rambo        |
| \[情報\] 看看誰最會填格子NBA Efficiency 25+          | 13      | checktime    |
| (本文已被刪除) \[phcebus\]                           | 4       | -            |
| \[情報\] Derrick Rose半月板撕裂                      | 爆      | dragon803    |
| Re: \[討論\] 現役球員 進名人堂的機率                 | 6       | nuturewind   |
| Re: \[情報\] Derrick Rose半月板撕裂                  | 28      | dragon803    |
| Re: \[討論\] 勒布朗到底強在哪裡？                    | 73      | as999        |
| Re: \[討論\] Chris Webber沒進名人堂?                 | 6       | vogue38      |
| \[Live\] 黃蜂 @ 雷霆                                 | 24      | Rambo        |
| \[Live\] 灰熊 @ 湖人                                 | 4       | Rambo        |
| \[Live\] 小牛 @ 公鹿                                 | 1       | Rambo        |
| \[Live\] 爵士 @ 馬刺                                 | 62      | Rambo        |
| \[BOX \] Celtics 110:94 Knicks 數據                  | 19      | Rambo        |
| \[BOX \] Hornets 113:101 Thunder 數據                | 54      | Rambo        |
| \[Live\] 老鷹 @ 籃網                                 | 爆      | Rambo        |
| \[Live\] 金塊 @ 熱火                                 | 2       | Rambo        |
| \[Live\] 溜馬 @ 騎士                                 | 爆      | Rambo        |
| \[新聞\] 理財顧問認罪 承認詐騙鄧肯600萬美元          | X2      | jojoii82     |
| \[BOX \] Mavericks 109:105 Bucks 數據                | 11      | Rambo        |
| \[BOX \] Grizzlies 103:108 Lakers 數據               | 26      | Rambo        |
| \[BOX \] Jazz 103:109 Spurs 數據                     | 34      | Rambo        |
| \[Live\] 巫師 @ 勇士                                 | 99      | Rambo        |
| \[BOX \] Sixers 105:113 Raptors 數據                 | 7       | Rambo        |
| \[BOX \] Bulls 117:110 Pelicans 數據                 | 46      | Rambo        |
| \[Live\] 火箭 @ 太陽                                 | 58      | Rambo        |
| \[BOX \] Hawks 82:91 Nets 數據                       | 84      | Rambo        |
| \[BOX \] Nuggets 116:113 Heat 數據                   | 12      | Rambo        |
| \[情報\] 今日傷兵&簽約消息(4/3)                      | 28      | jc0209       |
| \[新聞\] 林書豪15分6助攻 籃網勝老鷹本季2度2連勝      | 59      | jimmy5680    |
| \[討論\] KD在勇士定位是不是有點尷尬？                | 5       | signm        |
| \[BOX \] Pacers 130:135 Cavaliers 數據               | 99      | Rambo        |
| \[討論\] Monta Ellis為什麼變得這麼沒關注度           | 42      | go40404      |
| \[新聞\] 羅斯再因傷報銷 隊友、教頭都遺憾             | 53      | Gotham       |
| \[BOX \] Wizards 115:139 Warriors 數據               | 爆      | Rambo        |
| \[新聞\] 詹皇41分大三元 騎士二度延長打退溜馬         | 15      | james008     |
| \[情報\] ESPN的NBA管理階層排名                       | 58      | jimmy5680    |
| \[情報\] Steph Curry 連續兩季三分進球數突破300顆     | 爆      | thnlkj0665   |
| (本文已被刪除) \[Tmmontal\]                          | 1       | -            |
| \[外絮\] 林書豪 ig                                   | 23      | bigDwinsch   |
| (本文已被刪除) \[KyrieIrving1\]                      | 9       | -            |
| \[BOX \] Rockets 123:116 Suns 數據                   | 76      | Rambo        |
| \[討論\] T-Mac的打板灌籃數據算法                     | 32      | s111228s     |
| \[花邊\] 詹姆斯連續得分10+場次追平賈霸 歷史第2       | 40      | james008     |
| \[討論\] 大家是不想守還是守不住科鋁啊                | X4      | TUG5566      |
| (本文已被刪除) \[brandon0415\]                       | 1       | -            |
| \[討論\] 全盛的踢妹切入有比LBJ強嗎 ??                | 69      | osee         |
| Re: \[討論\] 現役球員 進名人堂的機率                 | 21      | carmeloeat   |
| Re: \[花邊\] 詹姆斯連續得分10+場次追平賈霸 歷史第2   | 14      | avrild12     |
| \[討論\] 刷數據輸球 跟 大三元勝率 的關係             |         | AHEAD099     |
| \[新聞\]林書豪一箭穿心助攻鎖勝 老鷹只能失望稱臣      | 12      | sinana       |
| \[閒聊\] Sam Dekker 左手骨折                         | 13      | dragon803    |
| (本文已被刪除) \[japanx\]                            |         | -            |
| \[新聞\] 馬刺6人「養生」 雷納德25分領軍退爵士        | 8       | zzzz8931     |
| \[新聞\] 3月威少9飆大三元　本季場均大三元9成99會成功 | 31      | sundle       |

解釋爬蟲結果
------------

``` r
dim(data)
```

    ## [1] 120   3

先顯示列 後顯示行 共有120篇文章標題

``` r
table(data$Author)
```

    ## 
    ##            -   [馬路探子]    btm978952    checktime     dora1024 
    ##           14            1            1            4            1 
    ##    dragon803 encorek01231      godroid   ixamaron12     kadasaki 
    ##            5            1            1            1            1 
    ##     nwohippo        Rambo       sscck5   thnlkj0665     zzzz8931 
    ##            1           33            1            2            3 
    ##       alex26   bigDwinsch   DantesChen ericl1234567        JAL96 
    ##            1            4            1            2            1 
    ## luvstarrysky        omare   phoenix286      SuperSg       Wall62 
    ##            1            1            1            1            2 
    ##     adam7148       alex01       dro001   FeiWenKing       Gotham 
    ##            1            1            1            1            2 
    ##        Ivers KDimitrov313 lebron860330        lovea       MaligB 
    ##            1            1            1            1            1 
    ## Mingming1258  waiting0212        as999    david1003  juniorpenny 
    ##            1            1            1            1            1 
    ##       leyi12   nuturewind      vogue38      go40404       jc0209 
    ##            1            1            1            1            1 
    ##    jimmy5680     jojoii82        signm     AHEAD099     avrild12 
    ##            2            1            1            1            1 
    ##   carmeloeat     james008         osee     s111228s       sinana 
    ##            1            2            1            1            1 
    ##       sundle      TUG5566 
    ##            1            1

由資料可知 Rambo 的文章數最多(有33個)

看了這些文章的標題 每個標題前面都有\[ \]呢
