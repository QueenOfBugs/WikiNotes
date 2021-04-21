[TOC]
# *linuxå¥é¨å°è¿é¶*

> æç¨è§é¢ä½¿ç¨çæ¯CentOS åç³»ç»è½¯ä»¶åè·¯å¾ææä¸åï¼ä¸è¦ç§æ¬

## ç®å½æä½

### åå»ºåå é¤
* åå»ºç®å½
    ```
  mkdir ./a
  mkdir a
  å½åç®å½ä¸åå»ºç®å½(æä»¶å¤¹)a
  mkdir /a
  æ ¹ç®å½ä¸åå»ºç®å½a
  mkdir -p a/b/c/d/
  åå»ºå¤çº§ç®å½
    ```
* å é¤ç®å½
    ```
  rmdir a
  åªè½å é¤éç©ºç®å½

  rm -r a
  å é¤ç®å½a(ä¸ç®¡æ¯å¦éç©º)è¯¾ç¨æ¼ç¤ºä¼ææç¤ºæ¯å¦å é¤å­ç®å½ï¼ä½å®éæä½manjaroä¸å¹¶æ²¡ææç¤ºï¼ç´æ¥å é¤äº
  rm -r -f a
  rm -rf a
  å é¤ç®å½aå¹¶ä¸ä¼æ¾ç¤ºæç¤ºä¿¡æ¯
  -rï¼-R --recursive
  -f,--force
    ```

### å¤å¶åç§»å¨
* å¤å¶
    ```
  cp -copy files and directories
  cp [options] SOURCE DEST
  cp a.txt /
  å°a.txtå¤å¶å°æ ¹ç®å½
  å¸¸ç¨éé¡¹
  -r,-R --å¤å¶æºç®å½ä¸çæææä»¶
  -v --æ¾ç¤ºå¤å¶è¿ç¨
  -p --ä¿çæä»¶æ¶é´æ³åæé
  -a --ä¿çæä»¶æéï¼ææèï¼æ¶é´ç­å¨é¨å¤å¶
    ```
* ç§»å¨&æ¹å
    ```
  mv -move(rename) files
  mv [options] SOURCE DEST
  mv a.txt /b.txt
  å°a.txt ç§»å¨å°æ ¹ç®å½ä¸éå½åä¸ºb.txt

    ```
### æ¥çææ¬

```
cat filename--æ¥çæä»¶ææåå®¹
head -number filename æ¥çæä»¶å¤´é¨åå®¹(ånumberè¡)
tail -number filename æ¥çæä»¶å°¾é¨åå®¹(ånumberè¡)
  tail å¸¸ç¨åæ° -f æä»¶åå®¹æ´æ°åï¼æ¾ç¤ºä¿¡æ¯åæ­¥æ´æ°ï¼å¯ä»¥å®æ¶è§å¯æ¥å¿æä»¶
  
wc ç»è®¡æä»¶åå®¹ä¿¡æ¯
less 
more ä¹æ¯æ¥çæä»¶çå½ä»¤
```

## æåä¸åç¼©è§£åç¼©

```
          tar cf etc_backup.tar /etc
          æå /etcç®å½å° å½åç®å½çetc_backup.tar
    ls -lh etc_backup.tar
         æ¥çæä»¶çè¯¦ç»ä¿¡æ¯ -hæ¾ç¤ºæä»¶å¤§å°
  
          æåå¹¶åç¼©--taréæäºåç¼©å½ä»¤
          tar cjf etc.tar.bz2 /etc
          tar xf etc_backup.tar -C /home/
          tar xzf etc.tar.gz 
          tar xjf etc.tar.bz2
          åæ°
          c æå
          x è§£å
          f æå®æä½ç±»åä¸ºæä»¶ 
          -C,---directory=DIR
 
          .tar.bz2 ç¼©å.tbz2 
          .tar.gz ç¼©å .tgz
```
## vim
### vimä½¿ç¨
æå¼vim: 
```bash
vim
```
æå¥½çvimå¥é¨æç¨å°±æ¯èªå¸¦çvimtutor

åç§æ¨¡å¼ï¼NormalãInsertãVisualãCommand

æå¼vimæ¯æ­£å¸¸æ¨¡å¼ï¼åæ¢æ¨¡å¼é½æ¯å¨æ­£å¸¸æ¨¡å¼ä¸çï¼æä¸<kbd>ESC</kbd>è¿åå°æ­£å¸¸æ¨¡å¼

å¨æ­£å¸¸æ¨¡å¼ä¸:
* æä¸A,a,O,o,I,i,è¿å¥æå¥æ¨¡å¼
* æ:è¿å¥å½ä»¤è¡æ¨¡å¼
* æ<kbd>v</kbd>,<kbd>V</kbd>,<kbd>Ctrl</kbd>+<kbd>v</kbd>è¿å¥å¯è§æ¨¡å¼

æ­£å¸¸æ¨¡å¼

d åªå

y å¤å¶yank

u æ¤éï¼å¤æ¬¡æuæ¤éå¤æ¬¡

U æ¤éå½åè¡å°æåä¸æ¬¡ä¿å­

CTRL+R éåæ¤éçæä»¤(åæ¶uåUçæ¤é)

x å é¤æå®å­ç¬¦

r æ¿æ¢æå®å­ç¬¦ 

num G ç§»å¨å°ç¬¬numè¡

G ç§»å¨åæ å°æåä¸è¡

gg ç§»å¨å°ç¬¬ä¸è¡

$ ç§»å¨å°å½åè¡çå¼å¤´

**å½ä»¤è¡æ¨¡å¼**

w ä¿å­å½ä»¤ w ~/a.txtä¿å­å½åæä»¶å°a.txt

! command å¯æ§è¡å¤é¨å½ä»¤(cat cd ç­)

/text åä¸æ¥æ¾text,ænæ¥æ¾ä¸ä¸ä¸ªï¼Nååæ¥æ¾
?text åä¸æ¥æ¾text,næ¥æ¾ä¸ä¸ä¸ªï¼Nååæ¥æ¾

s/old/new

%s/old/new/g å¨å±æ¿æ¢

%s/old/new/gc å¨å±æ¿æ¢å¹¶ç¡®è®¤æ¯ä¸æ¬¡æ¿æ¢

2,5s/old/new/g æ¿æ¢ç¬¬äºè¡åç¬¬äºè¡ä¹é´çææ¬

**å¯è§æ¨¡å¼**

v å­ç¬¦å¯ä½¿æ¨¡å¼

V è¡å¯è§æ¨¡å¼

<kbd>Ctrl</kbd>+<kbd>v</kbd> åå¯è§æ¨¡å¼

æIæå¥ï¼ä¸¤æ¬¡<kbd>ESC</kbd>æ¹éæå¥ï¼då é¤

### vim éç½®
**.vimrcéçç­å·ä¸è¦åå¼å a=bæ¯å¯¹çï¼a = bå°±å¯è½æ¯éç**

```
#é«äº®æ¥æ¾
set hlsearch 
set nohlsearch
#è¡å·
set nu
set nonu


## äº¤æ¢æä»¶
## vim -r æ¥çå½åç®å½ä¸ææswpæä»¶
## vim -r filename æ¥æ¢å¤æä»¶ï¼ç¶ååç¨rm å é¤swpæä»¶

#ä¸äº§çäº¤æ¢æä»¶
#set noswapfile
#è®¾ç½®23000æ¯«ç§æè400å­ç¬¦ä¿å­ä¸æ¬¡ï¼é»è®¤æ¯4000ms(4s)æ200å­ç¬¦ä¿å­ä¸æ¬¡ï¼è¥updatecount=0,é£ä¹å°ä¸ä¼ä¿å­äº¤æ¢æä»¶
set updatetime=23000
set updatecount=400
#äº¤æ¢æä»¶ä¿å­çç®å½
#set directory=/tmp
#è®¾ç½®äº¤æ¢æä»¶ä¿å­å°å½åç®å½
set directory=./
#è®¾ç½®ä¿å­ç®å½ä¸ºä¸ä¸ªç®å½åè¡¨ï¼æä»¶ä¼åè¢«å­æ¾å¨ç¬¬ä¸ä¸ªç®å½
#set directory=./,/tmp
#set directory = .  vimè¡¨ç¤ºä¸è½è¯å«(.)ä¸ºå½åç®å½ï¼=.å¯ä»¥è¯å«
```


## ç¨æ·åç¨æ·ç»

### ç¨æ·
```
root è¶çº§ç®¡çåç¨æ·ãå¶ä»å°±æ¯æ®éç¨æ·
useradd --æ°å»ºç¨æ·
userdel --å é¤ç¨æ·
passwd --ä¿®æ¹ç¨æ·å¯ç 
usermod --ä¿®æ¹ç¨æ·å±æ§
chage --ä¿®æ¹ç¨æ·å±æ§

useradd user1
id user1  æ¥çuidï¼uidä¸º0æ¯rootç¨æ·
åå»ºäº /home/user1ç®å½
/etc/passwd è®°å½user1çä¿¡æ¯
/etc/shadow è®°å½user1å¯ç ç¸å³ä¿¡æ¯
æªæå®ç¨æ·ç»æ¶ï¼åå»ºä¸ä¸ªåç¨æ·åå®å¨ç¸åçç¨æ·ç»
åªæç®¡çå(root)æææéåå»ºç¨æ·

userdel user1 å é¤user1,ä¿ç/home/user1
userdel -r user1 å é¤user1,ä¸å¹¶å é¤å®¶ç®å½/home/user1

usermod [option] username
options:
-d DIR  ä¿®æ¹ç¨æ·çå®¶ç®å½
usermod -d /home/u1 user1 å°user1çå®¶ç®å½åæ/home/u1

chage -æ´æ¹ç¨æ·/ç¨æ·å¯ç çè¿ææ¶é´


```
### ç¨æ·ç»

```
groupadd  GROUPNAME
groupdel  GROUPNAME

groupadd group1 æ°å»ºç¨æ·ç»
usermod -g group1 user1 å°user1æ·»å è¿group1

useradd -g group1 user2 æ°å»ºuser2å¹¶æ·»å å°group1

```
### åæ¢ç¨æ·

