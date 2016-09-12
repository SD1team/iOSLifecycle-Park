#@property

@property BOOL exists;

###getter, setter 이름 재정의하는 법
@property (getter = isExists, setter = newSetExists) BOOL exists;


##@property 속성 알아보기

###쓰기 여부
**readwrite** : getter, setter 모두 생성 (default)
**readonly** : getter만 생성

###setter속성
**strong** : 입력되는 변수의 소유권을 가져온다. reference count를 1증가, 내가 소유하고 있는 동안은 release안됨.
**retain** : strong속성과 비슷
**weak**   : 객체의 refenrecne count를 증가시키지 않음. 그래서 객체가 release되어 메모리에서 사라지게 되면, 자동으로 nil로 설정
**assign** : 기본값으로 값을 복사한다. weak과 비슷. weak은 객체를 다루고, assign은 스칼라값(ex.NSInteger)을 다룬다.
**copy**   : 주어진 객체를 복사. strong은 reference count를 사용해 소유권을 가져온다. copy는 아예 같은 값을 가지는 객체를 새로 생성

###Thread Sate
**atomic** : (default) setter가 thread safe하도록 설정. 여러 스레드에서 한 변수에 접근할 때, 하나의 스레드가 변수를 사용하고 있으면 다른 스레드가 접근하지 못하도록 제한한다
**nonatomic** : 멀티스레드X. atomic을 사용해서 setter를 thread safe하게 하면 좋겠지만, 비용 발생. 성능에 문제가 생긴다. 대부분의 경우 nonamtomic를 사용