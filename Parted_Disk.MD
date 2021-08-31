#### Parted_Command /bin/bash Shell

##### 전제: 디스크는 8개가 있고 모두 raid가 가능하도록 구성하시오.
```bash
apt install -y mdadm parted
```
이후 쉘 스크립트 생성
```bash
vim /part.sh
```
```bash
#!/bin/bash
for a in {b..i}
do
        parted --script /dev/sd$a "mklabel gpt"
        parted --script /dev/sd$a "mkpart primary 0 100%"
        parted --script /dev/sd$a "set 1 raid on"
        parted --script /dev/sd$a "unit gb"
done
```
이후 Permison을 주고 실행한다.
```bash
chmod 777 /part.sh
/part.sh
```
#### 명령어 해석
``for a in {b..i}do~done`` : 디스크를 추가하면 자동으로 sdb,c,d..순으로 생기니 8개의 디스크니까 b,c,d,e,f,g,h,i로 생기기때문에 지정

``parted --script /dev/sd$a "mklabel gpt"`` : VM에서 디스크를 삽입하면 자동으로 mgr로 인식하기 때문에 gpt로 변경해주는 명령어

``parted --script /dev/sd$a "mkpart primary 0 100%"`` : 디스크에서 파티션을 0으로 생성하고 여기에 모든디스크의 용량을 할당한다. 윈도우로 치면 디스크가 만약에 할당되어있다면 모든 용량을 C:\에 할당하는 것과 같은 이치