```
shell æ¹å¼åæ¢ç¨æ·

su - user1  åæ¢èº«ä»½ä¸ºuser1çåæ¶åæ¢å°user1çå®¶ç®å½
su user1  åæ¢èº«ä»½ä¸ºuser1ä¸åæ¢ç®å½

ä»¥å¶ä»ç¨æ·èº«ä»½æ§è¡å½ä»¤
sudo  command
visudo  è®¾ç½®éè¦ä½¿ç¨sudoçç¨æ·ç»

ä»¥shutdown å½ä»¤ä¸ºä¾å­

ç¨visudoå½ä»¤ç¼è¾/etc/sudersæä»¶

ç¨ä¾
%wheel    ALL=(ALL) ALL
ç¨æ·ç»    ALL é£äºç»ç«¯å¯ä»¥è®¿é®(æ¬å°/è¿ç¨) = (ALL)å¯ä»¥æ§è¡é£äºæä»¤ æ¯å¦éè¦å¯ç 
    Localhost=()ç»ç«¯å¯ä»¥è®¿é®
æäºuser1ç¨æ·shutdown -cçæé
user3   ALL=/usr/bin/shutdown -c  
which shutdownå¯ä»¥æ¥çshutdownå¨åªé

ä¿®æ¹åuser3å¯ä»¥ä½¿ç¨sudoæ§è¡ shutdown -cå½ä»¤
user3è¦æå¯ç ï¼passwd user3

sudo shutdown -c

```
### ç¨æ·åç¨æ·ç»éç½®æä»¶
```
/etc/passwd:

root:x:0:0::/root:/bin/bash
nobody:x:65534:65534:Nobody:/:/usr/bin/nologin
dbus:x:81:81:System Message Bus:/:/usr/bin/nologin
bin:x:1:1::/:/usr/bin/nologin
daemon:x:2:2::/:/usr/bin/nologin
mail:x:8:12::/var/spool/mail:/usr/bin/nologin
ftp:x:14:11::/srv/ftp:/usr/bin/nologin
http:x:33:33::/srv/http:/usr/bin/nologin
systemd-journal-remote:x:982:982:systemd Journal Remote:/:/usr/bin/nologin
systemd-network:x:981:981:systemd Network Management:/:/usr/bin/nologin
systemd-resolve:x:980:980:systemd Resolver:/:/usr/bin/nologin
systemd-timesync:x:979:979:systemd Time Synchronization:/:/usr/bin/nologin
systemd-coredump:x:978:978:systemd Core Dumper:/:/usr/bin/nologin
uuidd:x:68:68::/:/usr/bin/nologin
dnsmasq:x:977:977:dnsmasq daemon:/:/usr/bin/nologin
rpc:x:32:32:Rpcbind Daemon:/var/lib/rpcbind:/usr/bin/nologin
avahi:x:976:976:Avahi mDNS/DNS-SD daemon:/:/usr/bin/nologin
colord:x:975:975:Color management daemon:/var/lib/colord:/usr/bin/nologin
git:x:974:974:git daemon user:/:/usr/bin/git-shell
lightdm:x:973:973:Light Display Manager:/var/lib/lightdm:/usr/bin/nologin
nm-openconnect:x:972:972:NetworkManager OpenConnect:/:/usr/bin/nologin
nm-openvpn:x:971:971:NetworkManager OpenVPN:/:/usr/bin/nologin
ntp:x:87:87:Network Time Protocol:/var/lib/ntp:/bin/false
polkitd:x:102:102:PolicyKit daemon:/:/usr/bin/nologin
usbmux:x:140:140:usbmux user:/:/usr/bin/nologin
kamisama:x:1000:1000:kamisama:/home/kamisama:/bin/zsh
dhcpcd:x:970:970:dhcpcd privilege separation:/var/lib/dhcpcd:/usr/bin/nologin
mysql:x:969:969:MariaDB:/var/lib/mysql:/usr/bin/nologin
rtkit:x:133:133:RealtimeKit:/proc:/usr/bin/nologin
cups:x:209:209:cups helper user:/:/usr/bin/nologin
xmms2:x:968:968::/var/lib/xmms2:/usr/bin/nologin
user1:x:1001:1001::/home/user1:/bin/bash
user2:x:1002:1002::/home/user2:/bin/bash

```

user1 --ç¨æ·å

x     --æ¯å¦éè¦å¯ç 

1001  --uid

1001  --gid

ç¬¬äºä¸ªå­æ®µæ¯æ³¨é

ç¬¬å­ä¸ªæ¯æ ¹ç®å½

ç¬¬ä¸ä¸ªæ¯ç¨æ·ä½¿ç¨çå½ä»¤è§£éå¨(bologinä¸è½ç»å½ç»ç«¯)

å¯ä»¥æåè¿ä¸ªæä»¶æ°å»ºç¨æ·


```
/etc/shadow
root:$6$NepyQ6dyd2spEJzl$0rjYlOgixR.Lsgc2ynQ.XrqoHMyKrSjQHEH35Kv8Ncov1iPrlN7CXc8KTQoSpufDU.hMmnfYREQk0mrVjR3wp0:18392::::::
nobody:!!:18335::::::
dbus:!!:18335::::::
bin:!!:18335::::::
daemon:!!:18335::::::
mail:!!:18335::::::
ftp:!!:18335::::::
http:!!:18335::::::
systemd-journal-remote:!!:18335::::::
systemd-network:!!:18335::::::
systemd-resolve:!!:18335::::::
systemd-timesync:!!:18335::::::
systemd-coredump:!!:18335::::::
uuidd:!!:18335::::::
dnsmasq:!!:18335::::::
rpc:!!:18335::::::
avahi:!!:18335::::::
colord:!!:18335::::::
git:!!:18335::::::
lightdm:!!:18335::::::
nm-openconnect:!!:18335::::::
nm-openvpn:!!:18335::::::
ntp:!!:18335::::::
polkitd:!!:18335::::::
usbmux:!!:18335::::::
kamisama:$6$rs.yzOpJ2aJJ58.I$rWtHVPX74W.jsZ7b8u8FNyr9H38ozqVnu8l4pxzdfsdH2Rv5JW4HQOiw/hJ8XhY4HcekJz1tfhlAmLFn4KfOb.:18392:0:99999:7:::
dhcpcd:!!:18392::::::
mysql:!!:18392::::::
rtkit:!!:18392::::::
cups:!!:18393::::::
xmms2:!!:18395::::::
user1:!:18401:0:99999:7:::
user2:!:18401:0:99999:7:::

```
/etc/shadow
ç¨æ·åç¨æ·å¯ç ä¿¡æ¯

root  --å
$6$.... --å å¯åå¯ç 


```
/etc/group

root:x:0:root
adm:x:999:daemon
wheel:x:998:kamisama
kmem:x:997:
tty:x:5:
utmp:x:996:
audio:x:995:xmms2
disk:x:994:
input:x:993:
kvm:x:992:
lp:x:991:cups,kamisama
optical:x:990:
render:x:989:
storage:x:988:
uucp:x:987:
video:x:986:
users:x:985:
sys:x:3:bin,kamisama
mem:x:8:
ftp:x:11:
mail:x:12:
log:x:19:
smmsp:x:25:
proc:x:26:polkitd
games:x:50:
lock:x:54:
network:x:90:kamisama
floppy:x:94:
scanner:x:96:
power:x:98:kamisama
systemd-journal:x:984:
rfkill:x:983:
nobody:x:65534:
dbus:x:81:
bin:x:1:daemon
daemon:x:2:bin
http:x:33:
systemd-journal-remote:x:982:
systemd-network:x:981:
systemd-resolve:x:980:
systemd-timesync:x:979:
systemd-coredump:x:978:
uuidd:x:68:
dnsmasq:x:977:
rpc:x:32:
locate:x:21:
ntp:x:87:
avahi:x:976:
colord:x:975:
git:x:974:
lightdm:x:973:
nm-openconnect:x:972:
nm-openvpn:x:971:
polkitd:x:102:
usbmux:x:140:
kamisama:x:1000:
dhcpcd:x:970:
mysql:x:969:
rtkit:x:133:
cups:x:209:
xmms2:x:968:
user1:x:1001:
user2:x:1002:

```

root->ç»åç§°

x->æ¯å¦éå¯ç éªè¯

0->ç»ID

ç¬¬åå­æ®µ->å¶ä»ç»è®¾ç½®

## æéç®¡ç

### æä»¶ä¸ç®å½çæéè¡¨ç¤º
* æ¥çæä»¶æé
```bash
    ls -l
    -rw------- 1 root root 1523 sep 28 12:05 anaconda-ks.cfg
```
```
    ç±»å æé   æå±ç¨æ·åç»      æä»¶å
  
  æä»¶ç±»å
  - æ®éæä»¶
  d ç®å½æä»¶
  b åç¹æ®æä»¶
  c å­ç¬¦ç¹æ®æä»¶
  l ç¬¦å·é¾æ¥
  f å½åç®¡é
  s å¥æ¥å­æä»¶
  
  æéè¡¨ç¤ºæ¹æ³

  r è¯»
  w å
  x æ§è¡
  æ°å­æéçè¡¨ç¤ºæ¹æ³
  r=4
  w=2
  x=1

  -rw-r-xr-- 1 username groupname mtime filename
  rw- æä»¶å±ä¸»çæé
  r-x æä»¶å±ç»çæé
  r-- å¶ä»ç¨æ·çæé

åå»ºæ°ç¨æ·æé»è®¤æéï¼æ ¹æ®umaskå¼è®¡ç®ï¼å±ä¸»åå±ç»æ ¹æ®å½åè¿ç¨çç¨æ·æ¥è®¾å®(666-umask)
  ç®å½æéçè¡¨ç¤ºæ¹æ³
  x è¿å¥ç®å½
  rx è¿å¥ç®å½ä¸æ¾ç¤ºç®å½åæä»¶å
  wx ä¿®æ¹ç®å½åæä»¶å

```
* ä¿®æ¹æä»¶æé

  * chmod ä¿®æ¹æä»¶ãç®å½æé
    * chmod u+x /tmp/testfile
    * chmod 755 /tmp/testfile
  * chown æ´æ¹å±ç»ãå±ä¸»
  * chgrp åç¬æ´æ¹å±ç»ï¼ä¸å¸¸ç¨

```bash
chmod (u g o)[-+=]

touch afile

chmod u+x afile å¢å å±ä¸»æ§è¡æé

chmod g-r afile åå°å±ç»è¯»åæé

chmod o=w afile è®¾ç½®å¶ä»ç¨æ·ä¸ºåªæåæé

chmod a+r afile å±ä¸»ãå±ç»ãå¶ä»ç¨æ·é½å¢å è¯»åæé

ä½¿ç¨å­ç¬¦æé

chmod u-wx afile åå°å±ä¸»çååæ§è¡æé

ä½¿ç¨æ°å­æé
chmod 446 afile å±ç»ãå±ä¸»åªè¯»ãå¶ä»ç¨æ·è¯»å

```

```bash
mkdir /test

ls -ld /test

drwxr-xr-x. 2 root root 6 6æ 07ï¼18 test

```
> rootç¨æ·æ¯ä¸åæééå¶çï¼

