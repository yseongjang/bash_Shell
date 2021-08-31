#### Add_User in /bin/bash shell

##### 전제: user001~user100의 유저를 만들고 로그인할 수 있게 구성한다. 나머지 값은 아래를 참조
-   User: user001~user100
-   uid : 1001~1100
-   gid : nogroup(65534)
-   home-Diectory : /var/home/user001~100

```bash
vim /user.sh
```
```bash
#/bin/bash
mkdir /var/home
for a in {001..100}
do
    echo -e 'Skill39\nSkill39' | adduser --gecos "" --uid 1$a  --gid 65534 --home var/home/user$a user$a 
done
```
이후 Permition을 주고 실행한다.
```bash
chmod 777 /user.sh
/user.sh
```
