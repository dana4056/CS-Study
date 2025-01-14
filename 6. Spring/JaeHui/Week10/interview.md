## 📝 Interview

#### 🗨 WS와 WAS의 차이점에 대해 설명하세요.

```
서버란 네트워크를 통해 클라이언트에게 정보나 서비스를 제공하는 컴퓨터 시스템을 의미합니다.

웹 서버는 인터넷을 기반으로 클라이언트에게 웹 서비스를 제공하는 컴퓨터를 의미합니다.
클라이언트 입장에서는 웹 서버에게 URL 주소를 통해 HTTP 통신 규약에 맞게 요청하면 HTML 내용을 응답받게 됩니다.
서버 입장에서는 HTTP 웹 요청이 들어왔을 때 알맞은 데이터를 만들어 응답하는데, 그 데이터는 웹에서 처리할 수 있는 HTML, CSS, js, jpg 등 정적인 데이터로 한정됩니다.
대표적으로 Apache, Nginx 등이 있습니다.

웹 서버에서는 정적인 데이터만 다룰 수 있으므로, 이를 보완하기 비즈니스 로직 처리, DB 연동 등의 문제를 해결하기 위해 WAS가 등장하게 되었습니다.
WAS는 웹 어플리케이션을 실행시켜 기능을 수행하고 그 결과를 웹 서버에 전달하는 일종의 미들웨어로, 동적인 데이터를 제공할 수 있습니다.
웹 서버와 웹 컨테이너의 역할을 합친 형태로, 프로그램 실행 환경 설정, 데이터베이스 접속, 비즈니스 로직 수행 등을 맡습니다.
대표적으로 Tomcat, JEUS, IBM WebSphere가 있습니다.
```

<br>

#### 🗨 Cookie와 Session의 차이점에 대해 설명하세요.

```
쿠키란 클라이언트에 저장된 목적으로 생성한 key-value 형식의 문자열 덩어리를 의미합니다.
HTTP는 Stateless 무상태, Connectionless 비연결성의 특성을 가지기 때문에, 상태 정보를 유지하기 위해 사용합니다.
클라이언트가 서버에 요청을 보내면, 서버는 응답 헤더의 Set-Cookie에 정보를 담고, 이후 클라이언트는 매번 저장된 쿠키를 요청 헤더에 담아 보냅니다.
서버는 쿠키에 담긴 정보를 바탕으로 클라이언트가 누군지 식별하거나 정보를 바탕으로 추천 광고를 띄울 수 있습니다.
각 사용자의 고유 정보 유출 및 조작 위험이 있어 보안에 취약합니다.
또한 용량 제한이 있고, 웹 브라우저 간 공유가 불가능합니다.

세션은 쿠키와 같이 상태 정보를 유지하기 위한 목적으로 사용되지만,
다른 점은 서버에서 클라이언트의 세션 ID를 부여하여 브라우저가 종료되기 전까지 상태 정보를 유지하게 됩니다.
즉 브라우저가 아닌 서버 측에 인증 정보를 저장하고 관리합니다.
유저가 웹사이트에 접속하면 세션이 서버 메모리에 저장되고, 부여된 Session ID를 브라우저 쿠키에 저장합니다.
브라우저는 해당 사이트에 대한 모든 Request에 Session ID를 쿠키에 담아 전송하고, 서버는 그 값을 서버 메모리의 값과 비교하여 인증을 수행합니다.
```

<br>

#### 🗨 JWT란 무엇이며, 어떻게 활용되는지 설명하세요.

```
JWT란 인증에 필요한 정보들을 암호화시킨 JSON 토큰을 의미합니다.
JSON 데이터를 Base64 URL-safe Encode 방식으로 인코딩하여 직렬화한 것입니다.
위변조 방지를 위한 개인키 전자서명도 포함되어 있어, 서버에서는 서명을 검증하는 과정을 거치게 됩니다.
JWT는 Header, Payload, Signature로 이루어져 있습니다.
헤더에는 JWT에서 사용할 타입과 해시 알고리즘의 종류가 담겨 있습니다.
페이로드에는 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨 있습니다.
시그니처 부분에는 개인키 Private key로 서명한 전자서명이 담겨 있습니다.

토큰 기반 인증 시스템은 클라이언트가 서버에 접속했을 때 인증되었다는 의미로 토큰을 부여받는 방식으로 진행됩니다.
이 토큰은 유일한 값으로, 서버에서 클라이언트를 식별할 수 있는 값입니다.
이 방식은 로그인 시 보편적으로 사용되는 방식입니다.
사용자가 로그인을 하면 서버 측에서 토큰을 발생하고, 클라이언트에서는 이 토큰을 쿠키나 스토리지에 저장한 후 HTTP 요청 헤더에 포함시켜 매번 요청을 수행합니다.
서버는 토큰을 검증하고 요청에 응답하게 됩니다.
토큰 자체에 요청한 사람의 정보가 담겨 있기 때문에 DB를 조회하지 않고도 유저를 식별할 수 있습니다.
```