æ¹åæä»¶å±ä¸»
```bash
chown user1 test

```
æ¹åå±ç»
```bash
chown :group1 test
```

```bash
chgrp group2 test
```
> æä½<kbd>Ctrl</kbd>+<kbd>r</kbd> å¯ä»¥æç´¢ä¹åæ§è¡è¿çå½ä»¤ï¼ç´æ¥ææ¹åé®ä¸å¯ä»¥ä½¿ç¨ä¹åçå½ä»¤

* æéç®¡çåæä»¶çç¹æ®æé

```bash
chown user1:group1 afile åæ¶è®¾ç½®userågroup
chmod 400 afile è¯»åæé
echo 123 > afile
cat afile
```

> echo info æ¾ç¤ºä¿¡æ¯ echo 123 > afile è¾åºéå®åï¼å°è¾åºå°å±å¹ä¸çä¿¡æ¯è¾åºå°æä»¶ä¸­ä¸ä¸ª>æ¯æ¸ç©ºæä»¶å¹¶è¾åºï¼ä¸¤ä¸ª>æ¯è¿½å ï¼ä¸æ¸ç©ºæä»¶

> å¯¹ç®å½æä»¶ï¼xè¡¨ç¤ºå¯è¿å¥ï¼rè¡¨ç¤ºå¯æ¥çéé¢çæä»¶ï¼wè¡¨ç¤ºå¯ä»¥å¢å åå é¤éé¢çæä»¶ãæ®éæä»¶ï¼xè¡¨ç¤ºå¯æ§è¡ï¼rå¯è¯»åæä»¶åå®¹ï¼wå¯ä»¥ä¿®æ¹æä»¶åå®¹
> æä»¥ç®å½æä»¶çæéä¸è¬é½æ¯rx æ wx ærwx

* ç¹æ®æé
```
SUID ç¨äºäºè¿å¶å¯æ§è¡æä»¶ãæ§è¡å½ä»¤æ¶è·åæä»¶å±ä¸»æé
  å¦ /usr/bin/passwd
ls -l /usr/bin/passwd
-rwsr-xr-x. 1 root root ....
å°ås ä¸ç®¡æ¯ä»ä¹ç¨æ·æ§è¡è¿æ¡å½ä»¤é½ä¼ä»¥æä»¶å±ä¸»èº«ä»½æ§è¡è¿æ¡å½ä»¤


SGID ç¨äºç®å½ï¼å¨è¯¥ç®å½åå»ºæ°æä»¶åç®å½æ¶ï¼æéèªå¨æ´æ¹ä¸ºè¯¥ç®å½çå±ç»(ç¨äºæä»¶å±äº«)

SBIT ç¨äºç®å½ï¼å¨è¯¥ç®å½ä¸æ°å»ºçæä»¶åç®å½ï¼ä»root åèªå·±å¯ä»¥å é¤ï¼å¦/tmp
ls -ld /tmp
drwxrwxrwt. 16 root root ...


```
å¢å ç¹æ®æé

```bash

SUID  4+...

chmod 4755 /test/bfile
ls -l /test/bfile
-rwsr-xr-x ...

SGID 2+...

SBIT 1+...

chmod 1777 /test
ls -l /test
drwxrwxrwt ...

```
## ç½ç»ç®¡ç

* ç½ç»ç¶ææ¥ç
  * ç½ç»ç¶ææ¥çå·¥å·
      net-tools VS iproute
      1. net-tools
        * ifconfig
        * etho ç¬¬ä¸åç½å¡(ç½ç»æ¥å£)
        * ä¹å¯è½å«ä¸é¢åå­
      * eno1 æ¿è½½ç½å¡
      * ens33 PCI-Eç½å¡
      * enp0s3 æ æ³è·åç©çä¿¡æ¯çPCI-E ç½å¡
      * CentOS 7ä½¿ç¨äºä¸è´æ§ç½ç»è®¾å¤å½åï¼ä»¥ä¸é½ä¸å¹éåç¨eth0
    * route
    * netstat
      2. iproute2
    * ip
    * ss

>  **ç½ç»æ¥å£å½ä»¤ä¿®æ¹**
> * ç½å¡å½åè§ååå°biosdevname å net.ifnames ä¸¤ä¸ªåæ°å½±å
> * ç¼è¾/etc/default/grub æä»¶ï¼ä¿®æ¹GRUB_CMDLINE_LINUXï¼å¢å biosdevname=0 net.ifnames=0
> * æ´æ°grub
>   * grub2-mkconfig -o /boot/grub2/grub.cfg
> * éå¯
>   * reboot

> ||biosdevname|net.ifnames|ç½å¡å|
> | --- | --- | --- | --- |
> |é»è®¤|0|1|ens33|
> |ç»å1|1|0|em1|
> |ç»å2|0|0|eth0
æ¥çç½ç»æåµ
```bash
mii-tool eth0 æ¥çç©çç½å¡è¿æ¥æåµ
route -n æ¥çç½å³å½ä»¤ -nè¡¨ç¤ºä¸è§£æä¸»æºå
```

* ç½ç»éç½®

    ä¿®æ¹ç½ç»éç½®å½ä»¤
      
```
  ç½å¡
    ifconfig <interface> <ip> [netmask]
    ifup/ifdown <interface> å¼å¯å³é­ç½å¡
      ç½å³
  route add default gw <ip>
  route add -host ...
  route add -net ...

```
* è·¯ç±å½ä»¤
```
  ä¿®æ¹ç½å³
  route del default gw 10.211.55.1  å é¤é»è®¤0.0.0.0ç½å³
  route add default gw 10.211.55.2
  æ·»å æç»è·¯ç±
  route add -host 10.0.0.1 gw 10.211.55.1
  æå®ç½æ®µæ·»å æç»è·¯ç±
  route add -net 192.168.0.0 netmask 255.255.255.0 gw 10.211.55.3
```

å¯¹åºipå½ä»¤
|net-tools|iproute2|
| :---: | :---: |
|ipconfig| ip addr ls |
|ifup eth0|ip link set dev eth0 up|
|ifconfig eth1 10.0.0/24 via 192.168.0.1|route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.0.1|


* ç½ç»æéæé¤
  
  å¸¸ç¨å½ä»¤
  
  * ping  --æ¥çå½åç½ç»æ¯å¦çé
  ```bash
    ping www.baidu.com
  ```
  * traceroute  --å½åç½ç»ç¶æ
  ```bash
    traceroute -w 1 www.baidu.com
         wait 1sè¶æ¶ç­å¾
  ```
  * mtr -- åä¸(åçä¸¢å¤±æåµ)
  ```bash
    mtr
  ```
  * nslookup  --ååé®é¢
  ```bash
    nslookup www.baidu.com  è§£æåå
  ```
  * telnet  --ç«¯å£é®é¢
  ```bash
    telnet www.baidu.com 80   æ¥ç80ç«¯å£æ¯å¦é
  ```

  * tcpdump --tcpå
  ```bash
    tcpdump -i any -n port 80 æåä»»æç½å¡80ç«¯å£çæ°æ®å
      -i any æåææç½å¡ -nè§£æåå
    tcpdump -i any -n host 10.0.0.1
    tcpdump -i any -n host 10.0.0.1 and port 80
    tcpdump -i any -n host 10.0.0.1 and port 80 -w /tmp/filename
  ```
  * netstat --çå¬é®é¢
  ```bash
    netstat -n -t -p -l
      -nä¸æ¾ç¤ºåå -t tcpæ¹å¼æªå -pè¿ç¨ -tçå¬çæå¡
    netstat -ntpl
  ```
  * ss    --çå¬é®é¢
  ```bash
    ss -ntpl
  ```
**å½ä»¤éç½®åªæ¯ä¸´æ¶ä¿®æ¹ï¼æ°¸ä¹çæéè¦ä¿®æ¹éç½®æä»¶**

* ç½ç»æå¡ç®¡ç
    
    **SysVåSystemd**
    ```
    service network start/stop/restart
    chkconfig -list network

    systemctl list-unit-files NetworkManager.service
    systemctl start/stop/restart NetworkManager
    systemctl enable/disable NetworkManager å¼æºèªå¯å¨
    ```
* å¸¸ç¨ç½ç»éç½®æä»¶
  * ifcfg-eth0 ç½å¡ç¸å³éç½®æä»¶
  * /etc/hosts ä¸»æºåç¸å³éç½®æä»¶
  * centos7ç½å¡éç½®æä»¶
      ```
      /etc/sysconfig/network-scripts
      TYPE=
      UIP=
      NAME=
      BOOTPROTO=none --éæ dhcp å¨æ
      IPADDR= ipå°å
      NETMASK=
      GATEWAY=
      DNS1=...
      DNS2=...
      DNS3=...
      ```
  * ä¿®æ¹ä¸»æºå
      ```bash
      hostname [name] ä¸´æ¶ä¿®æ¹
      hostnamectl set-hostname [name] æ°¸ä¹çæ
      ä¿®æ¹hostnameä¹åéè¦å¨/etc/hostsä¸­ä¿®æ¹127.0.0.1å¯¹åºä¸»æºå
      ä¸ç¶å¨å¼æºæ¶ä¼ææå¡å ä¸ºä¸»æºåéè¯¯æ æ³å¯å¨ï¼
      è®¡ç®æºåªè½ç­å¾æå¡è¶æ¶ï¼ä¼å½±åå¼æºéåº¦
      ```


## è½¯ä»¶å®è£

### è½¯ä»¶åç®¡çå¨å®è£

åç®¡çå¨æ¯æ¹ä¾¿è½¯ä»¶å®è£ãå¸è½½ãè§£å³è½¯ä»¶ä¾èµå³ç³»çéè¦å·¥å·
* centosãredhatä½¿ç¨yumåç®¡çå¨ï¼è½¯ä»¶å®è£åæ ¼å¼ä¸ºrpm
* DebianãUbuntuä½¿ç¨aptåç®¡çå¨ï¼è½¯ä»¶å®è£åæ ¼å¼ä¸ºdeb

#### rpmå
*a rpmåæ ¼å¼
    * vim-common-7.4.10-5.el7.x86_64.rpm

  è½¯ä»¶å½å è½¯ä»¶åç§° è½¯ä»¶çæ¬ ç³»ç»çæ¬ å¹³å°


##### rpmå½ä»¤
* rpmå½ä»¤å¸¸ç¨åæ°
  * -q æ¥è¯¢è½¯ä»¶å
  * -i å®è£è½¯ä»¶å
  * -e å¸è½½è½¯ä»¶å
