iOS Life Cycle
================================================================




App Life Cycle 앱 생명주기
----------------------------------------------------------------
(앱이 화면상에서 보이지 않는 background 상태, 화면에 올라와 있는 foreground 상태 등을 정의)  

1. 앱 실행
2. UIApplication 객체 생성
3. @UIApplicationMain Annotation이 있는 클래스를 찾아서 AppDelegate객체를 생성
4. Main Event Loop를 실행 (touch, text input 등의 user들의 action을 받는 loop)

UIApplication 객체는 싱글톤 객체! (하나만 존재)  
Event Loop에서 발생하는 여러 이벤트들을 감지 > Delegate에 전달  
AppDelegate 객체는 UIApplication 객체로부터 받은 메시지에 해당하는 실행 함수들을 정의  


**App의 5가지 실행상태**
- Not Running : 앱이 실행되지 않은 상태 or 실행되고 있었지만 terminate된 상태
- Inactive: 앱이 foreground에서 실행중, 그러나 현재 아무런 이벤트가 발생되지 않은 상태
- Active: 앱이 foreground에서 실행중, 이벤트를 받고 있는 상태
- Background: 앱이 background에 있음, 실행되는 코드가 있는 상태
- Suspended: 앱이 background에 있음. 앱이 메모리에는 남아있지만, 실행되는 코드가 없는 상태

**delegate객체 메서드**
앱의 상태에 따라 메서드가 호출됨.
- application:willFinishLaunchingWithOptions: > 앱이 처음 실행되어 코드를 실행하는 부분
- application:didFinishLaunchingWithOptions: > 앱이 사용자에게 보여지기 이전 초기화 부분
- applicationDidBecomeActive: > 앱이 foreground에 들어올 때 실행
- applicationWillResignActive: > 앱이 active에서 inactive로 이동될 때
- applicationDidEnterBackground: > 앱이 background에서 돌아가고 있을 때
- applicationWillEnterForeground: > 앱이 background상태에서 벗어나 foreground상태가 될 때, 그러나 아직 active 상태는 아니다.
- application WillTerminate: > 앱이 종료될 때, suspended상태에서는 호출되지 않음.




ViewController Life Cycle 뷰 컨트롤러 생명주기
----------------------------------------------------------------

하나의 화면에 하나의 ViewController만을 가진다.  
iOS는 한 화면에서 다른 화면으로 전환할 때 기존의 화면 위에 새로운 화면이 쌓이는 식으로 화면을 전환.  
여러 개의 뷰 컨트롤러를 가지고 있는 앱, 각각의 뷰 컨트롤러는 각각 자신의 생명주기를 가지고 있다.  

**ViewController 메서드**
-ViewDidLoad > 해당 뷰 컨트롤러 클래스가 생성될 때 실행 (ViewWillAppear 이전에 실행된다.)
-ViewWillAppear > 뷰 컨트롤러가 화면에 나타나기 직전에 실행, 해당 뷰 컨트롤러가 나타나기 직전에 실행되어야 하는 부분을 이 메서드에 구현
-ViewDidAppear > 뷰 컨트롤러가 화면에 나타난 직후에 실행. 화면에 적용될 애니메이션이나, api로부터 정보를 받아와 화면을 업데이트할 때 이 메서드에 해당 로직을 구현하면 좋다! (WillAppear에 구현하여 너무 빨리 애니메이션을 그리거나 정보를 받아와 뷰 컨트롤러를 업데이트하면 화면에 반영되지 않을 수 있다.)
-ViewWillDisappear > 뷰 컨트롤러가 화면에서 사라지기 직전에 실행
-ViewDidDisappear > 뷰 컨트롤러가 화면에서 사라진 직후에 실헹




로그출력해보기
----------------------------------------------------------------
앱 실행  
2016-09-01 15:16:04.181 LifeCycleStudy[2384:125020] main.m > main()  
2016-09-01 15:16:04.183 LifeCycleStudy[2384:125020] call UIApplicationMain()  
2016-09-01 15:16:04.933 LifeCycleStudy[2384:125020] didFinishLaunchingWithOptions  
2016-09-01 15:16:04.937 LifeCycleStudy[2384:125020] ViewController viewDidLoad  
2016-09-01 15:16:04.940 LifeCycleStudy[2384:125020] applicationDidBecomeActive  
뷰 컨트롤러 나타났고! 버튼 클릭  
2016-09-01 15:16:14.086 LifeCycleStudy[2384:125020] button click!  
홈화면으로 이동  
2016-09-01 15:16:25.187 LifeCycleStudy[2384:125020] applicationWillResignActive  
2016-09-01 15:16:27.208 LifeCycleStudy[2384:125020] applicationDidEnterBackground  