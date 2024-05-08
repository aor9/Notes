##### FSM?
- 유한한 개수의 상태들로 구성된 하나의 간단한 기계
- 캐릭터의 행동을 각 상태로 모듈화를 시킨다.
- 복잡한 AI를 구현하기에는 어렵지만 간단한 AI는 쉽게 구현 가능하다.

- 캐릭터가 단 하나의 상태만을 가지게 하여 특정 조건이 만족하면 하나의 상태를 갖게하고 그 상태에 따라 다른 동작을 수행하도록 하여 FSM을 구현할 수 있다.
```c#
public class Monster : Creature
{
	private enum MonsterState
	{
		 IDLE,
		 MOVE,
		 ATTACk,
		 DEAD
	}
	private MonsterState _state;

	private void Start()
	{
		_stat = MonsterState.Idle;
	}

	private void Update()
	{
		UpdateState();
	}

	private void UpdateState()
	{
		switch(_state)
		{
			case MonsterState.IDLE:
				// 동작 구현
				break;
			case MonsterState.MOVING:
				// 동작 구현
				break;
			. . .
		}
	}
}
```

##### 단점
- 상태가 늘어나면 관리하기가 어려움 (유지보수 코스트가 늘어남)
- 새로운 동작을 추가하거나 기존 동작을 변경할 때 전체 시스템을 변경해야할수도 있음.
- 복잡한 상호작용을 표현하기 어려움

[[HFSM]] [[Behavior Tree]]