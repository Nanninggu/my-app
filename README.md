`application.properties` 파일에서 로컬 영역의 H2 데이터베이스와 GCP 환경의 Cloud SQL을 사용하는 방법을 설명하겠습니다.

### 로컬 영역의 H2 데이터베이스 사용

로컬 영역에서 H2 데이터베이스를 사용하려면 다음과 같이 `application.properties` 파일을 설정합니다:

```ini
# H2 In-Memory DB Connection
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
spring.h2.console.settings.web-allow-others=true
spring.datasource.initialization-mode=always
```

이 설정은 H2 인메모리 데이터베이스를 사용하며, H2 콘솔을 통해 웹에서 접근할 수 있도록 합니다.

### GCP 환경의 Cloud SQL 사용

GCP 환경에서 Cloud SQL을 사용하려면 다음과 같이 `application.properties` 파일을 설정합니다:

```ini
# GCP Cloud SQL(PostgreSQL) DB Connection
spring.datasource.driver-class-name=org.postgresql.Driver
spring.datasource.url=jdbc:postgresql://10.101.32.3:5432/postgres
spring.datasource.username=postgres
spring.datasource.password=test1234
```

이 설정은 GCP Cloud SQL PostgreSQL 데이터베이스를 사용합니다. `10.101.32.3`, `postgres`, `test1234` 부분을 실제 Cloud SQL 인스턴스의 정보로 대체해야 합니다.

`10.101.32.3`은 Cloud SQL 인스턴스의 내부 IP 주소입니다. 이 주소는 GCP 콘솔에서 확인할 수 있습니다. `10.101.32.3` 부분을 실제 Cloud SQL 인스턴스의 내부 IP 주소로 변경해야 합니다.

이렇게 설정하면 로컬에서는 H2 데이터베이스를, GCP 환경에서는 Cloud SQL을 사용할 수 있습니다. 필요에 따라 프로파일을 사용하여 환경별로 설정을 분리할 수도 있습니다.