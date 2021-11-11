# 본문의 글은 인프런 앨런 Swift문법 마스터 스쿨(온라인) 부트캠프의 강의 영상을 본후 직접 요약정리하여 공부하기 위해 작성하는 글입니다.
https://inf.run/YyoR

# 버튼을 누르면 화면의 글자가 바뀌는 앱만들기

```swift
import UIKit

class ViewController: UIViewController {
    
    
    
    @IBOutlet weak var mainLabel: UILabel! //레이블인 이 변수오 연결되어있다. 이변수의 타입은 UILabel 이다.
    //애플이 미리 개발자들 쓰기 편하게 만들어둔것. 우리는 버튼과연결해서 이 레이블을 건드릴 것임.
    //IBoutlet이 레이블에 영향을줌
    //interface builder 와 연결된 outlet(배출구) = 속성
    
    
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        //viewDidLoad 라는 함수는 앱의 화면에 들어오면 처음 실행시키는 함수이다.
        //여기다 mainLabel.text = "hello" 라고하면 앱을 키자마자 레이블의 텍스트가 바뀐다.
        //mainLabel.backgroundColor = UIColor.yellow 라고 하면 앱을 켜자마자 레이블의 바탕색이 바뀐다.
    }
    
    
    
    @IBAction func mainButten(_ sender: UIButton) { //그래서 버튼의 대한 함수를 만들고
        mainLabel.text = "안녕하세요"
        // mainLabel 이라는 변수의 하위요소중 text인 부분을 바꿔주기위해 이런코드를 작성한것.
        // 그래서 버튼을 누르면 함수가 작동하고 mainLable의 text가 "안녕하세요"라고 바뀐다.
        // 버튼이 IBAction에 영향을줌
        //interface builder 와 연결된 action(동작) = 메서드




        //mainLabel.backgroundColor = #colorLiteral(red: 0.9254902005, green: 0.2352941185, blue: 0.1019607857, alpha: 1)
        //이 코드는 mainLable의 바탕색을 바꾸는 코드이다. 한번 경험하는게 빠를듯




        //mainLabel.textColor = #colorLiteral(red: 1.0, green: 1.0, blue: 1.0, alpha: 1.0)
        //이건 글자색을 바꾸는 코드이다. 이것도 한번 경험해보자
    }
    
    
    
    
    
    
    
}
```