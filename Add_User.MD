#### Add_User in /bin/bash shell

##### 전제: user001~user100의 유저를 만들고 로그인할 수 있게 구성한다. 나머지 값은 아래를 참조
-   User: user001~user100
-   Password: Skill39
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
    echo -e 'Skill39\nSkill39' | adduser --gecos "" --uid 1$a  --gid 65534 --home /var/home/user$a user$a 
done
```
이후 Permition을 주고 실행한다.
```bash
chmod 777 /user.sh
/user.sh
```

##### 설명:
- ``for a in {001..100}do~done`` : $a라는 변수라는 값에 000~100값을 넣어 do~done스크립트를 실행한다.
-   ``echo -e 'Skill39\nSkill39'`` : 비밀번호인데 Skill39사이에 \n 있는 이유는 줄바꿈으로 adduser를 할 때 비번을 두번 치기 때문이다.
-   ``--gecos ""`` : 유저를 생성할 때 물어보는 막 전화번호 이런 등등 이상한거 스킵
-   ``--uid 1$a`` : 유저의 uid를  for문으로 계속 실행하기 때문에 해당 유저의 uid가 들어감
-   ``--gid 65534`` : nogroup의 gid가 65534 임
-   ``--home /var/home/user$a`` : user의 홈디렉토리 지정
-   ``user$a`` = 유저의 이름 지정
