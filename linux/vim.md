# 學會使用 vim #

vim 是 linux 上最多人使用的編輯器，在甚麼都沒裝的 linux 系統，也會預設裝一個簡化版的 vi，因此，無論如何都需要學會怎麼用 vim 編輯文件。

## 指令 ##

如果發現沒有安裝 vim，可以用 apt install vim 來安裝，裝完直接就可以用了。

### 進入 vim ###

進入一個文件編輯，使用

```
vim [file name]
```

檔名可以是已經存在的檔案，若是未存在的檔案，則會在存檔的時候建一個出來。

### vim 的三種模式 ###

vim 有三種不同的模式

* Command mode：剛進入 vim 就是 Command mode，這個模式不能打字，但是能做刪除剪下貼上等動作，也可以進入 Last line mode
* Last line mode：在這個模式可以做對於全檔的操作，例如存檔、退出
* Insert mode：進入 Insert mode 就可以打字了

### (in command mode) 進入 insert mode ###

如果要在游標的那一格變成 Insert mode，可以按

```
i
```

如果要變成 Insert mode，並且跳到下一格，則按

```
a
```

### (in insert mode) 退回 command mode ###

```
Esc
```

### (in command mode) 剪下 ###

```
x
```

### (in command mode) 貼上 ###

```
p
```

### (in command mode) 刪除整行 ###

```
dd
```

### (in command mode) 選取 ###

```
v
```

按了以後會進入選取模式，可以用方向鍵控制左右選取，在選取模式按剪下就可以把選取的範圍全部都剪下，再來也可以用貼上指令貼在別的地方。若要選取整行可用

```
V
```

### (in command mode) 替換 ###

```
r
```

按了之後會等你再輸入一個字，會把游標上的那個字換成新輸入的字，若選取多個字再替換，會全部替換成同一個字。

### (in command mode) 複製 ###

```
y
```

### (in command mode) 回上一步 ###

```
u
```

undo 回上一個動作

### (in command mode) 搜尋 ###

```
/
```

按下之後會跑到編輯器底部，輸入要搜尋的字按 Enter 就可以搜尋，若要搜下一個，再按

```
/ + Enter
```

### (in command mode) 進入 last line mode ###

```
:
```

按下之後游標會跑到編輯器最下方，再來就可以輸入指令了

### (in last line mode) 離開 ###

```
q + Enter
```

注意，如果有修改過，不能直接離開，如果要不存檔強制離開，可以用

```
q! + Enter
```

### (in last line mode) 存檔 ###

```
w + Enter
```

### (in last line mode) 存檔離開 ###

```
wq + Enter
```

### (in last line mode) 跳到指定行數 ###

```
[number] + Enter
```

例如要跳到 100 行，就輸入 100 然後按 Enter，如果要到最後一行，可以用

```
$ + Enter
```

### (in last line mode) 編輯別的檔案 ###

```
E + Enter
```

會進入檔案選擇介面，選擇檔案按 Enter 就會進入編輯

## 練習 ##

試著建立一個 test.r 的檔案，在裡面輸入程式

```
str = 'Hello R language'
print(str)
```