```bash
asd 
```
> ```bash
> linuxä¸åçæä»¶
> dd if=/dev/sr0 of=/xxx/xx.iso å°åçå¶é æåçéå 
> mount /dev/sr0 /mnt/  æè½½è®¾å¤
> cd /mnt
> cd packages/
> ls vim*
> æ¾å°vim-commonå
> mkdir /root/rpms
> cp vim-common-*.rpm vim-enhanced-*.rpm /root/rpms
> rpm -qa æ¥è¯¢ææä»¥å®è£çå
> rpm -qa | more  ç®¡éç¬¦ï¼åå±æ¾ç¤º
> rpm -q vim-common æ¥è¯¢è½¯ä»¶å
> rpm -i vim-enhanced-*.rpm å®è£éè¦æå®æ´åç§°æééç¬¦
> rpm -e vim-enhance å¸è½½
> rpm -e vim-common vim-enhanced  åæ¶å¸è½½ä¸¤ä¸ªè½¯ä»¶å
> rpm -i vim-enhanced-*.rpm æç¤ºéè¦ä¾èµå³ç³»ï¼éè¦æå¨è§£å³ä¾èµå³ç³»
> yum ä»åºå¯ä»¥èªå¨è§£å³ä¾èµå³ç³»
> å¦æè½¯ä»¶çæ¬ä¸ç¬¦åè¦æ±è¿å¯ä»¥éè¿æºä»£ç ç¼è¯å®è£è½¯ä»¶å
> ```
  

##### yumåç®¡çå¨
* arpmåçé®é¢
    * éè¦èªå·±è§£å³ä¾èµå³ç³»
    * è½¯ä»¶æ¥æºä¸å¯é 
* centos yum æº
    * http://mirror.centos.org/centos/7/
* å½åéå
    * https://opsx.alibaba.com/mirror
* yuméç½®æä»¶
    * / etc/yum.repos.d/CentOS-Base.repo
    * wget =O /etc/yum.repos.d/CentOS-Base.repo
* yumå½ä»¤å¸¸ç¨éé¡¹
    * install
    * remove 
    * list| group list
    * update
* yumä¿®æ¹å½åæº
    ```bash
    mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.baskup 
    å¤ä»½yuméç½®
    wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
    ä¿®æ¹éç½®æä»¶
    yum makecache æ´æ°ç¼å­
    rmp -e vim-enhanced
    rmp -e vim-common
    å¸è½½vim
    yum install vim-enhanced
    å®è£vim-enhanced ä¼èªå¨å®è£vim-common
    yum remove vim
    å¸è½½vim
    yum update æ´æ°ææè½¯ä»¶
    yum update name æ´æ°nameè½¯ä»¶
    ```

### æºä»£ç å®è£

* æ©ælinuxæ¶è´¹è½¯ä»¶ç¨äºè¿å¶å®è£(å¼æºä¹å),è¿è¦ææåç§åè®®ï¼ååéº»ç¦
* å¼æº(å¬å¼æºä»£ç )ä¹åï¼è¯çæºä»£ç ç¼è¯å®è£
  * wget https://openresty.org/download/openresty-1.15.8.1tar.gz
  * tar -zxf openresty-VERSION.tar.gz è§£åç¼©
  * cd openresty-VERSION/     è¿å¥å°æºä»£ç ç®å½
  * ./configure --prefix=/usr/local/openresty æ­¥éª¤ä¸ï¼éç½®è½¯ä»¶åç³»ç»å¹éï¼prefixå¶å®è½¯ä»¶å®è£éç½®ï¼ä¸è¬è¦æå®ï¼ä¸ç¶å é¤çæ¶åè¦å°å¤æ¾
  * make -j2  ç¨ä¸¤ä¸ªé»è¾ä¸CPUè¿è¡ç¼è¯ï¼ä¸å®ç¨åº¦ä¸å å¿«ç¼è¯éåº¦
  * make install  ç¼è¯å¥½çè½¯ä»¶å®è£å°æå®ç®å½
> æ§è¡./congifure ææ¶ä¼æ¥éï¼å¨éè¯¯ä¿¡æ¯ä¸­æ¾å°ç¼ºå¤±çä¾èµåº/è½¯ä»¶ï¼éè¦å®è£å¯¹åºè½¯ä»¶æ¥è§£å³éè¯¯ãè§£å³éè¯¯ååæ§è¡ä¸æ¬¡ï¼æ¥çè¿ç¼ºå°ä»ä¹åºï¼åéå¤ä¸é¢æ­¥éª¤ï¼ç´å°æåæ§è¡ä¸æ¥éãå¦ææç¤ºgmakeã gmake installæ¯æ¹ä¾¿è·¨å¹³å°å®è£çï¼gmakeä¹å¯ä»¥å¶å® -j2å å¿«éåº¦ï¼ä½æ¯å¦æä»£ç ä¹é´æä¾èµå³ç³»ï¼ä¹ä¸ä¼å å¿«å¤å°éåº¦çï¼æ²¡æä¾èµå³ç³»æè½ææ¾å å¿«
  * cd /usr/local/openresty è¿å¥å®è£ç®å½ï¼å¯ä»¥æ¥çè½¯ä»¶ç®å½
> æºç å®è£æ¯æåçææ®µï¼ä¸å°ä¸ä¸å¾å·²ï¼è¿æ¯ä¸è¦è´¹æ¶è´¹åä½¿ç¨æºç å®è£äº
> æºä»£ç å®è£æ¯éè¦ç¨å°è½¯ä»¶çææ°ç¹æ§ï¼ä½è½¯ä»¶ä»åºéä¸æ¯ææ°çæ¬æ¶æä½¿ç¨ç

## åçº§åæ ¸

* rpmæ ¼å¼åæ ¸
  * uname -r æ¥çåæ ¸çæ¬ 
  * yum install kernel-3.10.0 åçº§åæ ¸çæ¬
  * yum update åçº§å·²å®è£çå¶ä»è½¯ä»¶ååè¡¥ä¸
* æºä»£ç ç¼è¯å®è£
  * å®è£ä¾èµå yum install gcc gcc-c++ make ncurses-devel openssl-devel elfutils-libelf-devel
  * ä¸è½½å¹¶è§£åç¼©åæ ¸
  * https://www.kernel.org
  * tar xvf linux-5.1.10.tar.xz -C /usr/src/kernels
  * éç½®åæ ¸ç¼è¯åæ°
    * cd /usr/src/kernels/linux-5.1.10
    * make menuconfig | allyesconfig | allnoconfig
  * ä½¿ç¨å½åç³»ç»åæ ¸éç½®
    * cp /boot/config-kernelversion.platform /usr/src/kernels/linux-5.1.10/.config
  * æ¥çCPU
    * lscpu
  * ç¼è¯
    * make -j2 all
  * å®è£åæ ¸
    * make modules_install
    * make install
> uname -r æ¥çåæ ¸çæ¬
> epelä»åºå¯ä»¥æ©å±centosä»åº
> yum install epel-release -y å®è£epel
> åçº§åæ ¸ yum install kernel 
> yum install kernel-3.10.0 å¶å®çæ¬åæ ¸
> yum update æ´æ°æ´ä¸ªç³»ç»
**æºä»£ç å®è£åæ ¸**
```bash
ä¸è½½åæ ¸æä»¶linux-5.1.14.tar.xz
å®è£ä¾èµé¡¹
yum install gcc gcc-c++ make ncurse-devel openssl-devel elfutil-libelf-devel
è§£å
tar xvf linux-5.1.14.tar.xz -C /usr/src/kernels/
cd /usr/src/kernels/
cd linux-5.1.14/
ls -a æ¥çæææä»¶(éèæä»¶)ï¼æéç½®å±æ§
make menuconfig éç½®åæ ¸ï¼è¿å¥ç±»ä¼¼å¾å½¢çé¢çéç½®çé¢
File systems-->DOS/FAT/NT Filesystems--> NTFS file system support æ¥çæç¤ºå¯ä»¥éæ©åç§å®è£éé¡¹
M --æ¨¡ååå è½½ * --åºåå°åæ ¸
éæ©ä¿å­éåºå°±æ¯æNTFSæä»¶äº

å°å½åç³»ç»çéç½®åºç¨å°æ°çåæ ¸éç½®
cd /boot
cp config-3.10.0-957.21.2.e17.x86_64 /usr/src/kernels/linux-5.1.14/.config
åæéç½®ä¸æ¯æNTFSï¼éè¦åéç½®
cd -  è¿åä¸ä¸ä¸ªå·¥ä½ç®å½
make menuconfig åæ¬¡è®¾ç½®NTFSæ¯æ

å®è£ä¹å æ¥çcpuä¸ªæ°
lscpu (Core per socket è¡¨ç¤ºåæ ¸ä¸ªæ°)

make -j2 all  ç¼è¯åæ ¸

df -h æ¥çä½¿ç¨äºå¤å°ç©ºé´

å®è£ç¼è¯å¥½çåæ ¸æ¨¡å
make modules_install
***
DEPMOD 5.1.14

å®è£åæ ¸
make install

reboot éå¯

æ¥å°å¼å¯¼çé¢(GRUBçé¢)
åå§æ¯3.10çæ¬åæ ¸
æ°å®è£æ¯5.1.14

è¿å¥åå¼å¯ç»ç«¯

uname -r æ¥çç³»ç»åæ ¸çæ¬

```
## GRUBéç½®

* grub 
* grubéç½®æä»¶
  * /etc/default/grub
    * ç®å(é»è®¤)éç½®æä»¶
      ```
      vim /etc/default/grub
      ä¸¤ä¸ªéè¦è®¾ç½®é¡¹
      
      GRUB_DEFAULT=saved  
      savedæå¼å¯¼æ¶é»è®¤å¼å¯¼å°åªä¸ä¸ªåæ ¸
      grub2-editenv list  æ¥çå½åä½¿ç¨åæ ¸
      grep ^menu /boot/grub2/grub.cfg   æç´¢ææåæ ¸
      grub2-set-default 0 å¼å¯¼ç¬¬ä¸ä¸ªåæ ¸
      grub2-set-default 1 ç¬¬äºä¸ªããã

      GRUB_CMDLINE_LINUX = '...'  rhgb å¾å½¢çé¢ quietéé»æ¨¡å¼ï¼åªæå°å¿è¦æ¶æ¯ï¼
      å¦æç³»ç»å¼å¸¸ï¼å¯ä»¥å»æè¿ä¸¤ä¸ªåæ°ï¼éå¯æ¶å¯ä»¥çå°æ´è¯¦ç»çä¿¡æ¯,ä¿®æ¹ç½å¡ä¿¡æ¯ä¹æ¯è¿éæ·»å åæ°
      ```
  * /etc/grub.d/
        * è¯¦ç»éç½®æä»¶çç®å½
  * /boot/grub2/grub.cfg
        * 
  * grub2-mkconfig -o /boot/grub2/grub.cfg

