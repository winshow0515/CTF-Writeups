orphan CTF#1
===
目錄
---
* [Baby Bash #01](#baby-bash-01)
* [Baby Bash #02](#baby-bash-02)
* [Flag Generator](#flag-generator)
* [Window](#window)
* [Maze](#maze)
* [Bomb](#bomb)
* [Gemini](#gemini)
* [Baby Bash #03](#baby-bash-03)
* [King Crimson](#king-crimson)


## Baby Bash #01
提示：我是誰？**我在哪？** 我在幹甚麼？

這題就`pwd`
```bash
orphan@box:~$ pwd
/home/flag{wh3r3_4m_I?}
```
Flag: `flag{wh3r3_4m_I?}`

---

## Baby Bash #02
提示：甚麼？ <font color="red">flag</font> 就在我旁邊？
`ls -a` 查看這個資料夾的內容，包括隱形的檔案

```bash
orphan@box:~$ ls -a
./                      .profile            king_crimson
../                     .viminfo            maze/
.ash_history            bomb                treasure_box
.ashrc                  gemini/             window
.flag{I_w1ll_f1nd_y0u}  generate_flag
.local/                 instruction.txt
```
Flag: `flag{I_w1ll_f1nd_y0u}`

---

## Flag Generator
提示：明明就有叫做 <font color="red">generate_flag</font> 的程式卻 gen 不出來，你是不是在演我？

嘗試執行`generate_flag`
```bash
orphan@box:~$ ./generate_flag
Try to generate flag at ./treasure_box/treasure ...
treasure_box is not a directory?
```
把原本的`treasure_box`刪掉自己建一個
再執行一次
就可以在新的`treasure_box/`看到`treasure`了
```bash
orphan@box:~$ rm treasure_box
orphan@box:~$ mkdir treasure_box
orphan@box:~$ ./generate_flag
Try to generate flag at ./treasure_box/treasure ...
Wubba lubba dub dub! I finished!
orphan@box:~$ cat ./treasure_box/treasure
flag{rm_me_mkdir_you}
```
Flag: `flag{rm_me_mkdir_you}`

---

## Window
提示：所以我說這個檔案(<font color="red">window</font>)要怎麼開？

`file window` 發現是它是 .gzip 檔
所以解壓縮它，在解壓縮出來的`flag/`裡面就找到flag了
```bash
orphan@box:~$ tar -zxvf window
orphan@box:~$ cat flag/flag
flag{1s_y0u_0p3n_my_h34rt?}
```
Flag: `flag{1s_y0u_0p3n_my_h34rt?}`

---

## Maze
提示：聽說在迷宮 (<font color="red">maze</font>) 裡面走十步就會遇到寶物喔！
這題就是考`grep`搜尋
```bash
orphan@box:~$ grep flag maze/*/*/*/*/*/*/*/*/*/*/*
maze/r/l/r/l/l/l/r/l/r/r/flag:flag{M1331ng_1n_th3_m4z3}
```
Flag: `flag{M1331ng_1n_th3_m4z3}`

---

## Bomb
提示：你準備好被轟炸了嗎？(<font color="red">bomb</font>)
執行`bomb`會被flag亂碼轟炸，把它丟出去就會出現真正的flag了
```bash
orphan@box:~$ ./bomb > temp
flag{!>_<!}
```
Flag: `flag{!>_<!}`

---

## Gemini
提示：雙子座(<font color="red">gemini</font>)的兩人，真的長的一樣嗎？
diff 兩個檔案在用less慢慢看，就會發現B和A不一樣的那幾行的第一個字元，依序看下來會出現 f l a g { ，完整看完就得到`flag`了
```bash
orphan@box:~$ diff gemini/A gemini/B > temp
orphan@box:~$ less temp
```
Flag: `flag{d1ff_y0u_4nd_m3}`

---

## Baby Bash #03
提示：只要看了怎麼執行就可以有 flag？這麼好喔？
這題的關鍵是不能直接打`../tc/orphan's home/flag` ，也不能用 `'orphan's home'` 或 `'orphans\' home'`
這樣落單的`'`會造成錯誤
改成 `orphan\'s\ home` 或 `"orphan's home"` 就可以了

```
orphan@box:~$ cat instruction.txt
There's an directory under /home/tc named "orphan's home/"
And there's a file named "flag".

Open and read it, you will get the flag.
orphan@box:~$ cat ../tc/"orphan's home"/flag
flag{s3cr3t_f14g_1n_su}
```
Flag: `flag{s3cr3t_f14g_1n_su}`

---

## King Crimson
提示：啊這怎麼關？不要逼我直接關機喔乾！
這是我覺得最難的一題
`king_crimson` 這個檔案一執行就會開始刷 Gold Experience Requiem!，完全不能執行指令
```
Gold Experience Requiem! Can you break the loop???
Gold Experience Requiem! Can you break the loop???
Gold Experience Requiem! Can you break the loop???
```
不管是常見的`Ctrl+C`還是`Ctrl+Z`都停不下來
最後是`Ctrl+\`才成功停下並跳出flag
Flag: `flag{A_Pr0gram_1s_K1ll3d_3_T1m3s}`