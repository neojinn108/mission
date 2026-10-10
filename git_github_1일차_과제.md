# Git / GitHub 복습 노트

이번 수업은 Git 명령어 자체를 외우는 것보다  
**파일을 수정하고, 기록하고, 다른 사람과 공유하는 흐름을 이해하는 것**이 더 중요하게 느껴졌다.

처음에는 `git add`, `git commit`, `git push`가 다 비슷한 동작처럼 보였는데  
각 단계가 서로 다른 역할을 한다는 점이 핵심이었다.

---

## 1. 왜 Git과 GitHub를 같이 쓰는가

개발을 하다 보면 파일이 계속 바뀐다.

예를 들어 코드를 수정했는데 문제가 생겼거나,  
예전 상태로 돌아가고 싶거나,  
여러 사람이 같은 프로젝트를 같이 수정해야 할 수도 있다.

이럴 때 Git을 사용하면 변경 내용을 기록하면서 작업할 수 있다.

내가 이해한 Git의 역할은 다음과 같다.

- 파일 변경 이력을 남긴다.
- 특정 시점의 상태를 기록할 수 있다.
- 여러 작업을 브랜치로 나눠서 진행할 수 있다.
- 문제가 생겼을 때 이전 기록을 확인하기 쉽다.

GitHub는 Git으로 관리하는 프로젝트를  
온라인에서 저장하고 공유할 수 있게 해주는 서비스이다.

즉,

**Git = 버전 관리 도구**

**GitHub = Git 저장소를 온라인에서 관리하고 공유하는 서비스**

라고 정리했다.

---

## 2. Git과 GitHub는 같은 것이 아니다

둘을 같이 쓰는 경우가 많아서 처음에는 같은 개념처럼 느껴졌지만  
역할이 다르다.

Git은 내 컴퓨터 안에서도 사용할 수 있다.

예를 들어 인터넷이 연결되지 않은 상태에서도

```bash
git init
git add .
git commit -m "first commit"
```

같은 작업은 가능하다.

반면 GitHub는 원격 저장소를 제공한다.

내 컴퓨터에서 만든 Git 기록을 GitHub에 올리려면

```bash
git push
```

를 사용한다.

정리하면,

- Git: 로컬에서 변경 이력 관리
- GitHub: 원격 저장소, 협업, 공유

---

## 3. Repository는 프로젝트 기록을 담는 공간

Repository는 Git으로 관리하는 저장소이다.

단순히 파일만 들어있는 폴더가 아니라  
그 파일의 변경 기록까지 같이 관리하는 공간이라고 이해했다.

Repository는 크게 두 종류로 볼 수 있다.

### Local Repository

내 컴퓨터 안에 있는 저장소

### Remote Repository

GitHub 같은 곳에 있는 원격 저장소

보통은 로컬에서 작업하고  
필요한 시점에 GitHub로 올린다.

흐름을 단순하게 보면

```text
내 컴퓨터에서 파일 수정
        ↓
Git으로 기록
        ↓
Local Repository
        ↓
git push
        ↓
GitHub Repository
```

---

## 4. Commit은 작업 내용을 기록하는 시점

Commit은 현재 변경 내용을 하나의 기록으로 남기는 작업이다.

파일을 수정했다고 해서 바로 Git 기록이 되는 것은 아니다.

먼저 변경된 파일을 선택하고  
그 다음 commit을 만들어야 한다.

예를 들어

```bash
git add app.py
git commit -m "로그인 기능 수정"
```

처럼 사용할 수 있다.

여기서 commit message는  
나중에 기록을 봤을 때 어떤 작업을 했는지 알 수 있게 적는 것이 좋다.

예)

```bash
git commit -m "회원가입 페이지 추가"
git commit -m "로그인 오류 수정"
git commit -m "README 내용 수정"
```

너무 의미 없는 메시지보다  
작업 내용을 알아볼 수 있게 쓰는 것이 관리하기 편하다.

---

## 5. Branch는 작업 공간을 나누는 방법

한 프로젝트에서 여러 작업을 동시에 진행할 때  
모든 변경을 main 브랜치에서 바로 작업하면 위험할 수 있다.

새 기능을 만들다가 코드가 깨질 수도 있기 때문이다.

그래서 Branch를 사용한다.

내가 이해한 Branch는

**기존 프로젝트에서 갈라져 나온 별도의 작업 흐름**

이다.

예를 들어

```text
main
 |
 |---- feature/login
 |
 |---- feature/payment
```

처럼 로그인 기능과 결제 기능을 따로 작업할 수 있다.

작업이 끝난 뒤 필요한 브랜치를 다시 합친다.

---

# Git 기본 명령어를 실제 작업 순서로 보기

이번 수업에서 배운 명령어는  
따로 외우는 것보다 실제 작업 순서로 보는 것이 이해하기 쉬웠다.

