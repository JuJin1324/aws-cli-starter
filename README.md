# AWS-CLI-Starter
AWS CLI를 사용한 AWS 접근

## 설치 및 환경설정
### macOS
설치: `brew install aws-cli`   
설정
* [IAM](https://console.aws.amazon.com/iam/home?region=ap-northeast-2#/home) 접속   
* (엑세스 키가 이미 있는 경우 건너뛰기)우측 메뉴에 엑세스 관리 -> 사용자 -> AWS-CLI로 로그인할 사용자 클릭 -> 보안 자격 증명 탭 -> 액세스 키 만들기
* 하나의 계정만 사용할 경우: `aws configure`
* 멀티 계정 사용하고 싶은 경우: `aws configure --profile 원하는 프로파일 명`
``` shell
AWS Access Key ID [None]: 엑세스 키 입력
AWS Secret Access Key [None]: 시크릿 키 입력
Default region name [None]: ap-northeast-2
Default output format [None]: json
```

* 멀티 계정을 만든 경우 aws-cli 사용시 항상 마지막에 `--profile 프로파일명`을 붙여준다.

## IAM
### Group
* 그룹 확인: `aws iam list-groups --profile 프로파일명`
* 그룹 추가: `aws iam create-group --group-name Administrator --profile 프로파일명`

### Role
* 롤 확인: `aws iam list-roles --profile 프로파일명`  
* 롤 추가: `aws iam create-role --role-name 롤이름 --assume-role-policy-document file://Test-Role-Trust-Policy.json --profile 프로파일명`
