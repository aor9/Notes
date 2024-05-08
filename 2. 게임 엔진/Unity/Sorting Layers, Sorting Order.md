
##### 같은 Layer, 같은 Sorting Order를 갖게 된다면
- 때에 따라서 달라지게 된다.
#### 우선순위?
Layer로 Rendering 순서가 나뉘고 난 후 Layer 안에서는 sorting order로 나뉜다.
### Sorting Layers
![[Pasted image 20231129172943.png]]
- 맨 위에있는 것 부터 순서대로 Rendering이 된다. -> 점점 위에 쌓인다고 이해하면 될 듯.
### Sorting Order
- 같은 Layer 내에서의 sorting 순서를 정하는 기능
## UI 에서의 Sorting 
- unity hierarchy 에서의 위치에 따라 sorting이 된다. 
- hierarchy 기준 위에 있는 놈들부터 rendering
#### World Space UI
- world space ui 는 sorting layer, sorting order 사용 가능


 > Sorting Layers 와 Layer는 아예 다른것.