* ä½¿ç¨åç¨æ·è¿å¥ç³»ç»(å¿è®°rootå¯ç )
  * éå¯çµè
    ```bash
    reboot
    éæ©è¦å¼å¯¼çåæ ¸ï¼æeé®
    æ¾å°linux16... è¿ä¸è¡
    æ¾å°root=...æ¾å°æ ¹ç®å½çç®å½
    å¨æåæ·»å ä¸ä¸ª single ( centos7 æ¯ rd.break)
    æä¸Ctrl+xéå¯
    åæ¬¡å¯å¨ä¸éè¦è¾å¥å¯ç å°±å¯ä»¥è¿å¥

    ```
> åç¨æ·è¿å¥ç³»ç»è¿å¥çæ¯ç³»ç»èæåºæ¥çæ ¹ç®å½ï¼æä½ä¸ä¼è¢«ä¿å­
> mount -o remount,rw /sysroot  éæ°æè½½ç¡¬ç(é»è¾ä¸),ä»¥å¯è¯»åæ¹å¼æè½½ /sysroot
> chroot /sysroot ä¿®æ¹æ ¹ç®å½ä¸ºå®éæ ¹ç®å½
> echo 123456|passwd --stdin root éè¿echoæ¾ç¤ºçä¿¡æ¯éè¿ç®¡éä¼ éç»passwd
> è³æ­¤ï¼rootå¯ç å·²ç»è¢«éç½®ï¼ä½æ¯
> ç³»ç»ä¸­çSELinuxå®å¨ç»ä»¶(å¼ºå¶è®¿é®æ§å¶)ä¼æ ¡éª/etc/passwd å/etc/shadowï¼åç°è¿ä¸¤ä¸ªæä»¶éæ åä¿®æ¹ï¼ä¼å¯¼è´æ æ³è¿å¥å°ç³»ç»
> å³é­SELinux
> vim /etc/selinux/config
> SELINUX=enforcing æ¹ædisabledå°±å³é­äºSElinuxç»ä»¶
> ä¿å­éåº
> exit åå°èæroot
> reboot

## è¿ç¨ç®¡ç
* è¿ç¨çæ¦å¿µ
* è¿ç¨çæ§å¶å½ä»¤
* è¿ç¨çéä¿¡æ¹å¼--ä¿¡å·
* å®æ¤è¿ç¨åç³»ç»æ¥å¿
* æå¡ç®¡çå·¥å·systemctl
* SELinuxç®ä»


### è¿ç¨çæ¦å¿µ
* è¿ç¨--aè¿è¡ä¸­çç¨åºï¼ä»ç¨åºå¼å§è¿è¡å°ç»æ­¢çæ´ä¸ªçå½å¨ææ¯å¯ç®¡çç
  * Cç¨åºçå¯å¨æ¯ä»mainå½æ°å¼å§ç
    * int main(int agrc, char *argv[])
    * ç»æ­¢çæ¹å¼å¹¶ä¸å¯ä¸ï¼å¹¶åä¸ºæ­£å¸¸ç§æ¤åå¼å¸¸ç»æ­¢
      * æ­£å¸¸ç»æ­¢ä¹åä¸ºä»mainè¿åãè°ç¨exitç­æ¹å¼
      * å¼å¸¸ç§æ¤åä¸ºè°ç¨abortãæ¥åä¿¡å·ç­
* æ¥çè¿ç¨
  * ps
  ```bash
  kamisama-Manjaroi3 :: ~ Â» ps
      PID TTY          TIME CMD
   215660 pts/1    00:00:00 zsh
   215674 pts/1    00:00:00 ps
  ps -e | more æ¥çä¸åç»ç«¯çææè¿ç¨ ä¸éè¿ç®¡éåé¡µè¾åº
  ps -ef | more å ä¸fæ¾ç¤ºUID(ææç¨æ·ID),PPID(ç¶è¿ç¨)
  ps -eLf | more æ¾ç¤ºè½»éçº§è¿ç¨(çº¿ç¨) 
  ```
  * pstree  æ¥çè¿ç¨æ 
  ```bash
  pstree | more
  ```
  * top å¨ææ¥çè¿ç¨/ç³»ç» ä¿¡æ¯
  ```bash
  top
  upå¼æºæ¶é´
  user ç¨æ·æ°
  load average å¹³åè´è½½ è¡¡éç³»ç»è´è½½ç¨åº¦ ä¸ä¸ªæ°å­ åå«æ¯1min 5min 10minéæ ·å¾å°çç³»ç»ç¹å¿ç¨åº¦
  %CPU(s): us ç¨æ·ä½¿ç¨ sy ç³»ç»è¿ç¨ ni:nice ä¼åçº§ id idle ç©ºé²  wa iowaitç£çéåº¦è¿æ¢å°±ä¼ç­å¾io
  ææ°å­1å¯ä»¥æ¥çæ¯ä¸ä¸ªCPUçè¿è¡ç¶æ(åæ¬¡æ1åæ¶)
  æså¯ä»¥è®¾ç½®ç¶ææ´æ°æ¶é´é´é
  ```

> è¿ç¨ä¹æ¯æ å½¢ç»æï¼è¿ç¨åæéæçå¯ä¸å¯åçå³ç³»

### è¿ç¨æ§å¶
#### è¿ç¨çä¼åçº§è°æ´
* è°æ´ä¼åçº§
  * nice èå´ä»-20å°19
  * renice éæ°è®¾ç½®ä¼åçº§
* è¿ç¨çä½ä¸æ§å¶
      * jobs
  * & ç¬¦å·
```bash
vim a.sh
chmod u+x a.sh  ç¨æ·æ§è¡æé(èæ¬æä»¶è¦åæ·»å ræé)
ls -l a.sh
id æ¥çå½åç¨æ·çææID(UID)
./a.sh
top -p pid  æ¥ça.shè¿è¡ç¶åµé»è®¤niä¸º0
nice -n 10 ./a.sh æ°å­å¤§ï¼ä¼åçº§ä½
top -p pid  a.shä¼åçº§niåå

å¯¹å·²ç»è¿è¡çç¨åºåæ¬¡è°ä½ä¼åçº§
å¦æå¼ç»ç«¯
renice -n 15 pid


```
 a.shåå®¹
```
#!/binbash
 echo $$
 while : 
 do
  :
 done
````
**æ¯æ¬¡æå¼å¾å¤ç»ç«¯ä¸æ¹ä¾¿ï¼æä»¬å¯ä»¥è¿è¡åå°åå°çåæ¢ï¼ä¹å°±æ¯è¿ç¨çä½ä¸æ§å¶**

```bash
./a.sh &  ç¨åºå°±å¨åå°è¿è¡

jobs  æ¥çåå°ç¨åº
fg 1  jobsçç¼å·1ç¨åºè°ååå°

æ³æåå°ç¨åºè°ååå°å¯ä»¥æCTRL+zç¨åºä¼è°ååå°å¹¶åæ­¢

æ³è®©ç¨åºåè¿è¡å°åå°
fg 1
åå¨åå°å¹¶æ¢å¤è¿è¡
bg 1

```
> manjaro ä¸è½ç´æ¥ä½¿ç¨jobsçç¼å·ï¼è¦ç´æ¥ä½¿ç¨ç¨åºå
> fg ./a.sh è¿ä¸ªæ ·å­

### è¿ç¨é´éä¿¡

* **ä¿¡å·**æ¯è¿ç¨é´éä¿¡æ¹å¼ä¹ä¸ï¼å¸åç¨æ³ï¼è¾å¥ç»ç«¯å½ä»¤ï¼éè¿ä¿¡å·æºå¶åæ­¢æä¸ªç¨åº

* ä½¿ç¨ä¿¡å·çå¸¸ç¨å¿«æ·é®åå½ä»¤
  * kill -l
    * SIGINT éç¥åå°è¿ç¨ç»ç»æ­¢è¿ç¨ Ctrl+c
    * SIGKILL ç«å³ç»æç¨åºï¼ä¸è½è¢«é»å¡åå¤çkill -9 pid
```bash
./a.sh

kill pid  ç»æè¿ç¨
kill -9 pid æ æ¡ä»¶ç»æ(æ è§å µå¡)

```
### å®æ¤è¿ç¨åç³»ç»æ¥å¿

#### å®æ¤è¿ç¨(daemon) 
* ä½¿ç¨nohup ä¸&ç¬¦å·éåè¿è¡ä¸ä¸ªå½ä»¤
  * nohupå½ä»¤ä½¿è¿ç¨å¿½ç¥hangup(æèµ·)ä¿¡å·
  ```bash
  nohup tail -f /var/log/lastlog &
  ```
* å®æ¤è¿ç¨åä¸è¬è¿ç¨çå·®å«

> ç¨åºè¿è¡æ¶ä¼å ç¨å½åç®å½çï¼æä»¥ daemonä¼åæ¢ä¸ºå¨æ ¹ç®å½ä¸è¿è¡,é¿åUçç­æ æ³å¸è½½çé®é¢

> å­¤å¿è¿ç¨ éè¦è¢«å¶ä»è¿ç¨æ¥ç®¡

> ç¨æ·ç»å½ä¹åå¯å¨æå¡ï¼ç±»ä¼¼äºç¶è¿ç¨åå»ºå­è¿ç¨ï¼ç¶åç»æç¶è¿ç¨ï¼å­è¿ç¨ç±1å·è¿ç¨æ¥ç®¡,ç±äºè¿äºç¨åºè¿è¡æ¶æ²¡æç»ç«¯,æä»¥éè¦æå°æ¥å¿æä»¶

> nohup å& åªæ¯æ¨¡æå®æ¤è¿ç¨ï¼ç»ç«¯å³æç¨åºä¹è¿ä¼è¿è¡ 
> æ¬è¯¥å¨ç»ç«¯è¾åºçä¿¡æ¯ä¼å¨nohup.outæä»¶éè¾åº
> ä½æ¯å³æºä¹åç¨è¿ç§æ¹æ³å¯å¨çè¿ç¨ä¸ä¼åæ¬¡èªå¨å¯å¨

procç®å½
> ```
> /proc/ ç®å½å¨ç¡¬çä¸­é»è®¤ä¸å­å¨çï¼æ¯æä½ç³»ç»è¯»ååå­ä¿¡æ¯ï¼ç¶åä»¥æä»¶æ¹å¼åç°çç®å½
> procä¸æåè¿ç¨å·ååçç®å½
> ä¾å¦./a.shè¿è¡çè¿ç¨å·æ¯13906
> ls /proc/13906
> ls -l cwd   å½åè¿è¡ä½ç½®
> ls -l fd  è¾å¥è¾åº  0 è¾å¥ 1,2,3,4 æ åè¾åº
>
> ```

* ä½¿ç¨screenå½ä»¤
  * screen è¿å¥screenç¯å¢
  * ctrl+a d éåº(detached)screenç¯å¢
  * screen -ls æ¥çscreenä¼è¯
  * screen -r sessionid æ¢å¤ä¼è¯
  * exit éåºscreen
#### ç³»ç»æ¥å¿

```bash
cd /var/log/  è¿å¥ç³»ç»æ¥å¿æä»¶ç®å½

