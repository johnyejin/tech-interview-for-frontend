# CI와 CD
## CI (Continuous Integration, 지속적 통합)
CI는 **빌드와 테스트를 자동화**해서 공유 저장소에 병합시키는 프로세스를 뜻한다.

<br>

## CD (Continuous Delivery/Deploy, 지속적 전달/배포)
CD는 CI의 빌드/테스트를 통해 정상적으로 수행됨을 확인하면 배포를 수동으로 하냐, 자동으로 하냐에 따라 2가지로 나뉜다.

### 지속적 전달
프로덕션 배포를 위한 상태가 되고 **배포 자체는 수동**으로 실행한다. 개발팀과 비즈니스팀 간의 커뮤니케이션 부족 문제를 해결한다.

### 지속적 배포
**프로덕션까지 자동으로 배포**한다. 애플리케이션의 제공 속도를 증가시킨다.

<br>

## 대표적인 CI/CD 서비스
- Jenkins
- Travis CI
- Circle CI

![CI 프로세스](https://user-images.githubusercontent.com/26537048/111457949-2f958080-875c-11eb-81bb-343317af529b.png)

위의 그림은 지속적 통합 프로세스가 동작하는 과정을 그린 것이다. 지속적 통합은 소프트웨어 릴리즈 프로세스 중 빌드 및 유닛 테스트 단계를 지칭한다. 수정 버전이 커밋될 때마다 자동화된 빌드 및 테스트가 트리거된다.


<br>

## 참고
- [AWS | 지속적 통합이란 무엇입니까?](https://aws.amazon.com/ko/devops/continuous-integration/)
- [Github | CI와 CD](https://github.com/baeharam/Must-Know-About-Frontend/blob/master/Notes/frontend/ci-cd.md)
