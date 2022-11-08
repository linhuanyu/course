# Linux 常用指令 #

### 列出檔案 ###

```
ls
```

若想要看到詳細資料，例如擁有者、權限、大小，則需要用

```
ls -l
```

可以看到檔案內容如下

```
drwxr-xr-x 1 root root        512 Aug 20  2021 vulkan
-rw-r--r-- 1 root root       4942 Jul 25  2019 wgetrc
-rw-r--r-- 1 root root        642 Sep 24  2019 xattr.conf
```

* 其中 d 代表目錄
* 三組 rwx 是使用權限，分別代表 Read(r), Write(w), eXecute(X)
* 權限有三組，分別代表自己的權限、同一群組的權限、其他人的權限
* 兩個 root 第一個是擁有者帳號，第二個是所屬 group
* 後面的數字是檔案大小

### 改變路徑 ###

```
cd [目標路徑]
```

可以使用絕對路徑

```
cd /home/linhuanyu/
```

可以用相對路徑

```
cd linhuanyu/data
cd .
cd ../courseuser

```

自己的 home 有特殊寫法

```
cd ~/data
```

若要回到自己的 home 目錄，可以直接用

```
cd
```

### 熱鍵小訣竅 ###

* 按 ↑ 可以叫出之前執行的指令
* 打路徑或打指令的時候，按 tab 可以讓系統幫你補完輸入的字

## 練習 ##

看看一般系統的根目錄下面有哪些目錄

### 建立目錄 ###

```
mkdir program
```

### 刪除目錄 ###

```
rmdir program
```

請注意，目錄裡面有東西就不能用 rmdir 來刪除

### 複製檔案 ###

```
cp [目標檔案] [目標路徑]
```

例如

```
cp test.r ~/program/
```

如果要複製整個目錄，需要用 -r 的參數

```
cp -r program ~/
```

### 移動檔案 ###

```
mv [目標檔案] [目標路徑]
```

例如

```
mv test.r ~/program/
```

系統裡沒有重新命名的指令，但可以用移動來完成

```
mv test.r first_program.r
```

### 刪除檔案 ###

```
rm test.r
```

如果要把目錄連同裡面的東西都刪掉，也不要每個檔案問，可以用

```
rm -rf ~/program
```

### 檔名小訣竅 ###

如果想要一次刪除、複製多個特定種類的檔案，可以使用萬用符號，例如

```
rm *.r
```

這代表刪除全部最後是 .r 的檔案

### 指令輸出導向 ###

把指令輸入的結果導入檔案，並且以覆蓋的方式寫檔

```
ls > list.txt
```

若想要把結果接在後面而不是覆蓋，要用

```
ls >> list.txt
```

把一個指令的輸出導入另一個指令的輸入

```
ls | less
```

### 長文件閱讀器 ###

可以將長輸入導入以方便閱讀

```
ls -la /bin/ | less
```

這時候會得到類似以下的畫面

```
-rwxr-xr-x 1 root   root        7415 May  1  2021 add-apt-repository
-rwxr-xr-x 1 root   root       30952 Jul 21  2020 addpart
lrwxrwxrwx 1 root   root          26 Jan 21  2021 addr2line -> x86_64-linux-gnu-addr2line
-rwxr-xr-x 1 root   root        2558 Dec  5  2019 apport-bug
-rwxr-xr-x 1 root   root       13367 May 18  2021 apport-cli
lrwxrwxrwx 1 root   root          10 May 18  2021 apport-collect -> apport-bug
-rwxr-xr-x 1 root   root        2068 May 18  2021 apport-unpack
-rwxr-xr-x 1 root   root       14648 Feb 29  2020 appres
lrwxrwxrwx 1 root   root           6 Feb 26  2020 apropos -> whatis
-rwxr-xr-x 1 root   root       18824 Jun 15  2021 apt
lrwxrwxrwx 1 root   root          18 May  1  2021 apt-add-repository -> add-apt-repository
-rwxr-xr-x 1 root   root       88536 Jun 15  2021 apt-cache
:                                                                                        
```

* 按 ↑ ↓ 按鍵可以上捲下捲
* 按 / 可以輸入關鍵字搜尋
* 按 q 可以跳出

也可以直接用閱讀器開啟檔案閱讀，平常會用 vim，但如果檔案很長且不需要改動，用 less 比較順

```
less /etc/passwd
```

### 清掉螢幕 ###

```
clear
```

### 線上手冊 ###

如果想要了解更多指令的說明，可以使用 man

```
man ls
```

## 練習 ##

* 在 home 目錄裡面建立一個檔案叫做 test.r，內容是

```
vec = c(1, 2, 4)
vec = vec + 1
vec
```

* 在 home 目錄建立一個目錄 backup
* 把剛剛的程式檔複製到裡面去
* 確定複製成功
* 把 home 目錄的程式檔刪除
* 把 backup 連裡面的檔案一起刪除