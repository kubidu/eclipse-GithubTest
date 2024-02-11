
<!--
**gy0-0o/gy0-0o** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<div align="center">
Hello, I'm PanGyo :wave:
</div>


## 🔨 SKILL
<div style="display:flex; flex-direction:column; align-items:flex-start;">
    <!-- Backend -->
    <p><strong>Backend</strong></p>
    <div>
        <img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=Java&logoColor=white"> 
        <img src="https://img.shields.io/badge/spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white"> 
        <img src="https://img.shields.io/badge/MyBatis-000000?style=for-the-badge&logo=MyBatis&logoColor=white"> 
    </div>
    <!-- Database -->
    <p><strong>Database</strong></p>
    <div>
        <img src="https://img.shields.io/badge/oracle-e76f00?style=for-the-badge&logo=oracle&logoColor=white"> 
    </div>
    <!-- Server -->
    <p><strong>Server</strong></p>
    <div>
        <img src="https://img.shields.io/badge/apachetomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black"> 
    </div>
    <!-- Frontend -->
    <p><strong>Frontend</strong></p>
    <div>
        <img src="https://img.shields.io/badge/Jsp-e76f00?style=for-the-badge&logo=Jsp&logoColor=white"> 
        <img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white"> 
        <img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white"> 
        <img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"> 
        <img src="https://img.shields.io/badge/jquery-0769AD?style=for-the-badge&logo=jquery&logoColor=white"> 
        <img src="https://img.shields.io/badge/Ajax-2c83b9?style=for-the-badge&logo=Ajax&logoColor=white"> 
    </div>
</div>

## 💻 Git stats
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=pangyosim&show_icons=true&theme=cobalt)
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=pangyosim&exclude_repo=songyouyoung.github.io&layout=compact&theme=tokyonight" height = "195px"/>


> 프로젝트 URL : &nbsp; http://site.oyes.o-r.kr/

---
# 1.&nbsp;프로젝트 개요

### 1-1 프로젝트 기획 및 분석
#### &nbsp; 최근 유튜브, 넷플릭스 같은 서비스들의 가격이 향상되고 있다는 것을 체감할 수 있을 것이다. 
가족들과 공유가여 한 계정으로 다 같이 즐길 수 있다는 장점이 있지만 가족 구성원이나 같이 쓸 사람이 없다면 혼자서 감당하기에는 부담스러운 금액이다. 
이러한 불편함을 줄여주기위해 생각을 한 것이 OTT 서비스를 활용하자는 것이었다. 이를 통해 많은 사람들이 조금 더 저렴하고 편한 서비스를 이용할 수 있게
도와주는것이 이 프로젝트의 주제를 정하게 된 목적이자 목표다.


### 1-2 프로젝트 개발환경 및 기술스택
> ** apache-tomcat 9.0.84 | Spring Boot 4 (STS4) | Java 11 | Oracle DataBase 11g **

