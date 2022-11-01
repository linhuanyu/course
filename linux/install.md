# Linux 安裝指令 #

## 概念 ##

平常會用 apt 這套套件管理軟體來管理 Linux 上可以安裝的套件，他能夠跟套件庫取得套件列表，包括有哪些套件以及版本號，我們可以下指令安裝套件，以及讓我們的套件更新到最新版。

請注意，安裝指令多半需要 Root 權限，若使用 sudo，要用 sudo xxx 來執行。

## 指令 ##

### 從套件庫取得最新套件列表 ###

```
apt update
```

### 安裝套件 ###

```
apt install [package name]
```

例如安裝 vim 套件

```
apt install vim
```

### 刪除已安裝的套件 ###

```
apt remove [package name]
```

### 將已安裝套件更新到最新版 ###

```
apt upgrade
```

通常會先更新列表 (apt update) 之後才做，這樣才會更新到最新的版本

### 搜尋套件 ###

```
apt search [keyword]
```

常常搜出來的結果都很多，需要導給 less 比較好看

### 查看裝了哪些套件 ###

```
dpkg -l
```

### 增加套件庫來源 ###

套件庫列表放在 /etc/apt/source.list ，會影響能找到的新套件與最新版本，可以使用已下指令來增加來源

```
add-apt-repository '[repository url]'
```

新來源的套件在被我們抓回來的時候，我們的機器會自動以金鑰解密來驗證抓到的套件是否沒有被竄改過，增加金鑰來源可用

```
apt-key adv --keyserver [key from which server] --recv-keys [key name]
```

加入 adv 代表信任加入不做驗證，通常上面這兩個步驟都可以從網路上的安裝教學知道要裝甚麼 repository、裝甚麼 key，所以我們只要知道那是在做甚麼就好。

## 練習 ##

試著參考[網站教學](https://ubunlog.com/zh-TW/lenguaje-de-programacion-r-instalacion-ubuntu-20-04/)自己裝一次 R 語言，並且理解裡面每個步驟的意義

