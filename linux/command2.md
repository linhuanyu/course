# Linux 常用指令二 #

### 打包檔案 ###

把檔案壓縮成一包

```
tar -zcvf [壓縮檔名] [要壓縮的目錄]
```

如果不是壓縮目前目錄下的目錄，可以指定起始目錄，例如

```
tar -C /etc -zcvf init.tgz init.d
```

上面指令跟下面指令結果是不同的，下面壓縮檔會包含最後指定的完整目錄

```
tar -zcvf init.tgz /etc/init.d
```

若要解壓縮，可以用

```
tar -zxvf [壓縮檔名]
```

若要解壓縮到指定目錄，一樣可用 -C

```
tar -C ./backup -zxvf init.tgz
```

### 練習 ###

* 將 /etc/xml	裡的檔案包裝成壓縮檔 xml.tgz，注意，壓縮檔裡面不要包含目錄
* 在 home 目錄下建立 backup 目錄
* 把壓縮的檔案解到 backup 目錄裡

### 複製檔案 ###

將本機的檔案複製到遠端的機器裏面去，加 -P 可以指定特殊 port

```
scp -P 65535 init.tgz courseuser@test.linhuanyu.life:~/
```

也可以把遠端的檔案複製回本機端

```
scp -P 65535 courseuser@test.linhuanyu.life:~/init.tgz ./
```

也可以使用 ftp 上傳或下載檔案，選擇 sftp，輸入網址、帳號、密碼、port，就可以連入操作了

### 取得網路上的檔案 ###

可以用瀏覽器連得到的檔案、圖片，都可以用指令抓到本機端，下面例子是抓取 google logo 圖檔

```
wget https://www.google.com.tw/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png
```

### screen ###

screen 是個需要安裝的工具，讓使用者可以在 linux 中開出同時執行程序，就可以同時做多件事，例如一邊在抓大檔，還能用另一個 screen 寫程式，而且 screen 有一個特殊的特性，他在目前的連線斷線的情況下，還會繼續執行，在安裝完 screen 的電腦，要開出一個 screen 可以輸入

```
screen
```

多輸入一次就多開 screen，要跳到指定的 screen

```
Ctrl + a [0-9]
```

第一個開出的 screen 是 0 號，用 Ctrl + a 0 就可以跳到。若要在最後使用的兩個 screen 間來回跳，用

```
Ctrl + a Ctrl + a
```

關掉 screen 用

```
exit
```

### 管理員權限 ###

若要使用管理員的權限執行指令，而不使用 root 登入，則可以安裝 sudo，則可以用 sudo 指令讓原本的指令變成管理者權限在執行，例如要修改系統檔案

```
sudo vim /etc/group
```

若要讓一個使用者可以使用 sudo 指令，可以修改 /etc/group，把帳號加進 sudo 的群組，就可以使用了

```
in /etc/group
sudo:x:27:ubuntu,linhuanyu,courseuser
```

### 修改檔案所有權、權限 ###

若要修改一個檔案的所有人或所屬群組，可以用以下指令，第一個是所有人，第二個是所屬群組

```
chown courseuser:courseuser init.tgz
```

若要同時指定整個目錄和下層目錄，可以用 -R

```
chown -R courseuser:courseuser ./
```

若要修改檔案的權限，可以用

```
chmod 644 init.tgz
```

這邊的 644 三個數字分別代表自己的權限、同群組的權限、其他人的權限，數字要用二進位來看，例如 6 代表 110，對照權限 rwx，則可以看出這是指定可以 read，可以 write，不可以 execute。
同樣的，整批修改內部所有目錄與檔案權限可以用 -R

```
chmod -R 644 ./
```

### 關機與重開 ###

關機可用

```
sudo shutdown +1
```

其中 +1 代表 1 分鐘之後關機，若立即關機則用 +0。重開機可用

```
sudo reboot +0
```
