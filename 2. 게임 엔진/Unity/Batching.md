### DrawCall
- CPU 가 읽은 데이터를 GPU 한테 그려라 라고 하는 것
##### SetPass Call
- 그래픽 계열 쪽 material, shader과 같은 것의 커맨드들을 묶어서 SetPass 라 하고, 그것을 전달하는 것을 SetPass Call 이라 한다.

> draw call 뿐만 아니라, 그래픽을 구성하는 상태의 데이터들도 함께 포장을 해서 GPU한테 넘기는 것을 Batch라고 한다.
> Batch 수가 많을 수록 부하가 심하게 걸리고, 이 배치 수를 줄이는 것을 최적화라고 한다.

### Batch가 적용되는 컴포넌트
![[Pasted image 20231225150624.png]]
#### material 관련 최적화
- 여러 재질을 하나의 Atlas 로 묶어서 사용했을 때
- 예를 들어 8개의 material을 묶어서 사용하지 않을때는 DrawCall, SetPass Call 모두 8개지만 Atlas 로 묶어서 사용하면 SetPass Call이 3개로 줄어드는 것을 확인할 수 있다.
	- 3개로 줄어들면 뭔가 에러가 날 수 있다는 뜻?
	- 겹처서 들어가는놈들이 있다는 얘기인듯.
- Atlas : 여러개의 텍스처를 단일 텍스처로 결합한 것.
### Dynamic Batching
![[Pasted image 20231225151131.png]]
![[Pasted image 20231225151157.png]]
-> 유니티에서 dynamic batching 켜는 법.
-> 배치수가 줄어든다.
-> 2D에서 여러개의 텍스쳐를 하나의 Atlas로 만들어서 사용할 때  유용
### Static Batching
![[Pasted image 20231225151528.png]]
-> 오브젝트를 정적배칭을 하게 할 수 있음.
-> 정적배칭을 하면 트랜스포밍(회전 등)이 불가능.
-> 내부상에서 하나의 mesh로 통합이돼서 올라가서 메모리도 많이 필요로함.
### SRP batching
![[Pasted image 20231225152151.png]]
-> 여러 Material이 공통된 Shader를 사용할때 적용 가능
-> DrawCall 은 여러개, SetPass Call 이 줄어든다.
![[Pasted image 20231225152329.png]]
### GPU 인스턴싱
- 하나의 mesh를 가지고 엄청나게 batch수를 줄일 수 있는 기법
![[Pasted image 20231225152455.png]]
-> 셰이더가 SRP Batcher 와 호환하지 않으면 끌 필요가 없다.
-> SRP Batcher와 같이 사용 불가능
-> CPU가 하나의 mesh만 읽어 GPU한테 넘기고, GPU는 자기 자신의 메모리에 저장을 해서, 위치정보만 갖고 동일한 mesh를 계속 그리는 것.