---

## 6. git config

Git을 처음 사용할 때 사용자 정보를 설정한다.

예)

```bash
git config --global user.name "Kim"
git config --global user.email "kim@example.com"
```

commit 기록에 누가 작업했는지 남기기 위해 사용하는 정보이다.

설정 내용을 확인할 수도 있다.

```bash
git config --list
```

---

## 7. git init

현재 폴더를 Git으로 관리하기 시작할 때 사용한다.

```bash
git init
```

이 명령어를 실행하면  
해당 폴더가 Git Repository가 된다.

보통 새 프로젝트 폴더에서 처음 한 번 실행한다.

---

## 8. git status

현재 파일 상태를 확인한다.

```bash
git status
```

파일을 수정한 뒤 가장 자주 확인하게 되는 명령어 중 하나라고 느꼈다.

현재

- 어떤 파일이 수정됐는지
- 어떤 파일이 아직 add되지 않았는지
- 어떤 파일이 commit 준비 상태인지

확인할 수 있다.

작업 중 헷갈릴 때 일단 `git status`를 확인하는 습관이 중요해 보였다.

---

## 9. git add

수정한 파일을 commit할 대상으로 선택한다.

파일 하나만 선택

```bash
git add app.py
```

여러 변경 사항을 한 번에 선택

```bash
git add .
```

여기서 중요한 점은  
`git add`가 최종 저장은 아니라는 것이다.

commit하기 전에

**이번 기록에 어떤 변경을 포함할지 고르는 단계**

라고 이해했다.

---

## 10. git commit

add한 변경 내용을 실제 Git 기록으로 남긴다.

```bash
git commit -m "회원가입 기능 추가"
```

즉,

```text
파일 수정
↓
git add
↓
git commit
```

순서로 진행된다.

---

## 11. git push

로컬에서 만든 commit을  
GitHub 같은 Remote Repository로 올릴 때 사용한다.

```bash
git push
```

처음 연결된 브랜치를 올릴 때는 상황에 따라

```bash
git push -u origin main
```

처럼 사용할 수도 있다.

내 컴퓨터 안에만 commit이 있어서는  
다른 사람이 GitHub에서 볼 수 없기 때문에  
원격 저장소에 공유하려면 push가 필요하다.

---

## 12. git pull

Remote Repository의 최신 내용을  
내 Local Repository로 가져올 때 사용한다.

```bash
git pull
```

팀 작업에서는 다른 사람이 먼저 작업한 내용이 있을 수 있기 때문에  
작업 전에 최신 내용을 pull해서 맞춰주는 것이 중요하다.

내가 이해한 흐름은

```text
GitHub 최신 내용
      ↓
   git pull
      ↓
내 컴퓨터에서 작업
      ↓
   git add
      ↓
  git commit
      ↓
   git push
      ↓
GitHub에 반영
```

이다.

---

# Branch 실습 정리

## 13. git branch

현재 브랜치를 확인할 수 있다.

```bash
git branch
```

새 브랜치를 만들 수도 있다.

```bash
git branch feature/login
```

브랜치를 이동할 때는

```bash
git switch feature/login
```

처럼 사용할 수 있다.

브랜치를 만들면서 바로 이동하려면

```bash
git switch -c feature/login
```

처럼 사용할 수 있다.

수업 과제 목록에는 `git branch`가 중심이지만  
실제로는 브랜치를 만든 뒤 이동하는 과정도 같이 이해해야 했다.

---

## 14. 브랜치 이름은 역할에 따라 나눌 수 있다

프로젝트마다 방식은 다를 수 있지만  
대표적으로 다음과 같이 나눠서 관리할 수 있다.

### main

실제로 배포 가능한 안정적인 코드가 있는 브랜치

### develop

다음 배포를 준비하면서 여러 기능을 모으는 브랜치

### feature

새로운 기능을 개발할 때 사용하는 브랜치

예)

```text
feature/login
feature/payment
feature/search
```

### release

배포 직전에 마지막 점검이나 수정 작업을 하는 브랜치

### hotfix

운영 중인 서비스에서 급하게 수정해야 하는 문제가 생겼을 때 사용하는 브랜치

예)

```text
hotfix/login-error
```

모든 프로젝트가 반드시 이 구조를 그대로 쓰는 것은 아니지만  
브랜치를 역할에 따라 나누면  
여러 작업이 한곳에서 뒤섞이는 것을 줄일 수 있다.

---

# Merge는 다시 합치는 과정

Branch를 나눠서 작업했다면  
작업이 끝난 뒤 다시 합치는 과정이 필요하다.

이 과정이 merge이다.

---

## 15. Fast-forward merge

두 브랜치가 갈라진 뒤  
기준 브랜치에는 새로운 commit이 없고  
한쪽 브랜치만 앞으로 진행된 경우이다.

예)

