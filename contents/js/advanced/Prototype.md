# Javascript, Prototype

이번 시간에는 class와 Object를 비교하여 Prototype에 대해서 알아보고자 합니다.

## Objective Oretiented Pragramming

프로토타입에 나아가기에 앞서 객체지향을 간단히 언급해보겠습니다.
객체지향의 3요소는 캡슐화, 은닉화, 다형성입니다. 특히, 객체지향 언어인 Java에서는 Class, Access modifier, Interface 등으로 이를 구성할 수 있습니다.

하지만, 우리가 알아야 할 초기 JS에는 Class(ES6), Access modifier(ES5), Interface의 개념이 존재하지 않습니다. (Typescript는 모두 존재합니다. - 구현된 객체로서...)

그렇다면, JS에서는 객체지향 코드를 일반적인 객체지향 사고로 어떻게 구현할 수 있을까요?
간단히 언급하면 Javascript에서는 이를 구현하기 위해서는 Prototype, Scope, Closure의 개념이 필요합니다.

이에 대해서 얘기하려면 너무 길어지니, 하나씩 나누어서 같이 알아보고자 합니다.

먼저, Prototype에 대해서 알아보고자 합니다.

## Prototype
Prototype은 자바스크립트를 객체지향으로 구성할 수 있도록 도와주는 요소입니다.

기본적으로 JS는 모든 객체는 Object의 인스턴스입니다. 일반적으로 JS의 모든 객체는 Object.prototype을 통해 속성과 메소드를 상속받고 있습니다.

<!--
그러나, 의도적으로 Object를 생성할 때 (Object.create(null) 처럼) 이를 피할 수도 있고, Object.setPrototypeOf 등을 통해 나중에 무효화할 수도 있습니다.
-->