ls messages ç³»ç»å¸¸è§æ¥å¿(manjaroæ²¡æï¼å¯¹åºæä»¶æ²¡æ¾å°)

tail -f dmesg åæ ¸è¿è¡ç¸å³ä¿¡æ¯(manjaroæ²¡æ,å¯¹åºæä»¶æ²¡æ¾å°)

tail -f secure  ç³»ç»çå®å¨æ¥å¿

tail -f cron  å¨ææ§ä»»å¡(è®¡åä»»å¡)çæ¥å¿ä¿¡æ¯
```

### æå¡ç®¡çå·¥å·systemctl

* æå¡(æä¾å¸¸è§åè½çå®æ¤è¿ç¨)éä¸­ç®¡çå·¥å·
  * service(Centos6ä»¥å)
    * æ§è¡ç®åï¼æå¡èµ·åç±èªå·±ç¼åèæ¬æ§å¶
    * æå¡æ§å¶èæ¬å¨/etc/init.d/
    * æ¥çç³»ç»å¯å¨æå¡çº§å«chkconfig --list
    * init 0-6
      * 0 å³æº 
      * 1 åç¨æ· 
      * 2 ä¸å¸¦ç½ç»çå¤ç¨æ·
      * 3 å¤ç¨æ·(å­ç¬¦æ¨¡å¼)
      * 4 å¾å½¢æ¨¡å¼
      * 5 å¾å½¢æ¨¡å¼
      * 6 éå¯
    * èµ·åæå¡
          * service SericeName stop/start/restart
      
  * systemctl
    * èæ¬å¤æï¼æå¡èµ·åç®å
    * è½¯ä»¶åå®è£çæå¡æ§å¶èæ¬å¨/usr/lib/systemd/system/
    * ååºsystemdæå¡ systemctl list-unit-files
    * èµ·åæå¡
      * systemctl start|stop|restart|reload ServiceName é¨åæå¡æ¯æä¸éå¯éæ°å è½½éç½®(reload)
      * systemctl |enable|disable ServiceName è®¾ç½®å¼æºèªå¯å¨
      * systemctl status ServiceName  æ¥çæå¡ç¶æ
    * æ¥çæå¡çº§å«  cd /lib/systemd/system/
      * ls *.target -l æ¥çææä¸åçº§å«
      * ls -l runlevel*.target æ¥çç³»ç»å¯å¨çº§å«
      * systemctl get-default æ¥çå½åç³»ç»è¿è¡ççº§å«
      * systemctl set-default multi-user.target è®¾ç½®ä¸ºå­ç¬¦çé¢å¯å¨
    * æå¡å¯å¨èæ¬ /lib/systemd/system/*.service
      * æå¡å¯å¨èæ¬ç¼åå¨shellèæ¬éè¯¦è§£
### SELinuxç®ä»

> SELinuxä¼éä½æ§è½

**å®å¨å¢å¼ºçlinuxçæ¬**
**ä»¥åï¼èªä¸»è®¿é®æ§å¶--ç¨æ·æéåæä»¶æéæ§å¶å®å¨**
* MAC(å¼ºå¶è®¿é®æ§å¶ï¼è¿ç¨ç¨æ·åæä»¶æä¸æ ç­¾ï¼æ ç­¾ä¸è´å°±å¯ä»¥æ§å¶ç³»ç»ï¼ä¸ä¸è´å°±åè®¸è®¿é®)ä¸DAC(èªä¸»è®¿é®æ§å¶)
* æ¥çSELinuxçå½ä»¤
  * getenforce  æ¥çSELinuxç¶æå½ä»¤ /etc/selinux/configæ¯Selinuxéç½®æä»¶
  * /usr/sbin/sestatus  
  * ps -Z and ls -Z and id -Z
* å³é­SELinux
  * setenforce 0  
  * /etc/selinux/sysconfig


## åå­ä¸ç£çç®¡ç

### åå­åç£çä½¿ç¨çæ¥ç
#### åå­ä½¿ç¨çæ¥ç 
* å¸¸ç¨å½ä»¤ä»ç»
  * free éææ¾ç¤ºåå­ä½¿ç¨
  
  ```bash
  free -m æMBæ¾ç¤º 
  free -g æGBæ¾ç¤º
  çavaliable å total
  è¥æ²¡æswap åå­æ»¡æ¶linuxä¼éæºææåå­å ç¨æå¤§çè¿ç¨
  ```
  * top å¨ææ¥çåå­ä½¿ç¨
#### ç£çä½¿ç¨çæ¥ç
* æ¥çå½ä»¤
  * fdisk
  ```bash
  æ¥çç£çä¿¡æ¯
  fdisk -l
  ls -l /dev/sd?

  parted -l
  
  ```
  * df  fdiskçè¡¥å
  ```bash
  df -h çå°ååºåæè½½çç®å½
  
  ```
  * du  å®éå ç¨ç©ºé´
  ```bash
  du /etc/passwd  ä¸æ¾ç¤ºåä½(é»è®¤æ¯KB)
  du -h /etc/passwd æºè½æ¾ç¤ºåä½
  ls -lh /etc/passwd  
  
  ```
  * duålsåºå«
    duæ¥ççæ¯ç©çæºå®éå ç¨çç©ºé´ï¼ä¾å¦åå»ºèææºï¼å®éå¤§å°è¿è¿å°äºlsçå°ç
    æä»¶æç©ºæ´ï¼æ¯æåå»ºæä»¶çå¼å¤´åç»å°¾ï¼ä½æ¯ä¸­é´å¹¶æ²¡æé£ä¹å¤æ°æ®(ç©ºæ´åå®¹)ï¼
  > åå»ºå¸¦ç©ºæ´æä»¶
  > ```bash
  > dd if=afile  bs=4M  count=10 of=bfile ä»aæä»¶éè¯»å4Mæ°æ®å¹¶ä¸è¯»å10æ¬¡ b-->40M
  > dd if=/dev/zero bs=4M count=10 of=bfile è¯»å0 æ¯æ¬¡è¯»å4Mè¯»å10æ¬¡å°bæä»¶ b-->80M
  > dd if=/dev/zero bs=4M count=10 seek=20 of=bfile è¯»å0å°bfileï¼åå»ºbfileå¼å¤´ï¼å¹¶è·³è¿20åï¼åå¼å§åå¥4Mç0 10æ¬¡
  > è¿æ ·ç¨ls -lh bfile æ¯120M du -h bfile æ¯40M
  > ```

### ext4æä»¶ç³»ç»
> linux æ¯æå¤ç§æä»¶ç³»ç»ï¼å¸¸è§çæext4ãxfsãNTFS(éè¦é¢å¤å®è£è½¯ä»¶ntfs-3gï¼ntfsæä»¶ç³»ç»æçæ)
* ext4æä»¶ç³»ç»åºæ¬ç»ææ¯è¾å¤æ
  * è¶çº§å(è®°å½æ´ä¸ªç³»ç»åå«çæä»¶æ°ãå ç¨ç©ºé´)--dfæ¥ççæ¯è¶çº§åä¿¡æ¯
  * è¶çº§åå¯æ¬  ä¿è¯è¶çº§åä¸¢å¤±åå¯æ¢å¤
  * ièç¹(inode) è®°å½æ¯ä¸ä¸ªæä»¶çåç§°(ç±»å?)ãå¤§å°ãç¼å·åæé  lsæ¥ççä¿¡æ¯
  * æ°æ®å(datablock)  è®°å½æ°æ® duæ¥ççä¿¡æ¯(æ°æ®åä¸ºç©º)

* åç§æä»¶æä½å½ä»¤inodeådatablockçæä½
```bash
touch afile åªæièç¹æ²¡ææ°æ®
ls -li afile  æ¥çièç¹ä½¿ç¨æåµ
du -h afile
echo 123 > afile åå¥123å°afile
ls -li afile  å¤§å°ä¸º4ä¸ªå­è
du -h afile å¤§å°ä¸º4K(xfs ext4é»è®¤ä¸ä¸ªæ°æ®åçå¤§å°4Kï¼æä»¥æä¸é¨å­å°æä»¶çæä»¶ç³»ç»)

```

```bash
cp afile afile2
ls -li afile* ièç¹ä¸åäºï¼äº§çä¸¤ä¸ªæä»¶

```

```bash
mv afile2 afile3  æ¹å
ls -li afile* æä»¶åç§°ååï¼ä½æ¯inodeæ²¡æååï¼å³æä»¶æ¬èº«æ²¡æåå

mv afile2 /afile3 ç§»å¨
å¦æç§»å¨å°åä¸ååºï¼éåº¦å¾å¿«ï¼ç§»å¨å°ä¸åååºï¼éåº¦å¾æ¢
```

```bash
vim afile4  åå¥1234
ls -li afile4 è®°ä½inodeä¿¡æ¯
vim afile4  åå¥5678
ls -li afile4 inodeåå,å³çæäºæ°çæä»¶
```

```bash
rm  å é¤æä»¶--æ­å¼æä»¶ååièç¹çé¾æ¥--ä¸ç®¡å é¤å¤å¤§æä»¶é½æ¯ä¸ç¬é´
rm afile4 å é¤afile4

```

```bash
ls -li afile
134493 -rw-r--r-- 1 kamisama kamisama 0  6æ  6 22:42 afile
      1è¡¨ç¤ºæä¸ä¸ªæä»¶åé¾æ¥å°è¿ä¸ªinode
ln afile bfile é¾æ¥bfileå°afileçinode
ls -li afile  
ls -li bfile  ä¸¤ä¸ªçinodeä¸æ ·ï¼æä»¥lnä¸é¢å¤å¢å ç£çå ç¨
lnæ¯ä¸è½è·¨ååº(ç³»ç»ç)ï¼å ä¸ºinodeæ¯å­å¨æä»¶ç³»ç»ä¸é¢çï¼
è·¨è¶ååºè¦ç¨ä¸é¢çè½¯é¾æ¥(ç¬¦å·é¾æ¥)

ls -li afile
ln -s afile aafile  åå»ºè½¯é¾æ¥
ls -li afile aafile inodeä¸ä¸æ ·,aafileè®°å½çæ¯ç®æ æä»¶çè·¯å¾
å¯¹é¾æ¥æåçæéé½ä¼ä¼ éå°é¾æ¥çæä»¶ï¼
ç¬¦å·é¾æ¥(ln -s)å¯ä»¥è·¨ç³»ç»(ååºä½¿ç¨)ï¼ä½æ¯ä¼åå»ºæ°çæä»¶ï¼åé¾æ¥(ln)æ¯æåºå«ç

