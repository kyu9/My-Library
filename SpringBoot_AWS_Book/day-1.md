# Day 1

## TDDλ?

π νμ€νΈκ° μ£Όλνλ κ°λ°

ν­μ μ€ν¨νλ νμ€νΈλ₯Ό λ¨Όμ  μμ±νκ³ (Red),

νμ€νΈκ° ν΅κ³Όνλ νλ‘λμ μ½λλ₯Ό μμ±νκ³ (Green),

νμ€νΈκ° ν΅κ³Όνλ©΄ νλ‘λμ μ½λλ₯Ό λ¦¬ν©ν λ§(Refactor)

νμ€νΈ μ½λμ μμ±μ λμμ£Όλ νλ μμν¬ : xUnit

πWhy? νμ€νΈ μ½λ

μν€νΌλμ

* λ¨μ νμ€νΈλ κ°λ°λ¨κ³ μ΄κΈ°μ λ¬Έμ λ₯Ό λ°κ²¬νκ² λμμ€λλ€
* λ¨μ νμ€νΈλ κ°λ°μκ° λμ€μ μ½λλ₯Ό λ¦¬ν©ν λ§νκ±°λ λΌμ΄λΈλ¬λ¦¬ μκ·Έλ μ΄λ λ±μμ κΈ°μ‘΄ κΈ°λ₯μ΄ μ¬λ°λ₯΄κ² μλνλμ§ νμΈν  μ μμ΅λλ€
* λ¨μ νμ€νΈλ κΈ°λ₯μ λν λΆνμ€μ±μ κ°μμν¬ μ μμ΅λλ€
* λ¨μ νμ€νΈλ μμ€νμ λν μ€μ  λ¬Έμλ₯Ό μ κ³΅ν©λλ€. μ¦ λ¨μ νμ€νΈ μμ²΄κ° λ¬Έμλ‘ μ¬μ©λ  μ μμ΅λλ€

κ²½νλ΄

* λΉ λ₯Έ νΌλλ°±
* System.out.println()μ ν΅ν΄μ λμΌλ‘ κ²μ¦ν΄μΌνλ λ¬Έμ  β νμ€νΈμ½λκ° μλ κ²μ¦ν΄μ€
* κ°λ°μκ° λ§λ  κΈ°λ₯μ μμ νκ² λ³΄νΈ

πμ€μ λ‘ νμ€νΈ μ½λ μμ±ν΄λ³΄κΈ°

ν¨ν€μ§ μμ±μ, ν¨ν€μ§ λͺμ μΉ μ¬μ΄νΈ μ£Όμμ μ­μμΌλ‘ μ§μ

[admin.jojoldu.com](http://admin.jojoldu.com)μ μ¬μ΄νΈμ ν¨ν€μ§ λͺ β com.jojoldu.adminμΌλ‘ μ€μ 

πμμ±ν νμ€νΈ μ½λ

```java
package com.kyu.book.springboot;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

Applicationμ΄ μμΌλ‘μ λ©μΈ ν΄λμ€

@SpringBootApplication : μ€νλ§ λΆνΈμ μλμ€μ , μ€νλ§ bean μ½κΈ°/μμ±μ λͺ¨λ μλμΌλ‘ μ€μ 

* @SpringBootApplication annotationμ΄ μλ μμΉλΆν° μ€μ μ μ½μ β μ΄ ν΄λμ€λ ν­μ νλ‘μ νΈμ μ΅μλ¨μ μμΉν΄μΌν¨

psvmμ μλ SpringApplication.run()μΌλ‘ λ΄μ₯ WAS(Web Application Server)κ° μ€νλ¨(λ³λμ ν°μΊ£ μ€μΉκ° λΆνμ)

```java
package com.kyu.book.springboot.web;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {
    @GetMapping("/hello")
    public String hello(){
        return "hello";
    }
}
```

@RestController

* μ»¨νΈλ‘€λ¬λ₯Ό JSONμ λ°ννλ μ»¨νΈλ‘€λ¬λ‘ λ§λ€μ΄μ€λ€

@GetMapping

* HTTP MethodμΈ Getμ μμ²­μ λ°μ μ μλ APIλ₯Ό λ§λ€μ΄ μ€λλ€
* κ³Όκ±°μλ @RequestMappingμΌλ‘ μ¬μ©λμμμ
