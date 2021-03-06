# 본문의 글은 인프런 앨런 Swift문법 마스터 스쿨(온라인) 부트캠프의 강의 영상을 본후 공부한 내용을 정리하여 기록한것입니다.
https://inf.run/YyoR


```swift
/*
 - 스위프트에서 제공하는 불특정한 타입을 다룰 수 있는 타입을 제공
 
 1) Any 타입
 - 기본 타입(Int, String, Bool, ...) 등 포함, 커스텀 클래스, 구조체, 열거형, 함수타입
   까지도 포함해서 어떤 타입의 인스턴스도 표현할 수 있는 타입 (옵셔널타입도 포함)
 
 2) AnyObject 타입
 - 어떤 클래스 타입의 인스턴스도 표현할 수 있는 타입
 */

 // 1) Any타입 ============================================

var some: Any = "Swift"
(some as! String).count //이렇게 타입캐스팅을 해줘야만 됨
some = 10
some = 3.2



// 단점 ===> 저장된 타입의 메모리 구조를 알 수없기 때문에, 항상 타입캐스팅해서 사용해야함 ⭐️


class Person {
    var name = "정덕호"
    var age = 10
}

class Superman {
    var name = "이름"
    var weight = 100
}


// Any타입의 장점: 모든 타입을 담을 수 있는 배열을 생성 가능            // (String) -> String
let array: [Any] = [5, "안녕", 3.5, Person(), Superman(), {(name: String) in return name}]


//array[1].count
(array[1] as! String).count

var abcdef = array[3] as! Person
abcdef.name

(array[3] as! Person).name

// 2) AnyObject타입 =======================================

//클래스의 오브젝트만 담을수있는 타입... 어떤 타입이던..
let objArray: [AnyObject] = [Person(), Superman(), NSString()]

//objArray[0].name
(objArray[0] as! Person).name







// 타입캐스팅 + 분기처리

for (index, item) in array.enumerated() { //enumerated = 열거를 시키는것
    // (0번쨰,  5)
    // (1번째, "안녕")
    // (2번째, 3.5)
    // ...
    
    switch item {
    case is Int:                                  //is int면 true 면?
        print("Index - \(index): 정수입니다.")
    case is Double:                       // 타입캐스팅이되면 num에다 담겠다.
        print("Index - \(index): 소수 입니다.")
    case is String:                               //is string이면 true면?
        print("Index - \(index): 문자열입니다.")
    case let person as Person:                    //타입캐스팅이되면 person에다 담겠다.
        print("Index - \(index): 사람입니다.")
        print("이름은 \(person.name)입니다.")
        print("나이는 \(person.age)입니다.")
    case is (String) -> String:                   //
        print("Index - \(index): 클로저 타입입니다.")
    default:
        print("Index - \(index): 그 이외의 타입입니다.")
    }
}






//옵셔널값의 Any 변환=======================

/*
- 의도적인 옵셔널값의 사용
- Any는 모든 타입을 포함(옵셔널타입도), 의도적인 옵셔널값을 사용하려면 Any타입으로 변환하면
  컴파일러가 알려주는 경고를 없앨 수 있음
 
- 왜?
- 옵셔널값은 임시적인 값일 뿐이므로, 일반적으로 개발자들은 옵셔널 바인딩을 해서
  일반적으로는  언래핑해서 안의 값을 사용해야함 ===> 그래서 경고를 통해 알려줌
  (Any로 변환하겠다는 것은 그 자체를 사용하겠다는 의미임 ===> 경고 없음)
*/



let optionalNumber: Int? = 3
print(optionalNumber)          // 경고
print(optionalNumber as Any)   // 경고 없음
```