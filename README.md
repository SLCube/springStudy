# springStudy
인프런 김영한님의 스프링 강의 학습

- 학습기간 : 2022-06-30 ~
- 학습의도 : 스프링을 이용해 개발하고 있지만 기본부터 다시 학습하기 위해 강의학습
- 학습목표 : 단순히 강의내용을 따라하는것이 아닌 학습 후 사이드 프로젝트 진행

---

### 스프링에서 빈을 등록하는 2가지 방법
1. 컴포넌트 스캔과 자동 의존관계 설정
1. 자바 코드로 직접 스프링 빈 등록하기
####  
###
#### 1.컴포넌트 스캔과 자동 의존관계
- @Component annotation이 있으면 스프링 빈으로 자동 등록됨
- @Controller, @Service, @Repository가 스프링 빈으로 자동 등록된 이유도 컴포넌트 스캔 때문
####
- @Component를 포함하는 다음 annotation도 스프링 빈으로 자동 등록됨.
  - @Controller
  - @Service
  - @Repository
####
- 예시
```java
@Service
public class MemberService() {
    private final MemberRepository memberRepository;
    
    @Autowired
    public MemberService(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }
}
```
####
###
#### 2. 자바 코드로 직접 스프링 빈 등록하기
```java
@Configuration
public class SpringConfig {
    
    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }
    
    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }
}
```