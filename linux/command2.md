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