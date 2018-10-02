# HTML - HTMLEvent

Event 인터페이스는 DOM의 모든 이벤트를 표현합니다.
일부는 마우스나 키보드 등 사용자가 유도하는 이벤트고, 일부는 애니메이션 종료와 비디오 일시정지 등 API에서 발생합니다.
많은 종류의 이벤트가 존재하고, 몇몇은 Event 인터페이스에 기반한 다른 인터페이스를 사용합니다. Event 자체는 모든 이벤트 공통의 속성과 메서드를 가지고 있습니다.

> 전역에 선언되어있는 TypeScript에 정의된 Event 종류들

```ts
interface Event { }
interface AnimationEvent extends Event { }
interface ClipboardEvent extends Event { }
interface CompositionEvent extends Event { }
interface DragEvent extends Event { }
interface FocusEvent extends Event { }
interface KeyboardEvent extends Event { }
interface MouseEvent extends Event { }
interface TouchEvent extends Event { }
interface PointerEvent extends Event { }
interface TransitionEvent extends Event { }
interface UIEvent extends Event { }
interface WheelEvent extends Event { }
```

## Event Properties
- Event.cancelBubble
	- A historical alias to Event.stopPropagation(). Setting its value to true before returning from an event handler prevents propagation of the event.
- Event.cancelable Read only
	- 이벤트를 취소할 수 있는지 나타내는 불린 값입니다.
- Event.currentTarget Read only
	- A reference to the currently registered target for the event. This is the object to which the event is currently slated to be sent; it's possible this has been changed along the way through retargeting.
- Event.eventPhase Read only
	- Indicates which phase of the event flow is being processed.
- Event.target Read only
	- A reference to the target to which the event was originally dispatched.
- Event.type Read only
	- 이벤트의 이름입니다. 대소문자를 구분하지 않습니다.
- Event.isTrusted Read only
	- 이벤트를 사용자의 클릭 등으로 브라우저가 생성했는지, 아니면 new Event() 등 스크립트에서 생성했는지 나타냅니다.


> 추가적인 Dom Event 속성에 대해서 보고싶으시면 아래 주소를 클릭해주세요.
- [HTML - Dom Event Properties](https://developer.mozilla.org/ko/docs/Web/API/Event#Properties)

## Event Methods



## Examples
<script async src="//jsfiddle.net/SHun10114/bwtp6vh9/embed/js,html,result/"></script>


## References
- [HTML - Dom : Event](https://developer.mozilla.org/ko/docs/Web/API/Event)
- [HTML - Dom : Event Type](https://developer.mozilla.org/en-US/docs/Web/Events)
- [HTML - Dom : addEventListener](https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener)
