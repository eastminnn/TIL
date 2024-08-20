# Controller
MVC에서 C에 해당되고 주로 사용자의 요청을 처리 한 후 지정된 뷰에 모델 객체를 넘겨주는 역할을 해준다.

## Controller 관련 대표적인 Annotation
1. @Controller
- Controller의 역할을 수행한다고 명시, 필요한 비즈니스 로직을 호출하여 전달할 모델과 이동할 뷰 정보를 DispatherSevlet에 반환한다.
- @Component의 구체화된 어노테이션

2. @RequestMapping
- 요청에 대해 어떤 Controller, 어떤 메소드가 처리할지 맵핑하기 위한 어노테이션
- 클래스나 메서드 선언부에 @RequestMapping과 함께 URL을 명시하여 사용
- viewName 생략시 @RequestMapping의 path로 설정한 URL이 default viewName

## RequestMapping 속성들
1. value(String[]) : URL 값
```
@RequestMapping(value="/login")
@RequestMapping("/login") 
```

2. method (RequestMethod[]) : HTTP Request 메소드 값
 - GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE
```
@RequestMapping(method=RequestMethod.GET)
@RequestMapping(method=RequestMethod.POST)
@RequestMapping(method=RequestMethod.PUT)
@RequestMapping(method=RequestMethod.DELETE)
```

3. contentype
```
@RequestMapping(consumes="application/json")
@RequestMapping(produces="application/json")
```

## Sping boot에서 controller 생성 (@Controller)
### Homecontroller 생성 (@Controller)
test용 controller 생성
![alt text](/Image/Spring_boot/springboot1.PNG)
```
package com.example.demo.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class Homecontroller {
    @GetMapping("/")
    public  String index() {
        return  "index";
    }
}

```

### View 생성 (Index 페이지 만들기)
static 폴더는 html 문서, 이미지, 영상 등을 관리
![alt text](/Image/Spring_boot/springboot2.PNG)