# swift 스토리보드 ui

#### 프로젝트 B-TEGS 

- ios 스토리보드랑 코드 이용하여 메인,회원가입 ui 구성
- button 이용하여 화면 전환 코드 구성
```swift
    @IBAction func signupbutton(_ sender: UIButton) {
        
        let vcName = self.storyboard?.instantiateViewController(withIdentifier: "main-2")//화면 전환할 곳
                vcName?.modalPresentationStyle = .fullScreen //전체화면으로 보이게 설정
                vcName?.modalTransitionStyle = .crossDissolve //전환 애니메이션 설정
                self.present(vcName!, animated: true, completion: nil)
        
    }
 ```   
- 회원가입 ui 구성하면서 입력 해야하는 곳에 맞는 Text input Traits 설정
- data Picker 를 사용하여 학력을 작성할수있도록 구현 
  - Text Field 에다가 적용하여 깔끔하게 선택할수도록 구현
 ```swift
class RegisterVC: UIViewController{
    var a: String = ""
    var b: String = ""
    let Education = [["고등학생  ", "중학교  "],
        ["1 학년","2 학년","3 학년"]]
    
    let picker = UIPickerView()
    
    @IBAction func loginbutton2(_ sender: UIButton) {
        let vcName = self.storyboard?.instantiateViewController(withIdentifier: "main-3")
                vcName?.modalPresentationStyle = .fullScreen //전체화면으로 보이게 설정
                vcName?.modalTransitionStyle = .crossDissolve //전환 애니메이션 설정
                self.present(vcName!, animated: true, completion: nil)
    }
    @IBOutlet weak var tf: UITextField!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        picker.delegate = self
        picker.dataSource = self
        tf.inputView = picker
    }
}


extension RegisterVC: UIPickerViewDelegate, UIPickerViewDataSource{
    

    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        self.view.endEditing(true)
    }
    func numberOfComponents(in pickerView: UIPickerView) -> Int {
        return Education.count
    }
    
    // days 배열의 구성요소의 열의 수를 반환하는 메서드 -> 각 행의 열의 수를 결정
    func pickerView(_ pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
        return Education[component].count
    }
    
    // days 배열의 값들을 반환하는 메서드 -> 각각의 값을 결정
    func pickerView(_ pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {
    
        return Education[component][row]
        
    }
    
    // 주어진 component에서 선택된 열을 매개변수로 갖음
    func pickerView(_ pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
    
    // component에 따라 연, 월, 일의 값을 변경
        switch component {
        case 0:
            a = Education[0][row]
        case 1:
            b = Education[1][row]
        default:
            print("Error!!")
        }
        
        // 바뀐 값을 텍스트필드의 값으로 할당
        tf.text = a+b
    }
}
 ``` 


<img width="495" alt="스크린샷 2021-12-23 오후 7 59 17" src="https://user-images.githubusercontent.com/84947346/147231101-b810610e-d55e-4c7b-b92e-c703dcb638f7.png">