```

* æä»¶è®¿é®æ§å¶åè¡¨facl
```bash
æ¥çæä»¶è®¿é®æ§å¶åè¡¨
getfacl afile
èµäºæé
setfacl -m u:user1:r afile  ç»user1ç¨æ·åªè¯»æé
ls -l afile
-rw-r--r--+ 2 kamisama kamisama 0  6æ  6 22:42 afile  å å·è¡¨ç¤ºé¤äºæ åæéå¤è¿æfaclæé
getfacl afile
setfacl -m g:group1:r afile ç»ç»èµäºæé
setfacl -x g:group1:r afile æ¶åèµäºçæé
```
### ç£çéé¢çä½¿ç¨
* ç¨æ·ç£çéé¢
      * xfsæä»¶ç³»ç»çç¨æ·ç£çéé¢ quota
        * mkfs.xfs /dev/sdb1
        * mkdir /mnt/disk1
        * mount -o uquota,gquota /dev/sdb1 /mnt/disk1
        * chmod 1777 /mnt/disk1
        * xfs_quota -x -c 'report -ugibh' /mnt/disk1
        * xfs_quota -x -c 'limit -u isoft=5 ihard=10 user1' /mnt/disk1

```bash
fdisk /dev/sdb
  n
  1
  w
mkfs.xfs /dev/sdb1
mkdir -p /mnt/disk1 -på¦æç®å½ä¸å­å¨å°±åå»º
mount -o uquota,gquota /dev/sdb1 /mnt/dski1 ä¸æ¬¡ä¹çæè¦æ´æ¹fstabéç½®æä»¶

mount æ¥ç

chmod 1777 /mnt/disk1

xfs_quota æ¥çç£çéé¢(äº¤äºæ¨¡å¼)
xfs_quota -x -c 'report -ugibh' /mnt/disk1  

xfs_quota -x -c 'limit -u isoft=5 ihard=10 user1' /mnt/disk1

su - user1

id

cd /mnt/disk1

touch 1 2 3 4 5
touch 6   æ¥çç£çéé¢ä¼æ¾ç¤ºå®½éæ¶é´
touch 7 8 9 10
touch 11  æ¾ç¤ºè¶åºç£çéé¢

```
### ç£ççååºåæè½½
* å¸¸ç¨å½ä»¤
  * fdisk ç»ç£çåå»ºååº
  ```bash
  fdisk /dev/sdc  
  m--è·åå¸®å©
  q--ä¸ä¿å­æ´æ¹å¹¶æ¨åº
  w--ä¿å­æ´æ¹éåº
  n--åå»ºæ°ååº
  p--åå»ºä¸»ååº
  1--éæ©çç¬¦1

  ```
  * mkfs ä¸ºååºåå»ºæä»¶ç³»ç»(æ ¼å¼å)
  ```bash
  mkfs.btrfs mkfs.ext2 mkfs.ext4 mkfs.minix mkfs.vfat
  mkfs.cramfs mkfs.ext3 mkfs.fat mkfs.msdos mkfs.xfs
  
  mkfs.ext4 /dev/sdc1
  ```
  * parted ç»å¤§äº2Tçç£çååº
  ```bash
  parted /dev/sdd
  help è·åå¸®å©ï¼ç±»ä¼¼fdisk
  ```
  * mount æè½½
  ```bash
  mkdir /mnt/sdc1
  mount -t ext4 /dev/sdc1 /mnt/sdc1
  mount -t auto /dev/sdc1 /mnt/sdc1
  mount /dev/sdc1 /mnt/sdc1
  ä¸é¢ä¸ä¸ªå½ä»¤ææä¸æ ·ç
  ```
* å¸¸ç¨éç½®æä»¶
  * /etc/fstab
    * ä¸é¢çmountå½ä»¤åªæ¯ä¸´æ¶æè½½è®¾å¤ï¼éå¯åå¤±æ
    * è¦èªå¨æè½½(åºå)å°±è¦ä¿®æ¹/etc/fstabéç½®æä»¶

ä¿®æ¹éç½®æä»¶
```bash
vim /etc/fstab
```
æ·»å è¦æè½½çç£ç
```bash
/dev/sdc1 /mnt/sdc1 ext4 defaults 0 0
```
### äº¤æ¢ååº(èæåå­)çæ¥çä¸åå»º
* å¢å äº¤æ¢ååºçå¤§å°
  * mkswap  æ è®°ååºä¸ºswapååº(ç±»ä¼¼æ ¼å¼å)
  
  * swapon  å¯ç¨swapååº

```bash
free -m 
ls -l /dev/sdd
fdisk /dev/sdd

ls /dev/sdd1

mkswap /dev/sdd1

swapon /dev/sdd1
free -m

swapoff /dev/sdd1
free -m
```

* ä½¿ç¨æä»¶å¶ä½äº¤æ¢ååº
  * dd if=/dev/zero bs=4M count=1024 of=/swapfile     
```bash
dd if=/dev/zero bs=4M count=1024 of=/swapfile   

mkswap /swapfile

ls -l /swapfile

chmod 600 /swapfile

swapon /swapfile

free -m

vim /etc/fstab

åå¥

/swapfile swap swap defaults 0 0
ç¬¬ä¸ä¸ª0éæ©è¦ä¸è¦å¤ä»½ååºï¼ç¬¬äºä¸ªæ¯å¼æºæ¶ç£çèªæ£ï¼æ£æ¥é¡ºåºé®é¢ é»è®¤é½æ¯0å°±å¯ä»¥äº

```
### è½¯ä»¶RAIDçä½¿ç¨
*RAID(ç£çéµå) ä¸RAIDææ¯*

* RAIDçå¸¸è§çº§å«åå«ä¹
  * RAID 0 striping æ¡å¸¦æ¹å¼,æé«åçååç
  * RAID 1 mirroring éåæ¹å¼,æé«å¯é æ§
  * RAID 5 æå¥å¶æ ¡éª ä¸ä¸ªå­æ°æ®ä¸ä¸ªå­æ ¡éªå¼
  * RAID 10 æ¯RAID 1 å RAID 0 çç»å  --éèç¸å³(ä¸¤ä¸ªRAID1 åå»åRAID0)
* è½¯ä»¶RAID çä½¿ç¨
```bash
mdadmå½ä»¤(æ²¡æéè¦å®è£)

/dev/sd* å¤§å°ç¸ç­ --ä½¿ç¨å¤§å°ç¸ç­çç£ç

mdadm -C /dev/md0 -a yes -l1 -n2 /dev/sdb1 /dev/sdc1  RAID1 è¦ä¸¤åç¡¬ç

mdadm -C /dev/md0 -a yes -l1 -n2 /dev/sd[b,c]1  RAID1 è¦ä¸¤åç¡¬ç

mdadm -D /dev/md0 æ¥çRAIDä¿¡æ¯

ç ´åRAID
dd if=/dev/zero of=/dev/sdc1 bs=4M count=1

éç½®æä»¶çè®¾ç½®
echo DEVICE /dev/sd[b,c]1 >> /etc/mdadm.conf
mdadm -Evs >> /etc/mdadm.conf

æ ¼å¼åRAIDè®¾å¤
mkfs.xfs /dev/md0 æ ¼å¼ååå¯ä»¥æè½½äº

```

### é»è¾å·ç®¡ç

* é»è¾å·åæä»¶ç³»ç»çå³ç³» 
* ä¸ºLinuxåå»ºé»è¾å·
* å¨ææ©å®¹é»è¾å·

æ°å»ºé»è¾å·&&å¨çº¿æ©å®¹
```bash
æ°å»ºé»è¾å·
/dev/sdb1 /dev/sdc1 /dev/sdd1 ä¸ä¸ªç¡¬ç

pvcreate /dev/sdb1 /dev/sdc1 /dev/sdd1
pvcreate /dev/sd[b,c,d]1
æ¥éå ä¸ºä¹åsd[b,c]1åå»ºäºRAIDå·

åæRAIDå·ï¼ä¹åååå»ºå°±å¯ä»¥æåäº
mdadm --stop /dev/md0   åæäºè¿è¦æ§æ¯RAIDå³ç³» åºè¯¥åªè¦ä¸é¢ä¸¤æ¡å½ä»¤å°±å¯ä»¥äº

dd if=/dev/zero of=/dev/sdb1 bs=1M count=1  ç ´æè¶çº§å
dd if=/dev/zero of=/dev/sdc1 bs=1M count=1  ç ´æè¶çº§å


pvcreate /dev/sd[b,c,d]1

pvs æ¥ç

åå»ºå·ç»(VG)

vgcreate vg1 /dev/sdb1 /dev/sdc1
ä¸ä¸ªPVä¸è½åæ¶å å¥ä¸¤ä¸ªå·ç»ç
pvs

vgs æ¥çå·ç»