```text
A --- B
      \
       C --- D
```

main이 B에 있고  
feature 브랜치가 C, D까지 진행됐다고 생각하면 된다.

이 경우 main이 D까지 이동하면 되기 때문에  
별도의 merge commit 없이 합칠 수 있다.

결과

```text
A --- B --- C --- D
```

브랜치가 단순히 앞으로 이동하는 느낌이라  
Fast-forward라고 이해했다.

---

## 16. 3-way merge

두 브랜치 모두 각자 commit이 생긴 경우에는  
단순히 포인터만 이동해서 합칠 수 없다.

예)

```text
        C --- D
       /
A --- B
       \
        E --- F
```

한쪽에서는 C, D가 생기고  
다른 쪽에서는 E, F가 생긴 상태이다.

이 경우 공통 조상인 B와  
두 브랜치의 최신 상태를 비교해서 merge한다.

결과적으로 새로운 merge commit이 생길 수 있다.

```text
        C --- D
       /       \
A --- B         M
       \       /
        E --- F
```

이런 병합 방식을 3-way merge라고 한다.

---

## 17. Merge conflict

Merge를 한다고 해서 항상 자동으로 잘 합쳐지는 것은 아니다.

두 브랜치가 같은 파일의 같은 부분을 서로 다르게 수정했다면  
Git이 어느 내용을 선택해야 할지 결정하지 못할 수 있다.

이때 Merge conflict가 발생한다.

예를 들어

main에서는

```python
title = "Hello"
```

로 수정했고,

feature 브랜치에서는

```python
title = "Welcome"
```

로 수정했다면

같은 위치의 내용이 달라서 충돌이 날 수 있다.

이 경우 개발자가 직접 파일을 확인해서  
어떤 내용을 사용할지 결정해야 한다.

충돌을 해결한 뒤에는 다시

```bash
git add .
git commit
```

을 진행하면 된다.

즉, conflict는 오류라기보다

**Git이 자동으로 판단할 수 없으니 사람이 선택해야 하는 상황**

이라고 이해했다.

---

# 내가 정리한 실제 Git 작업 흐름

처음 프로젝트를 만든다면

```bash
git config --global user.name "Kim"
git config --global user.email "kim@example.com"

git init
```

파일을 만든 뒤

```bash
git status
git add .
git commit -m "첫 번째 작업"
```

GitHub Repository와 연결되어 있다면

```bash
git push
```

새 기능을 따로 작업하고 싶다면

```bash
git switch -c feature/login
```

작업 후

```bash
git add .
git commit -m "로그인 기능 추가"
```

그리고 main 또는 develop 브랜치에 merge한다.

팀 작업이라면 작업 전후로  
원격 저장소의 최신 상태도 확인해야 한다.

```bash
git pull
git push
```

---

# 이번 수업에서 가장 헷갈렸던 부분

## add와 commit

처음에는 둘 다 저장하는 명령어처럼 느껴졌다.

하지만

```text
git add
→ commit에 포함할 변경을 선택

git commit
→ 선택한 변경을 하나의 기록으로 저장
```

으로 구분할 수 있었다.

---

## commit과 push

commit은 내 컴퓨터에 기록하는 작업이고  
push는 그 기록을 GitHub로 보내는 작업이다.

```text
commit = Local Repository

push = Local → Remote Repository
```

---

## branch와 repository

Repository는 프로젝트 전체를 관리하는 저장소이고,  
Branch는 그 Repository 안에서 나뉘는 작업 흐름이다.

즉 Branch마다 별도의 Repository가 생기는 것은 아니다.

---

## pull과 push

```text
pull
GitHub → 내 컴퓨터

push
내 컴퓨터 → GitHub
```

방향이 반대라고 기억하면 구분하기 쉽다.

---

# 최종 정리

Git은 코드를 단순히 저장하는 도구가 아니라  
변경 이력을 관리하는 도구이다.

작업 흐름을 가장 짧게 정리하면

```text
파일 수정
↓
git status
↓
git add
↓
git commit
↓
git push
```

이다.

협업에서는 여기에 Branch가 추가된다.

```text
main
↓
새 Branch 생성
↓
기능 작업
↓
commit
↓
merge
↓
main에 반영
```

그리고 merge할 때  
두 브랜치의 진행 상황에 따라 Fast-forward가 될 수도 있고  
3-way merge가 될 수도 있다.

같은 부분을 서로 다르게 수정했다면  
Merge conflict가 발생하고  
그때는 개발자가 직접 내용을 확인해서 해결해야 한다.

이번 수업을 통해 Git 명령어를 각각 외우는 것보다  
**변경 내용을 선택하고(add), 기록하고(commit), 공유하고(push),  
작업을 나누고(branch), 다시 합치는(merge) 흐름으로 이해하는 것이 훨씬 중요하다**고 정리했다.