<br>

#### 🗨 CORS란 무엇인가요?

```
CORS란 출처가 다른 자원들을 공유한다는 의미로, 한 출처에서 있는 다른 자원에서 다른 출처에 있는 다른 자원에 접근하도록 하는 개념입니다.
웹 애플리케이션은 리소스가 자신의 출처, 즉 도메인, 프로토콜, 포트 등과 다를 때 CORS HTTP 요청을 실행합니다.

위 URL에서 Protocol, Host, Port가 같으면 동일 출처(Origin)이라고 합니다.
동일 출처 정책이란 다른 출처로부터 조회된 자원들의 읽기 접근을 막아 다른 출처 공격을 예방합니다.
하지만 이는 다른 출처 자원을 가져오는 것을 제한적으로 허용했기 때문에, 다른 출처 리소스에 접근성을 높이기 위해 CORS가 등장했습니다.
```

<br>

#### 🗨 JDBC와 영속성에 대해 설명하세요.

```
영속성이란 데이터를 생성한 프로그램이 종료되더라도 사리지지 않는 데이터의 특성으로,
영속성을 갖지 않는 데이터는 단지 메모리에서만 존재하기 때문에 프로그램이 종료되면 모두 잃어버리게 됩니다.
따라서 파일 시스템, 관계형 데이터베이스 혹은 객체 데이터베이스 등을 활용하여 데이터를 영구적으로 저장하여 영속성을 부여해야 합니다.

JDBC는 DB에 접근할 수 있도록 Java에서 제공하는 API입니다.
모든 Java Data Access 기술의 근간으로, 모든 Persistence Framework는 내부적으로 JDBC API를 사용합니다.
Persistence Framework는 데이터를 데이터베이스에 저장하는 과정을 도와주고 자동화하는 매개 소프트웨어로,
데이터를 가공하는 자바 객체 층과 데이터를 저장하는 데이터베이스 층 사이를 매끄럽게 연결하는 역할을 합니다.
크게 SQL Mapper와 ORM으로 나뉩니다.
```

<br>

#### 🗨 SQL Mapper와 ORM의 차이에 대해 설명하세요.

```
SQL Mapper란 Object와 SQL의 필드를 매핑하여 데이터를 객체화하는 기술입니다.
객체와 테이블 간의 관계를 매핑하는 것이 아니라, SQL문을 직접 작성하고 쿼리 수행 결과를 어떠한 객체에 매핑할지 바인딩하는 방법입니다.
대표적으로 JdbcTemplate, Mybatis가 있으며, DBMS에 종속적인 문제가 있다는 단점이 있습니다.

MyBatis는 자바에서 SQL Mapper를 지원해주는 프레임워크로, SQL문을 직접 작성하여 쿼리 수행 결과를 객체화할 수 있습니다.
쿼리문을 xml로 분리할 수 있으며 복잡한 쿼리를 작성할 수 있다는 장점이 있습니다.
그러나 객체와 쿼리문을 모두 관리해야 하며, DB CRUD 메소드를 직접 다 구현해야 하는 번거로움이 있습니다.

ORM이란 Object와 DB 테이블을 매핑하여 데이터를 객체화하는 기술입니다.
개발자가 반복적인 SQL을 직접 작성하지 않아도 되어 편리하며 DBMS에 종속적이지 않습니다.
대표적으로 JPA가 있으며, 복잡한 쿼리의 경우 JPQL을 사용하거나 SQL Mapper를 혼용하여 사용 가능합니다.

JPA란 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스입니다.
자바 ORM의 기술 표준으로, CRUD 메소드를 기본으로 제공합니다.
쿼리를 직접 만들지 않아도 되며 객체 중심으로 개발이 가능합니다.
쿼리가 수정되어 데이터 정보가 바뀌면 객체만 수정하면 되어 편리하지만, 복잡한 쿼리 작성이 어렵다는 단점이 있습니다.
```

<br>

#### 🗨 JPQL와 QueryDSL에 대해 설명하세요.

