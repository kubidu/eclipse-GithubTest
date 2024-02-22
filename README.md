
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
Hello, I'm ChanYoung :wave:
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
![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=zkflsk&show_icons=true&theme=cobalt)
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=pangyosim&exclude_repo=songyouyoung.github.io&layout=compact&theme=tokyonight" height = "195px"/>


> 프로젝트 URL : &nbsp; http://site.oyes.o-r.kr/

---
# 1.&nbsp;프로젝트 개요

### 1-1 프로젝트 기획 및 분석
#### &nbsp; 최근 유튜브, 넷플릭스 같은 서비스들의 가격이 향상되고 있다는 것을 체감할 수 있을 것이다. 
가족들과 공유하여 한 계정으로 다 같이 즐길 수 있다는 장점이 있지만 가족 구성원이나 같이 쓸 사람이 없다면 혼자서 감당하기에는 부담스러운 금액이다. 
이러한 불편함을 줄여주기위해 생각을 한 것이 OTT 서비스를 활용하자는 것이었다. 이를 통해 많은 사람들이 조금 더 저렴하고 편하게게 서비스를 이용할 수 있게
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


### 3-2 프로젝트에서 활용한 것들들

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

#### ✅ &nbsp; pay
- ** 선택한 결제방식으로 결제창이 뜰 수 있도록 value값을 pg 이름으로 설정 **
```
<table id="mw">
	   		<tr>
	   			<td style="width: 300px;font-weight: bold; font-size: 20px;">결제 방법</td>
	   		</tr>
	   		<tr>
	   			<td style="">
	   				<img src="resources/assets/img/tosspay.png" width="140" height="50"/> &nbsp; <input type="radio" name="pg" value="tosspayments" checked/> <label>toss</label><br/>
	   				<img src="resources/assets/img/kakaopay.png" width="140" height="50"/> &nbsp; <input type="radio" name="pg" value="kakaopay"/> <label>kakao</label><br/>
	   				<img src="resources/assets/img/payco.png" width="140" height="50"/> &nbsp; <input type="radio" name="pg" value="payco"/> <label>payco</label><br/>
 	   				<p id="number">합계 :&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;<fmt:formatNumber type="number" maxFractionDigits="0" value="${(vo.price / vo.peoplecnt_max)*1.1 }" />&nbsp;원</p>
	   			</td>
	   			<td>
	   			</td>
	   		</tr>
 	   			<tr>
	   		</tr>
	   	</table>
	  
	   	</div>
	
	   	<br/>
	   	<br/>
	   	<div class="input_area">
		   	<input type="button" id="pay" value="결 제" onclick="requestPay(${(vo.price / vo.peoplecnt_max)*1.1 },'${vo.service }','${mv.name }','${mv.email }','${mv.tel }','${mv.addr }',${vo.seq},'${mv.email}')"/> &nbsp; &nbsp; &nbsp;
		   	<input type="button" id="list" onclick="location.href='/'" style="cursor: pointer;" value="목 록" />
	   	</div>

```
- ** javascript 부분 **
```
function requestPay(price,service,name,email,tel,addr,seq,email) {
	  var page = document.querySelector('input[name="pg"]:checked').value;
      var IMP = window.IMP;
      IMP.init("내 가맹점코드");
      IMP.request_pay(
        {
      	  	pg: page, // 반드시 "tosspayments"임을 명시해주세요.
      	    merchant_uid: "",
      	    name: service,
      	    pay_method: "card",
      	    escrow: false,
      	    amount: Math.round(price),
      	    tax_free: 2,
      	    buyer_name: name,
      	    buyer_email: email,
      	    buyer_tel: tel,
      	    buyer_addr: addr,
      	    buyer_postcode: "04783",
      	    notice_url: "https://helloworld.com/api/v1/payments/notice",
      	    confirm_url: "https://helloworld.com/api/v1/payments/confirm",
      	    currency: "KRW",
      	    locale: "ko",
      	    custom_data: { userId: 30930 },
      	    display: { card_quota: [0, 6] },
      	    appCard: false,
      	    useCardPoint: true,
      	    bypass: {
      	      tosspayments: {
      	        useInternationalCardOnly: true, // 영어 결제창 활성화
      	      },
      	    },
        },
        function (rsp) {
          if(rsp.success){
			  jQuery.ajax({
			    url: "http://site.oyes.o-r.kr/paywork?seq="+ seq + "&price="+Math.round(price)+"&email="+ email, 
			    method: "POST",
			    headers: { "Content-Type": "application/json; charset=utf-8" },
			    data: JSON.stringify ({ 
					imp_uid: rsp.imp_uid, // 결제 고유 번호
					merchant_uid : rsp.merchant_uid, // 주문번호 
					status : rsp.status // 결제방법
			    })
			  });
			  location.href='/';
          } else {
          	console.log(rsp);
          	alert('결제 실패,,,');
          }
        });
  	}

```

### 3-3 &nbsp; Mali 의존성 추가 후 사용

#### ✅ &nbsp; MailService

```
import java.io.UnsupportedEncodingException;

import javax.mail.MessagingException;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;

import org.springframework.mail.javamail.JavaMailSender;
import org.springframework.stereotype.Service;

import lombok.RequiredArgsConstructor;

@Service
@RequiredArgsConstructor
public class MailService {
   
   private final JavaMailSender javamailSender;
   private static final String senderEmail = "oy1666919@gmail.com";
   private static int number;
   
   public static void createNumber() {
      number = (int)(Math.random() * (90000)) + 100000;
   }
   
   public MimeMessage CreateMail(String mail) throws UnsupportedEncodingException {
      createNumber();
        MimeMessage message = javamailSender.createMimeMessage();
      
      try {
         message.setFrom(new InternetAddress(senderEmail, "OYES"));
         message.setRecipients(MimeMessage.RecipientType.TO, mail);
         message.setSubject("이메일 인증");
         String body = "";
         body += "<h3>" + "요청하신 인증 번호입니다" + "</h3>";
         body += "<h1>" + number + "</h1>";
         message.setText(body,"UTF-8", "html");
      } catch (MessagingException e) {
         e.printStackTrace();
      }
      
      return message;
      
   }
   
   public int sendMail(String mail) throws UnsupportedEncodingException {
      
      MimeMessage message = CreateMail(mail);
      
      javamailSender.send(message);
      
      return number;
   }
   
}

```
---
# 4. &nbsp; 결론
#### &nbsp; 첫 프로젝트인만큼 방황도 많이 하고 어려운 부분들이 많았다. 이런 점들을 팀원들과의 소통을 통해서 해소하며
#### &nbsp;프로젝트는 혼자가 아니 다 같이 도우며 알려주고 의견 공유를 많이 해야 더 좋고 질높은 프로그램이 나올 수 있다는 것을 알게 되었다.
#### &nbsp; 넷플릭스, 유튜브와 같은 대형 플렛폼을 이용하는만큼 사람들은 OTT 서비스라는 개념에는 아직 생소하다고 생각한다.
#### &nbsp; 이번 프로젝트에서 만든것을 바탕으로 사람들이 그 편리성을 이해하고 많이 사용하면 좋겠다는 생각을 했다.


