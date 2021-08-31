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
```bash
chmod 777 /part.sh
```
이후 실행
```bash
/part.sh
```