```
JPA는 SQL을 추상화한 JPQL이라는 객체 지향 쿼리 언어를 제공합니다.
따라서 테이블을 대상으로 쿼리 하는 것이 아닌 엔티티 객체를 대상으로 쿼리하게 됩니다.
JPQL은 SQL을 추상화했기 때문에 특정 데이터베이스 SQL에 의존하지 않는 장점이 있습니다.
따라서 JPQL과 SQL의 가장 뚜렷한 차이점은 JPQL은 엔티티 객체를 대상으로 쿼리문을 작성하며, SQL은 데이터베이스 테이블을 대상으로 쿼리문을 작성하는 것입니다.
JPQL은 기본 문자열로 작성되기 때문에 컴파일 시 에러를 발생하지 않는다는 단점이 있습니다.
또한 동적으로 쿼리 언어를 작성하는 데 효율적이지 못합니다.

QueryDSL이란 정적 타입을 이용해서 SQL, JPQL을 코드로 작성할 수 있도록 도와주는 오픈소스 빌더 API입니다.
하이버네이트 쿼리 언어(HQL: Hibernate Query Language)의 쿼리를 타입에 안전하게 생성 및 관리해주는 프레임워크입니다.
JPQL의 단점을 보완하기 위해 등장하여 컴파일 시 오류를 발견하는 것이 가능하며, 복잡하고 동적인 쿼리 작성이 가능합니다.
```

<br>

#### 🗨 Transaction이란 무엇인지 설명하세요.

```
트랜잭션이란 여러 작업을 진행하다가 문제가 생겼을 경우 이전 상태로 롤백하기 위해 사용되는 것을 말합니다.
더 이상 쪼갤 수 없는 최소 작업 단위이며, commit으로 성공하거나 또는 rollback으로 실패 이후 취소 되어야 합니다.

💡 Transaction ACID

- 원자성 Atomicity: 트랜잭션 내의 작업들은 모두 성공 또는 모두 실패한다.
- 일관성 Consistency: 모든 트랜잭션은 일관성 있는 DB 상태를 유지한다. (ex: DB의 무결성 제약 조건 항상 만족)
- 격리성 Isolation: 동시에 실행되는 트랜잭션들은 서로 영향을 미치지 않는다. (ex: 동시에 같은 데이터 수정 X)
- 지속성 Durability: 트랜잭션이 성공적으로 끝나면 그 결과는 항상 기록되어야 한다.

Spring에서는 마치 트랜잭션 코드와 같은 부가 기능 코드가 존재하지 않는 것 처럼 보이기 위해
해당 로직을 클래스 밖으로 빼내서 별도의 모듈로 만드는 AOP(Aspect Oriented Programming, 관점 지향 프로그래밍)를 고안 및 적용할 수 있습니다.
이를 적용한 트랜잭션 어노테이션(@Transactional)을 지원하게 되었다. 이를 적용하면 위와 같은 코드를 핵심 비지니스 로직만 다음과 같이 남길 수 있습니다
```

<br>

#### 🗨 Local Cache와 Global Cache를 비교 설명하세요.

```
캐싱(Caching)은 애플리케이션의 처리 속도를 높여줍니다. <br>
이미 가져온 데이터나 계산된 결과값의 복사본을 저장함으로써 처리 속도를 향상시키며, 이를 통해 향후 요청을 더 빠르게 처리할 수 있습니다. <br>
대부분의 프로그램이 동일한 데이터나 명령어에 반복해서 엑세스하기 때문에 캐싱은 효율적인 아키텍처 패턴입니다.

Local Cache는 서버마다 캐시를 따로 저장하는 방식으로, Memory, Disk와 같은 로컬 서버 장비의 Resource를 이용합니다.
서버 내에서 작동하기 때문에 속도가 빠른 장점이 있지만, 다른 서버의 캐시를 참조하기 어렵다는 단점도 존재합니다.
캐시에 저장된 데이터가 변경되는 경우에는 해당 서버를 제외한 모든 peer에 변경사항을 전달하고 복사하는 과정을 거칩니다.
이 때문에 WAS 인스턴스가 늘어나고, 만약 캐시 저장 데이터 크기가 커지면 성능이 저하되기도 합니다.
대표적으로 Spring에서 사용 가능한 자바 기반 오픈 소스인 Ehcache가 있습니다.

Global Cache는 여러 서버에서 캐시 서버에 접근하여 참조하는 방법입니다.
별도의 캐시 서버를 이용하기 때문에 서버 간 데이터 공유가 쉽고 데이터를 분산하여 저장할 수 있습니다.
하지만 네트워크 트래픽을 사용해야 해서 Local Cache보다는 속도가 느립니다.
Local Cache와 다르게 캐시에 저장된 데이터가 변경되더라도 추가적인 작업이 별도로 필요하지 않습니다.

Redis란 Key, Value 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터 베이스 관리 시스템 (DBMS)입니다.
데이터베이스, 캐시, 메세지 브로커로 사용되며 인메모리 데이터 구조를 가진 저장소입니다.
```

<br>

#### 🗨 캐시 서버 구현 패턴 2가지에 대해 설명하세요.

