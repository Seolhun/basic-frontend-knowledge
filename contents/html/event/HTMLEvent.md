# HTML - HTMLEvent

Event 인터페이스는 DOM의 모든 Event를 표현합니다.
일부는 마우스나 키보드 등 사용자가 유도하는 Event고, 일부는 애니메이션 종료와 비디오 일시정지 등 API에서 발생합니다.
많은 종류의 Event가 존재하고, 몇몇은 Event 인터페이스에 기반한 다른 인터페이스를 사용합니다. Event 자체는 모든 Event 공통의 속성과 메서드를 가지고 있습니다.

> 전역에 선언되어있는 Event 종류들(TypeScript)
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

---
## Event Properties
- Event.target (Read only)
	- A reference to the target to which the event was originally dispatched.
- Event.currentTarget (Read only)
	- A reference to the currently registered target for the event. This is the object to which the event is currently slated to be sent; it's possible this has been changed along the way through retargeting.
- Event.type (Read only)
	- Event의 이름입니다. 대소문자를 구분하지 않습니다.
- Event.cancelable (Read only)
	- Event를 취소할 수 있는지 나타내는 불린 값입니다.
- Event.cancelBubble
	- A historical alias to Event.stopPropagation(). Setting its value to true before returning from an event handler prevents propagation of the event.
- Event.eventPhase (Read only)
	- Indicates which phase of the event flow is being processed.

> 추가적인 Dom Event 속성에 대해서 보고싶으시면 아래 주소를 클릭해주세요.
- [HTML - Dom Event Properties](https://developer.mozilla.org/ko/docs/Web/API/Event#Properties)

#### - event.target
Event는 다른 Element에 전파되어도 Event의 근원이 정확히 어디서 발생되었는지를 알 수 있습니다. 이러한 정보를 가지고 있는 것이 바로 `event.target`입니다.

Note the differences from `this` ( = `event.currentTarget`):
- `event.target` -- is the "target" element that initiated the event, it doesn't change through the bubbling process.
- `this` -- is the "current" element, the one that has a currently running handler on it.

For instance, if we have a single handler `form.onclick`, then it can "catch" all clicks inside the form. No matter where the click happened, it bubbles up to `<form>` and runs the handler.

In `form.onclick` handler:

- `this` (`= event.currentTarget`) is the `<form>` element, because the handler runs on it.
- `event.target` is the concrete element inside the form that actually was clicked.

Check it out:

[codetabs height=220 src="bubble-target"]

It's possible that `event.target` equals `this` -- when the click is made directly on the `<form>` element.

#### - event.currentTarget
Event의 currentTarget은 Event의 근원(event.target)과는 다릅니다.
Event는 항상 전파되는 속성을 갖고 있기 때문에, 현재 Event가 전파되어 작동되는 Event가 다르기 때문입니다.
이렇게 전파되고 있는 Event가 어디에 위치하였는지에 대한 정보를 알기 위해 currentTarget이란 속성을 사용할 수 있습니다.

#### - event.type
현재 Event가 어떠한 type으로 동작하는지를 알 수 있습니다.

예를 들어, `addEventListener('click', ...)` 혹은, `<button onclick='handler'>Hello</button>`처럼 Event가 할당된다면 type은 'click'이란 정보를 저희에게 제공해줄 것입니다.

#### - event.cancelable

#### - event.cancelBubble

#### - event.eventPhase

---
## Event Methods
#### - Method : event.prevnetDefault()
Event를 취소할 수 있는 경우, Event의 전파를 막지않고 그 Event를 취소합니다. Event를 취소할 수 없는 경우(cancelable = false)는 작동되지 않습니다.

특히, HTML Tag마다 기본적인 Event가 존재하는데(예, 'A' Tag에서 href로 인한 페이지이동) 이러한 기본적으로 존재하는 Event를 취소하는데 사용됩니다.

> Event를 취소하는 도중에 preventDefault를 호출하게되면, 일반적으로는 브라우저의 구현에 의해 처리되는 기존의 액션이 동작하지 않게되고, 그 결과 Event가 발생하지 않게됩니다.
> Event의 취소가능 여부는 event.cancelable를 사용해서 확인할 수 있습니다. 취소불가능한 Event에 대해서 preventDefault를 호출해도 결과는 없습니다.
> preventDefault는 DOM을 통한 Event의 전파를 막지않습니다. 전파를 막을때는 `event.stopPropagation()`를 사용해주세요.

#### - event.stopPropagation()
Event Bubbling에과 Capturing에 있어 현재 Event 이후의 전파를 막습니다.

모든 Event는 기본적으로 bubble 속성을 가지고 있습니다. 그러므로, 전파를 막기 위한 `event.cancelable` 속성의 변경을 통해서도 Bubbling에 의한 이벤트 전파를 막을 수 있습니다.

> Capturing에 관련된 속성이 없는 이유는, Capturing은 Bubbling처럼 기본적인 속성이 아닙니다.
즉, 개발자에 의해 Capturing 이벤트가 주어졌을 떄, 전파가 방지되야하는 곳에 해당 메소드를 선언하면 쉽게 해결할 수 있습니다..

해당 메소드는 [BubblingAndCapturing](/html/event/BubblingAndCapturing)에서 더 알아보도록 하겠습니다.

## Examples
<script async src="//jsfiddle.net/SHun10114/bwtp6vh9/embed/js,html,result/"></script>

---
## References
- [HTML - Dom : Event](https://developer.mozilla.org/ko/docs/Web/API/Event)
- [HTML - Dom : Event Type](https://developer.mozilla.org/en-US/docs/Web/Events)
- [HTML - Dom : addEventListener](https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener)
