# Eatake GitHub Guide

## 목차
1. [신규 직원 초대 방법](#신규-직원-초대-방법)
2. [팀원으로 초대 방법](#팀원으로-초대-방법)
3. [레포지토리 생성 및 설정](#레포지토리-생성-및-설정)
4. [로컬 프로젝트와 레포지토리 연결](#로컬-프로젝트와-레포지토리-연결)
5. [형상 관리 원칙](#형상-관리-원칙)
6. [자주 사용하는 Git 명령어](#자주-사용하는-git-명령어)
7. [Merge 방법](#merge-방법)

---

## 신규 직원 초대 방법
1. **GitHub Organization에 로그인**합니다.
2. 우측 상단의 **Settings** → **People** 메뉴로 이동합니다.
3. **Invite Member** 버튼을 클릭합니다.
4. **신규 직원의 GitHub 이메일**을 입력하고, **Role**을 `Owner`로 설정하여 초대합니다.
5. 초대가 수락되면 해당 직원이 Organization에 추가됩니다.

## 팀원으로 초대 방법
1. 초대가 수락된 신규 직원이 Organization에 추가되면, **Teams** 메뉴로 이동합니다.
2. **develope** 팀을 선택한 후, **Add a member** 버튼을 클릭하여 **신규 직원을 팀원으로 추가**합니다.

## 레포지토리 생성 및 설정
1. Organization 내에서 **New Repository** 버튼을 클릭하여 새로운 레포지토리를 생성합니다.
2. 레포지토리 이름을 입력하고 **Create repository** 버튼을 클릭합니다.
3. **Settings** → **Manage access**로 이동하여 **develope** 팀에게 `Write` 권한을 부여합니다.

## 로컬 프로젝트와 레포지토리 연결
1. 로컬 프로젝트가 준비된 상태에서, 아래의 명령어를 사용하여 GitHub 레포지토리와 연결합니다:
   ```bash
   git init
   git remote add origin https://github.com/your-organization/your-repository.git
   git add .
   git commit -m "Initial commit"
   git push -u origin main
   ```
2.	이미 로컬 프로젝트에 Git이 초기화되어 있다면:
   ```bash
    git remote set-url origin https://github.com/your-organization/your-repository.git
   ```

## 형상 관리 원칙
- main 브랜치: 배포용 브랜치입니다. 실제 배포가 필요한 코드만 main 브랜치로 머지합니다.
- develope 브랜치: 최종 작업 브랜치로, 모든 기능 개발이 완료되면 develope 브랜치로 머지합니다.
- 협업 시 브랜치 전략:
  1. 각자 develope 브랜치에서 새로운 브랜치를 생성하여 작업을 시작합니다. 브랜치 이름은 feature/기능명 또는 bugfix/이슈번호 등으로 작성합니다.
  2. **작업이 완료되면, 본인의 브랜치를 develope 브랜치로 PR(Pull Request)**을 작성하고, 코드 리뷰 후 머지합니다.
  3. 최종 배포가 필요한 경우, develope 브랜치를 main 브랜치로 머지하여 배포합니다.
     
## 자주 사용하는 Git 명령어

- 브렌치 생성 및 이동:
  ```bash
  git checkout -b feature/기능명
  ```
- 브렌치 목록 확인:
  ```bash
  git branch
  ```
- 변경 사항 확인:
  ```bash
  git status
  ```
- 변경 사항 커밋:
  ```bash
  git add .
  git commit -m "작업 내용"
  ```
- 브렌치 푸시:
  ```bash
  git push origin 브랜치명
  ```
- 로컬 브렌치 삭제:
  ```bash
  git branch -d 브랜치명
  ```
- 원격 브렌치 삭제:
  ```bash
  git push origin --delete 브랜치명
  ```

  ## Merge 방법

  1. 작업 브렌치에서 develope 브렌치로 Pull Request를 생성합니다.
  2. 코드 리뷰를 요청하고 필요한 경우 수정합니다.
  3. 코드 리뷰가 완료되면 PR을 머지합니다.
  4. 최종 배포 시, develope 브렌치의 코드를 main 브렌치로 머지합니다:
     ```bash
     git checkout main
     git merge develope
     git push origin main
     ```
  