åå»ºé»è¾å·(#LV)
lvcreate -L 100M -n lv1 vg1

lvs æ¥çé»è¾å·

æ ¼å¼åå¹¶æè½½

mkdir /mnt/test

mkfs.xfs /dev/vg1/lv1

mount /dev/vg1/lv1 /mnt/test


æ´ä¸ªè¿ç¨

fdisk /dev/sd?? **pv vg1 lv1**å¯å¨ææ©å± xfsæä»¶æ¹å¼æä½ mountåå­ç®¡çåºç¨


æ©åå®¹é

æ©åå·ç»
vgextend centos /dev/sdd1
pvs
vgs
lvs
æ©åé»è¾å·

lvextend -L +50G /dev/centos/root

lvs

df -h åç°ååºå¹¶æ²¡ææ©å¤§ï¼å ä¸ºæä»¶ç³»ç»æ²¡æè®¤è¯å°èªå·±çååºæ©å¤§äº

æä»¶ç³»ç»
xfs_growfs /dev/centos/root

æä»¶ç³»ç»æ©å¤§äº

df -h

ç¼©å®¹ä¹å¯ä»¥å¨lvä¸å®ç°ï¼ä½æ¯å®ç°ä¼æé£é©ï¼å¯¼è´åºé


```


### ç³»ç»ç»¼åç¶ææ¥ç

* ä½¿ç¨sar å½ä»¤æ¥çç³»ç»ç»¼åç¶æ
* ä½¿ç¨ç¬¬ä¸æ¹å½ä»¤æ¥çç½ç»æµé
  * yum install epel-release 
  * yum install iftop
  * iftop -p


```bash
sar -u 1 10   æ¥çCPU 1så·æ°ï¼æ¥çåæ¬¡
sar -r 1 10   æ¥çåå­
sar -b 1 10 æ¥çI/O
sar -d 1 10   æ¥çç£çè¯»å
sar -q 1 10   æ¥çè¿ç¨ä½¿ç¨


iftop -p  æ¥çç½ç»å½ä»¤ é»è®¤çå¬eth0

```

### shellèæ¬

#### è®¤è¯shell
* ä»ä¹æ¯shell
  * shellæ¯å½ä»¤è§£éå¨ï¼ç¨äºè§£éç¨æ·å¯¹æä½ç³»ç»çæä½
  * shell æå¾å¤
        * cat /etc/shells
  * CentOS 7é»è®¤ä½¿ç¨çshellæ¯bash
        * åºäºbshell éåäºä¸é
* linuxçå¯å¨è¿ç¨(ç³»ç»å¯å¨çshellèæ¬)
  * BIOS-MBR-BootLoader(grub)-Kernel-system-ç³»ç»åå§å-shell

```bash

BIOS
å¼æºæ¶æF2(åä¸ªçµèä¸ä¸æ ·)
```

```bash
MBR

dd if=/dev/sda of=mbr.bin bs=446 count=1

hexdump -c mbr.bin(æ²¡ææä»¶ç³»ç»ï¼ä¸è½ç¨catï¼å¯ä»¥ç¨16è¿å¶æ¥ç -Cè¡¨ç¤ºå°å¯ä»¥æ¾ç¤ºä¸ºå­ç¬¦çæ¾ç¤ºä¸ºå­ç¬¦)

dd if=/dev/sda of=mbr2.bin bs=512 count=1

hexdump -c mbr2.bin | more 
55 aa æ è®°è¡¨ç¤ºå¯å¼å¯¼
```
```bash
GRUB
cd /boot/grub2
ls
grub2-editenv list  
uname -r æ¥çä½¿ç¨åæ ¸
```

```bash
which init (CentOS7 Systemd)
/usr/sbin/init
top -p 1

cd /etc/systmed/system/ é»è®¤å¯å¨çº§å«
cd /usr/lib/systemd/system/ è¯»ååç§service

ls /etc/rc.d/ (CentOs6ç³»ç»èæ¬ï¼æ¿æ´»RAIDç­åå§åæä½)

```

é¤äºå¯å¨è¿ç¨ç¨å°å¤§éçshellèæ¬ä¹å¤ï¼linuxå½ä»¤ä¹æå¾å¤å¨ç¨shellèæ¬

ä¾å¦grub-mkconfigå½ä»¤
```bash
file /sbin/grub-mkconfig

vim /sbin/grub-mkconfig

```

* ææ ·ç¼åä¸ä¸ªshell
  * UNIXå²å­¦ï¼ä¸æ¡å½ä»¤åªåä¸ä»¶äº
  * ä¸ºäºç»åå½ä»¤åå¤æ¬¡æ§è¡ï¼ä½¿ç¨èæ¬æä»¶æ¥ä¿å­éè¦æ§è¡çå½ä»¤
  * èµäºè¯¥æä»¶æ§è¡æé(chmod u+rx filename)


> äºè¿å¶æä»¶åªéè¦èµäºå¯æ§è¡æä»¶ï¼shellèæ¬æä»¶è¿éè¦å¯è¯»æä»¶


```bash
è¿å¥å°æä¸ªç®å½å¹¶æ¥çæåªäºæä»¶
cd /var ; ls
æ¾ç¤ºå½åç®å½è·¯å¾
cd /var ; ls ; pwd
æ¥çå ç¨ç£çç©ºé´å¤§å°
cd /var ; ls ; pwd ; du -sh

cd /var ; ls ; pwd ; du -sh ; du -sh *
```

æ¹æshellèæ¬

vim 1.sh
```shell
cd /var/
ls
pwd
du -sh
du -sh *

```
èµäºå¯æ§è¡æé

```bash
chmod u+x 1.sh
```

æ§è¡èæ¬
```bash
./1.sh    ä½¿ç¨é»è®¤å½ä»¤è§£éå¨æ§è¡
bash 1.sh ç¨bashè§£éå¨æ§è¡
zsh 1.sh  ç¨zshè§£éå¨æ§è¡
```
èæ¬å¨å¶ä»ç¯å¢ä¸è¿è¡ï¼å¦æé»è®¤å½ä»¤è§£éå¨ä¸æ¯bashï¼å¯è½ä¼å¤±è´¥ï¼æä»¥éè¦ä¸äºå£°æ
```bash
#!/bin/bash
#äºå·å¼å¤´ä¼è¢«è®¤ä¸ºæ¯æ³¨éï¼ä½å½ä¸æå®å½ä»¤è§£éå¨æ¶(./1.sh)
#ä¸é¢çå½ä»¤å°±åæäºåè¯ç³»ç»ä½¿ç¨ä»ä¹å½ä»¤è§£éå¨çéæ³¨é
#demo--èæ¬åæ¼ç¤ºç¨
cd /var/
ls
pwd
du -sh
du -sh *

```

* sehllèæ¬çæ§è¡æ¹å¼
  1. bash ./filename.sh å¨å½åç»ç«¯ä¸äº§çbashå­è¿ç¨ï¼å¨bashå­è¿ç¨ä¸è¿è¡
  2. ./filename.sh    ä¹æ¯äº§çå­è¿ç¨åè¿è¡
  3. source ./filename.sh sourceå½ä»¤æ¯å¨å½åè¿ç¨ä¸è¿è¡ç
  4. .filename.sh   .å°±æ¯sourceå½ä»¤çå¦ä¸ç§åæ³

1,2 ä¸å¯¹å½åè¿è¡ç¯å¢äº§çå½±å
3,4 å¯¹å½åè¿è¡ç¯å¢äº§çå½±å

vim 2.sh
```bash
#!/bin/bash
#!/usr/bin/python--ç¨python

# demo 2

cd /tmp
pwd
```

```bash
bash 2.sh
æªèµäºå¯æ§è¡æéä¹è½è¿è¡
å¨èæ¬è¿è¡è¿ç¨ä¸­è¿å¥tmpç®å½ï¼èæ¬éåºååå°åç®å½
```

```bash
./2.sh  æç¤ºæéä¸å¤
chmod u+x 2.sh
./2.sh
```

```bash
source ./2.sh
ç´æ¥è¿å¥tmp

. ./2.sh
ç´æ¥è¿å¥tmp
```


* åå»ºå½ä»¤åå¤é¨å½ä»¤çåºå«

#### ç®¡éä¸éå®å

##### ç®¡éä¸ç®¡éç¬¦
* ç®¡éåä¿¡å·ä¸æ ·ï¼ä¹æ¯è¿ç¨éä¿¡çæ¹å¼ä¹ä¸
* å¿åç®¡é(ç®¡éç¬¦)æ¯shellç¼ç¨ç»å¸¸ç¨å°çéä¿¡å·¥å·
* ç®¡éç¬¦æ¯"|",å°åä¸ä¸ªå½ä»¤çæ§è¡ç»æä¼ éç»åé¢çå½ä»¤
      * ps | cat 
  * echo 123 | ps

ç®¡éç¬¦ä½¿ç¨
```bash
ls -l |more
ls -l å½ä»¤çæ§è¡ç»æä¼ éç»åé¢çå½ä»¤ 
åå°åé¢å½ä»¤(more)çæ§è¡ç»æå½ä½æç»æ§è¡ç»æ
```
> ;å|
> ; éå¼ä¸¤æ¡å½ä»¤ï¼| å°ç¬¬ä¸æ¡å½ä»¤çè¾åºä½ä¸ºç¬¬äºæ¡å½ä»¤çè¾å¥
> ç®¡éç¬¦æ¯éè¿å­è¿ç¨è¿è¡çï¼æä»¥è¦å°½éå«ä½¿ç¨cd pwdç­åå»ºå½ä»¤

##### å­è¿ç¨ä¸å­shell

```bash
cat | ps -f
å¯ä»¥çå°zsh(bash)çpidä¸æä¸¤ä¸ªpidç¸é»çå­è¿ç¨cat åps

è¥åå»ºçå­è¿ç¨æ¯shellèæ¬(1.sh)ï¼éå¸¸ç§°è¿ç§å­è¿ç¨å«å­shell

ç±äºç®¡éç¬¦æ¯éè¿å­è¿ç¨æ¹å¼è¿è¡çï¼æä»¥å¦æä½¿ç¨äºcd pwdç­åé¨å½ä»¤
æ§è¡å®æåï¼å½åç¶è¿ç¨æ¯ä¸ä¼åçååç

```

```bash
cat | ps -l
æ°å¼ç»ç«¯
cd /proc/14486  (åè®¾catçPIDä¸º14486)
cd fd
ls -l
æ åè¾å¥(0)/æ åè¾åº(1)/éè¯¯è¾åº(2) 3ä¸ªæä»¶æè¿°ç¬¦
å¯ä»¥çå° 1æ¯\'pipe[1234]\' æ¾ç¤ºä¸ºç®¡éç¬¦å·

```

##### éå®åç¬¦å·

* ä¸ä¸ªè¿ç¨é»è®¤ä¼æå¼æ åè¾å¥ãæ åè¾åºãéè¯¯è¾åºä¸ä¸ªæä»¶æè¿°ç¬¦
* è¾å¥éå®åç¬¦å· "<" 
  * read var < /path/to/a/file

* è¾åºéå®åç¬¦å· ">" ">>" "2>" "&>"
  * echo 123 > /path/to/a/file

* è¾å¥åè¾åºéå®åç»åä½¿ç¨
  * cat > /path/to/a/file << EOF
  * I am $USER
  * EOF

| å½ä»¤ è¯´æ |                                                                                                                                               |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| command > file         | å°è¾åºéå®åå° fileãÂ                                                                           |
| command < file         | å°è¾å¥éå®åå° fileã                                                                            |
| command >> file        | å°è¾åºä»¥è¿½å çæ¹å¼éå®åå° fileãÂ                                          |
| n > file               | å°æä»¶æè¿°ç¬¦ä¸º n çæä»¶éå®åå° fileã                                  |
| n >> file              | å°æä»¶æè¿°ç¬¦ä¸º n çæä»¶ä»¥è¿½å çæ¹å¼éå®åå° fileã |
| n >& m                 | å°è¾åºæä»¶ m å n åå¹¶ãÂ                                                                       |
| n <& m                 | å°è¾å¥æä»¶ m å n åå¹¶ãÂ                                                                       |
| << tag                 | å°å¼å§æ è®° tag åç»ææ è®° tag ä¹é´çåå®¹ä½ä¸ºè¾å¥ãÂ    |
