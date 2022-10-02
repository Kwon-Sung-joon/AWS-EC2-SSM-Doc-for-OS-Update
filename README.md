# AWS-EC2-SSM-Documenrt

## SSM을 통한 원격 명령 수행
- [Systems Manager 사전 조건 충족](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/systems-manager-prereqs.html)
- EC2 OS Update 수행
- 고객이 보유한 인스턴스의 OS가 다를 경우도 효율적으로 Update명령을 수행할 것 
- Test OS : Amazon Linux2, Ubuntu, SUSE Linux, Redhat


## [SSM 문서 생성 후 해당 문서로 명령 실행](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/sysman-ssm-docs.html)
- AWS SSM Run Command 사용
- [Precondition 파라미터로 교차 플랫폼 지원](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/document-schemas-features.html)
- 리눅스도 Ubuntu, CentOS, SUSE 등 다양하기 때문에 스크립트로 각 OS마다 다른 명령어 실행
- Ubuntu, SUSE 등 인스턴스 실행 시 SSM Agent가 자동으로 실행되지 않는 OS는 직접 SSM agent 설치 후 실행해줘야 SSM Run Command 사용 가능


## 	AWS SSM 문서 생성


![image](https://user-images.githubusercontent.com/43159901/193452143-8cba749f-a81c-4f0e-9a28-f1e0d77f31ac.png)
##  AWS SSM 문서 생성 확인

![image](https://user-images.githubusercontent.com/43159901/193452254-46ef491e-31e2-419d-a486-ed3eeb6f845e.png)
[SSMDocsContents.yaml](https://github.com/Kwon-Sung-joon/AWS-EC2-SSM-Doc-for-OS-Update/blob/main/SSM-Docs.yaml)
![image](https://user-images.githubusercontent.com/43159901/193452619-c3208304-2489-412d-89ee-a19add50260a.png)


## 해당 문서로 AWS SSM Run Command 사용

![image](https://user-images.githubusercontent.com/43159901/193452264-ff3ad00a-03ca-4e2c-8f4b-cc098b2fb1cf.png)
![image](https://user-images.githubusercontent.com/43159901/193452267-7891805d-45d4-4da0-9c50-bdf957583740.png)
### 대상 지정시 Owner 태그 값으로 인스턴스 지정 후 실행 (수동 선택 가능)
![image](https://user-images.githubusercontent.com/43159901/193452278-daa68a2e-4069-4f7d-95ae-2ddc5a8287e1.png)

### 명령 실행 시 화면
![image](https://user-images.githubusercontent.com/43159901/193452287-e050a194-8589-4771-ba7c-cb1921ea6a63.png)
### 각 대상의 출력값 확인 가능

![image](https://user-images.githubusercontent.com/43159901/193452299-9e73e55b-ae94-421c-abb6-358e22944a9d.png)


# Concluding
- SSM을 사용하여 여러 EC2에 한번에 명령어를 실행할 수 있다.
- SSM을 사용하려면 EC2는 다음과 같은 조건을 충족해야만 한다.
	- 필요한 IAM 역할 사용
	- 지원되는 운영 체제 사용
	- SSM Agent 실행확인 
- SSM 문서를 생성하여 실행 할 명령어를 세부적으로 지정할 수 있다.
- 생성한 SSM 문서를 기반으로 SSM Run Command를 하여 EC2에 명령어를 수행한다.
- SSM 명령 실행 시 대상으로 인스턴스의 태그를 기반으로 지정할 수 있다. ( 수동도 가능)
- SSM 명령 실행 후 명령 ID를 통해 대상의 명령 실행 후 출력, 에러가 있다면 에러까지 확인할 수 있다.
