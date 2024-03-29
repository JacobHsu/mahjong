# mahjong

[打麻將的數學冷知識（二）：如何一眼就知道胡牌了沒](https://www.thenewslens.com/article/100657)  


**先把可能的對子拿出來，然後最小牌能拿走一刻即拿走一刻，否則試著拿走一順**  


一副牌P，若把一個**對子**拿掉後，假設此時數字最小的牌是x， 
若x的張數是3張以上，則拿掉**一刻**（3張x）後，剩下牌為Q。  
否則拿掉**一順**（x, x+1, x+2）之後，剩下的牌為Q。（若無法拿，則P沒胡）  

則「P胡」若且唯若「Q胡」。 （英語：if and only if，iff）


#### 例1：判斷P = 33345678是否胡牌？

P中唯一能當眼睛的地方，就是3，因此把33一對拿掉，變成Q=345678，Q是胡牌型，所以P也是。 [33]345678 = [33][345]678

#### 例2：判斷P = 55666777889是否胡牌？

若拿55，剩下666777889；最小的6有三張，直接拿掉666，剩777889，再拿777，得889，所以沒胡。 [55][666][777]889  
若拿66，剩下556777889；最小的是兩張5，但沒有辦法拿掉兩個567了，所以沒胡。55[66]6777889  
若拿77，剩下556667889；最小的是兩張5，但沒有辦法拿掉兩個567了，所以沒胡。55666[77]7889  

各種能拿掉對子的方式都試過，都無法胡，所以P不是胡牌型。


### 判斷聽牌

只要試著加入任何一張牌，再嘗試拿掉各種可能的對，利用定理1判斷是否可以胡牌，即可得知聽哪些牌，僅需要O（n3）的時間。

例3：判斷3456667888聽什麼牌？

加入1，剩13開頭，沒胡  13456667888 = 13[456]6[678]88  
加入2  

2345[66]67888 拿掉66，剩234567888 = [234][567][888]，胡！  
234566678[88] 拿掉88，剩234566678=[234]5[66]678 ，沒胡  

加入3

[33]456667888 拿掉33，剩456667888 = [456]667[888]，沒胡  
3345[66]67888 拿掉66，334[567][888]，剩334開頭，沒胡  
334566678[88] 拿掉88，334[566][678]，剩334開頭，沒胡  



# 眼睛 對子 位置的判斷

一副牌，依一四七、二五八、三六九分成三堆，每堆的張數除以三的餘數必有一個與另兩個不同，則眼睛就在不同的那堆裡。

先只看同個花色，把所有的牌分成3堆：「一四七」堆，「二五八」堆，「三六九」堆，接著觀察每堆的張數。

胡牌的話，要抓成三個三個一組的搭子再搭配一對眼睛，搭子若是「順」，貢獻這三堆的個數必同時都加1；搭子若是「刻」，則某一堆會加3。

因此，若先不看眼睛，這三堆的牌數除以3的餘數應該要相等。再加上眼睛，就只會讓某一堆個數與其他兩堆不同。

例：判斷　23333444455556666是否胡牌呢？
一四七有4張，除以3餘1
二五八有5張，除以3餘2
三六九有8張，除以3餘2

所以眼睛只可能是44，
接著把44拿掉，23333[44]4455556666，剩下 233334455556666
然後利用定理1依序去拿，得到234、333、456、555、666，所以是胡牌型。


# 十六張麻將

[平胡](https://zh.wikipedia.org/wiki/%E5%B9%B3%E5%92%8C_(%E9%BA%BB%E5%B0%86))