```
데이터 조회 시 사용
💡 Look aside cache
1. 클라이언트가 데이터를 요청
2. 웹서버는 데이터가 존재하는지 Cache 서버에 먼저 확인
3. Cache 서버에 데이터가 있으면 DB에 데이터를 조회하지 않고 Cache 서버에 있는 결과값을 클라이언트에게 바로 반환 (Cache Hit)
4. Cache 서버에 데이터가 없으면 DB에 데이터를 조회하여 Cache 서버에 저장하고 결과값을 클라이언트에게 반환 (Cache Miss)

데이터 추가 시 사용
💡 Write Back
1. 웹서버는 모든 데이터를 Cache 서버에 저장
2. Cache 서버에 특정 시간 동안 데이터가 저장됨
3. Cache 서버에 있는 데이터를 DB에 저장
4. DB에 저장된 Cache 서버의 데이터를 삭제
```

<br>

#### 🗨 Maven과 Gradle에 대해 설명하세요.

```
빌드란 소스코드 파일을 컴퓨터에서 실행할 수 있는 독립적인 형태로 변환하는 과정과 결과를 의미합니다.
즉 작성한 소스코드와 파일 및 자원을 JVM이나 Tomcat과 같은 WAS가 인식할 수 있도록 패키징하는 과정 및 결과물을 나타냅니다.
빌드 관리 도구란 이런 빌드 과정에서 필요한 라이브러리들을 자동으로 관리해주는 도구로, 다음과 같은 작업을 수행합니다.

Maven은 Java 전용 프로젝트 관리 도구로, Lifecycle 관리 목적 빌드 도구이며, Apache Ant의 대안으로 만들어졌습니다.
아파치 라이센스로 배포되는 오프 소스 소프트웨어이고, pom.xml에 종속 관계를 명시합니다.

Gradle은 Maven을 대체할 수 있는 프로젝트 구성 관리 및 범용 빌드 툴입니다.
Ant Builder와 Groovy script를 기반으로 구축되어 기존 Ant의 역할과 배포 스크립트의 기능 모두 사용 가능하며, SpringBoot와 Android에서 주로 사용됩니다.
Maven에 비해 빌드 속도가 10~100배 가량 빠르며,Java, C/C++, Python 등을 지원합니다.

💡 Maven vs Gradle
Gradle은 작업 의존성 그래프에 기반, Maven은 고정적이고 선형적인 단계의 모델에 기반한다는 빌드 접근 방식의 차이점이 있습니다.
Gradle은 캐시를 사용하기 때문에 Maven보다 속도가 훨씬 빠릅니다.
Maven은 멀티 프로젝트에서 특정 설정을 다른 모듈에서 사용하려면 상속 받아야하지만, Gradle은 설정 주입 방식을 사용하므로 멀티 프로젝트에 적합합니다.
```

<br>

#### 🗨 Filter, Interceptor, AOP를 비교 설명하세요.

```
애플리케이션을 개발할 때 세션 및 권한 체크, XSS 방어, 분기처리, 로그, 페이지 인코딩 변환 등 공통 업무에 관련된 중복된 코드가 많아질 수 있습니다.
이는 프로젝트가 커질수록 서버에 부하를 줄 수 있고 소스 코드 관리가 어렵습니다.
따라서 공통 부분을 따로 빼서 관리해야 할 필요성이 있습니다.

Filter는 요청과 응답을 거른 뒤 정제하는 역할을 합니다.
DispatcherServlet 이전 혹은 맨 마지막에 실행되기 때문에
요청 내용 변경, 전처리 또는 응답 내용 변경, 인코딩 변환, XSS 방어 등을 수행할 수 있습니다.


Interceptor는 요청에 대한 작업 전/후를 가로채서(끼어들어) 기능을 수행하게 됩니다.
Spring Context 내부에서 Controller의 요청과 응답에 관여하며 모든 Bean에 접근이 가능합니다.
로그인 체크, 권한 체크, 로그 확인 등의 작업을 주로 수행합니다.

AOP란 OOP를 보완하기 위해 나온 개념으로, 관점(종단면)을 기준으로 묶어 개발하는 방식을 의미합니다.
관점이란 어떤 기능을 구현할 때 그 기능을 핵심 기능과 부가 기능으로 구분해 각각을 하나의 관점으로 보는 것을 의미합니다.
부가 기능은 핵심 기능이 어떤 기능인지에 무관하게 로직이 수행되기 전 또는 후에 수행되도록 함으로서,
소스 코드에서 여러번 반복해서 쓰는 코드, 즉 흩어진 관심사(Corcern)을 Aspect로 모듈화하여 핵심 로직에서 분리하고 재사용이 용이하도록 합니다.
모듈화된 객체를 편하게 적용할 수 있게 함으로써 개발자가 비즈니스 로직을 구현하는 데만 집중할 수 있게 도와줍니다
```
