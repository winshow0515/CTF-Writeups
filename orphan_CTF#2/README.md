orphan CTF#2
===
目錄
---
* [Rubbish Sorting](#rubbish-sorting)
* [Zzzzzip](#zzzzzip)
* [Amnesia](#amnesia)
* [Debug](#debug)

## Rubbish Sorting
提示：垃圾分類，從你我做起。(如果你分類完垃圾，問一下 <font color="red">./government</font> 看你做得好不好？)

單純的把`trash` `mv` 到`trash_can/`
```bash
orphan@box:~$ mv trash/*.c    trash_can/c/
orphan@box:~$ mv trash/*.cpp  trash_can/cpp/
orphan@box:~$ mv trash/*.tar.gz   trash_can/tar.gz/
orphan@box:~$ mv trash/*.txt  trash_can/txt/
orphan@box:~$ mv trash/*.zip  trash_can/zip/
orphan@box:~$ ./government
flag{Wh4t_4_tr4sh_4r3_y0u?}
```
Flag: `flag{Wh4t_4_tr4sh_4r3_y0u?}`

---

## Zzzzzip
提示：明明用 <font color="red">file flag</font>就是說 <font color="red">zip</font> 啊，啊怎麼不能 <font color="red">unzip</font>？

我不會做，還沒做出來

```bash
orphan@box:~$ 

```
Flag: 

---

## Amnesia
提示：我好像失憶了嗎？我怎麼不記得我打過 <font color="red">flag</font>？

照提示用 `history` 看看，發現一行有用的指令
```bash
orphan@box:~$ history > temp
orphan@box:~$ less history
...
8 cat /home/orphan/s3cr3t/flag
...
orphan@box:~$ cat /home/orphan/s3cr3t/flag
flag{h1st0ry_1s_us3fu1!}
```
Flag: `flag{h1st0ry_1s_us3fu1!}`

---

## Debug
提示：你是 Debug 大師嗎？不是很會 Debug？

用`sed`把`bug`都刪掉就好了
```bash
orphan@box:~$ sed 's/bugs//g; s/BUGS//g; s/bug//g; s/BUG//g' bug_code
flag{d1d_y0u_m1sus3_tr_b3f0r3_ur3_s3d_0r_0th3r_tr1clc?}
```
Flag: `flag{d1d_y0u_m1sus3_tr_b3f0r3_ur3_s3d_0r_0th3r_tr1clc?}`