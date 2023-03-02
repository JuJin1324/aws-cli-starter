# aws-cli-starter
> aws cli 를 사용한 AWS 접근

## 시작하기
### 설치
> macOS: `brew install awscli`  
> Ubuntu: `sudo apt install -y awscli`

### 계정 설정  
> default 계정 설정: `aws configure`   
> 원하는 프로파일 계정 설정: `aws configure --profile <원하는 프로파일 명>`    
> ``` shell
> AWS Access Key ID [None]: 엑세스 키 입력
> AWS Secret Access Key [None]: 시크릿 키 입력
> Default region name [None]: ap-northeast-2
> Default output format [None]: json
> ```
>
> 멀티 계정을 만든 경우 aws-cli 사용시 항상 마지막에 `--profile 프로파일명`을 붙여준다.  

### 설정 확인
> 계정 설정은 `~/.aws` 디렉터리에서 `credentials` 파일을 통해서 확인할 수 있다.  

---

## Amazon EC2
### instance
> 간단 조회: `aws ec2 describe-instances --filters --query "Reservations[].Instances[].[PrivateIpAddress,Tags[?Key=='Name'].Value[]]" --output text --profile <프로파일>`  
> 상세 조회
> ```shell
> aws ec2 describe-instances --query 'Reservations[].Instances[].[InstanceId,
> Tags[?Key==`Name`].Value[],PrivateIpAddress,PublicIpAddress,InstanceType,
> Placement.AvailabilityZone,State.Name,LaunchTime,SubnetId]' \
> --profile <프로파일>
> ```
> 참조사이트: [AWS CLI EC2 List](https://sarc.io/index.php/aws/1022-aws-cli-ec2-list)

### Elastic Block Storage
> 전체 조회: `aws ec2 describe-volumes --query 'Volumes[].[Attachments[].InstanceId,VolumeId,VolumeType,Iops,Size]' --profile <프로파일>`
> 상태가 available or delete or error 볼륨 필터
> ```shell
> aws ec2 describe-volumes --filters "Name=status,Values=available" "Name=status,Values=deleted" "Name=status,Values=error" \
> --query 'Volumes[].[VolumeId,VolumeType,Iops,Size]' \
> --profile <프로파일>
> ```

### Load Balancer
> TODO

---

## Amazon RDS
### cluster
> 조회: `aws rds describe-db-clusters`

### instance
> 조회: `aws rds describe-db-instances`

### snapshot
> 조회: `aws rds describe-db-snapshots`