![](https://velog.velcdn.com/images/spg9468/post/1e69ca75-59c3-41ac-8f1a-7f55be5c4047/image.png)


### 1-3 프로젝트 아키텍쳐
![](https://velog.velcdn.com/images/spg9468/post/21b6e2d2-44ea-4fb6-8443-675911525805/image.png)

---
# 2.&nbsp; 프로젝트 기능소개

### 2-1 기능 요약
~~~
로그인 & 회원가입 & 파티만들기
~~~

![](https://velog.velcdn.com/images/spg9468/post/9e53a648-0fc2-4b4c-b2ca-fdc49e589457/image.png)

~~~
마이페이지 & Q&A페이지
~~~
![](https://velog.velcdn.com/images/spg9468/post/df256260-d9e4-4bc6-9813-5e727b096336/image.png)


~~~
어드민페이지
~~~

![](https://velog.velcdn.com/images/spg9468/post/41ab62fe-edd5-4c9b-8c1a-4350f2c9341b/image.png)

---


# 3.&nbsp; 프로젝트 개발결과
### 3-1 플로우 차트
![](https://velog.velcdn.com/images/spg9468/post/ea382928-c55e-4d7f-ad4a-6d4d3021e2c7/image.png)


### 3-2 Springboot Controller

#### ✅ &nbsp; Mybatis-Config
- ** SqlSessionFactory 생성 시 Reference로 DataSource Bean 수정 및 생성**
```
package com.web.config;

import javax.sql.DataSource;

import org.apache.ibatis.session.SqlSessionFactory;
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.SqlSessionTemplate;
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.boot.jdbc.DataSourceBuilder;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
@MapperScan(value="com.web.dao",sqlSessionFactoryRef = "SqlSessionFactory")
public class MyBatisConfig {
	private static SqlSessionFactory factory = null;

	@Value("${mybatis.mapper-locations}")
	String mPath;
	
	@Bean(name="dataSource")
	@ConfigurationProperties(prefix="spring.datasource")
	public DataSource DataSource() {
		return DataSourceBuilder.create().build();
	}
	
	@Bean(name="SqlSessionFactory")
	public SqlSessionFactory SqlSessionFactory(@Qualifier("dataSource") DataSource DataSource, ApplicationContext applicatiionContext) throws Exception{
		SqlSessionFactoryBean sqlSessionFactoryBean = new SqlSessionFactoryBean();
		sqlSessionFactoryBean.setDataSource(DataSource);
		sqlSessionFactoryBean.setMapperLocations(applicatiionContext.getResources(mPath));
		return sqlSessionFactoryBean.getObject();
	}
	@Bean(name="SessionTemplate")
	public SqlSessionTemplate SqlSessionTemplate(@Qualifier("SqlSessionFactory") SqlSessionFactory firestSqlSessionFactory) {
		return new SqlSessionTemplate(firestSqlSessionFactory);
	}
	
}
```

#### ✅ &nbsp; Interceptor-Config
- ** 로그인 안되어있을 때 Interceptor로 접근 금지 URL 관리 **
```
package com.web.config;

import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

import com.web.session.SessionCheckInterceptor;

@Configuration
public class WebConfig implements WebMvcConfigurer {

	@Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new SessionCheckInterceptor())
                .order(2)
                .addPathPatterns("/memberJoinForm", "/loginForm", "/createparty",
                                 "/memberUpdate", "/memberUpdateForm", "/memberUpdateNo",
                                 "/memberUpdateResult", "/reviewInsert", "/admin",
                                 "/getmypage", "/groupInsert", "/groupJoinForm",
                                 "/groupRegistrationForm", "/imageban", "/mygrouplist",
                                 "/MyKingList", "/PartyList", "/partyUpdate",
                                 "/youtubePartyList", "/findparty", "/partydetail",
                                 "/payinfo", "/reviewContent", "/reviewForm" ) // 접근 금지 url
                .excludePathPatterns("/resources/**", "/**/*.ico", "/error", "/login", "/loginResult",
                					 "/userSearch" ); // 예외 url 
    }
}

```
- ** HandlerInterceptor 부분 **
```
package com.web.session;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import org.springframework.web.servlet.HandlerInterceptor;

import lombok.extern.slf4j.Slf4j;

public class SessionCheckInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse
            response, Object handler) throws Exception {
		
        //Session Check - Session X
        if(request.getSession().getAttribute(MemberSession.LOGIN) == null){
        	
            // 세션이 없을 시, login으로 Redirect
            response.sendRedirect("/login");
            return false;
        }
		
        // Session O
        return true;

    };
}

```

### 3-3 &nbsp; JSoup 데이터 크롤링

#### ✅ &nbsp; TopService

```
package com.web.service;

import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

import javax.annotation.PostConstruct;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;
import org.springframework.stereotype.Service;

import com.web.vo.Top;

@Service
public class TopService {
	private static String Top_Netflix_URL = "https://www.netflix.com/tudum/top10/south-korea";
	private static String Top_WhaCha_URL ="https://pedia.watcha.com/";
    @PostConstruct
    public List<Top> getTopDatas() throws IOException {
        List<Top> TopList = new ArrayList<>();
        Document document = Jsoup.connect(Top_Netflix_URL).get();

        Elements contents = document.select("section ul div");
        for(Element content : contents) {
        	Top top = Top.builder()
        			.image(content.select("picture source").attr("abs:srcset"))
        			.subject(content.select("b").text())
        			.url(content.select("a").attr("abs:href"))
        			.build();
        	if(top.getImage() != "" && top.getSubject() != "" && top.getUrl() != "") {
            	top.setSubject(top.getSubject().substring(0,top.getSubject().length()-3));
        		TopList.add(top);
        	}
        }
        return TopList;
    }
    
    @PostConstruct
    public List<Top> getTopWhacha() throws IOException {
        List<Top> TopList = new ArrayList<>();
        Document document = Jsoup.connect(Top_WhaCha_URL).get();
        Elements contents = document.select("section div ul li");
        for(Element content : contents) {
        	Top top = Top.builder()
        			.image(content.select("img").attr("abs:src"))
        			.subject(content.select("a").text())
        			.url(content.select("a").attr("abs:href"))
        			.build();
        	if(top.getImage() != "" && top.getSubject() != "" && top.getUrl() != "") {
        		TopList.add(top);
        	}
        }
        return TopList.subList(0, 10);
    }
}

```
---
# 4. &nbsp; 결론
#### &nbsp; OTT서비스에 대한 수요가 날로 늘어나고 있으며, 이에 따른 공유 서비스들도 증가하고 있다. 그러나 수요 증가 추세에도 불구하고 아직까지 사람들이 많이 이용하고 있는 공유 서비스는 없는 편이다. 따라서 본 프로젝트는 OTT서비스 파티 관리 부분을 개선하여 사용자에게 보다 나은 서비스를 제공하고자 하였다.


