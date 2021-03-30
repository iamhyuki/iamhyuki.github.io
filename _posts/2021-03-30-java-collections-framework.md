---
title: Java Collections Framework
description: Java의 대표적인 자료구조인 Collection에 대해서 알아봅니다.
date: 2021-03-31 00:20:00 +0900
categories: datastructure
tag: [datastructure, java]
toc: true
toc_sticky: true
layout: single 
---

## Java Collections Framework

**컬렉션 프레임워크란?** 다수의 데이터를 쉽고 효과적으로 처리할 수 있는 표준화된 방법을 제공하는 클래스의 집합을 의미한다.
즉, 데이터를 저장하는 자료 구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현해 놓은 것이다.
  
이러한 컬렉션 프레임워크는 자바의 인터페이스를 사용하여 구현된다.
  
<p align="center">
       <img src="/images/2021-03-31/img_java_collection_interface_diagram.png" alt="" style="zoom: 100%;" />
</p>
  
Collection 인터페이스 상위에 있는 **iterable 인터페이스** 존재에 의문이 들 수 있다. 검색해보면 iterable은 스페인어로 '반복가능한' 이라는 뜻으로 나온다.(영어에서 iteration은 반복을 의미한다.) 컬렉션 프레임워크의 클래스들은 모두 객체 형태로 내부 구현 또는 대개 Object[] 배열 형태가 아니라 각각의 객체를 갖고 움직인다. 그래서 객체의 데이터들을 모두 순회하면서 출력하려면 사용자들이 각각의 데이터 순회 방법을 알거나 하나씩 get() 같은 메소드를 통해 데이터를 하나씩 꺼내와야 한다. 하지만 Iterable은 for-each를 제공한다. Iterable을 구현받은 클래스들은 기본적으로 for-each 문법을 쉽게 사용할 수 있다. 한마디로 **반복자로 구현되어 나오게 하는 것**이다.
  
또한 Map 인터페이스는 따로 구분되어 있다. Collection 인터페이스와는 별개지만, json의 형식과 유사한 key-value 자료구조로 자주 쓰인다.
  
## Collections Framework의 주요 인터페이스
  
### Collection 인터페이스
<p align="center">
       <img src="/images/2021-03-31/java-collection-hierarchy.png" alt="" style="zoom: 75%;" />
</p>
  
#### List
List Interface는 대표적인 선형 자료구조이다. 배열의 기능을 갖고 있으며, 배열의 단점을 보완하여 동적으로 크기를 할당할 수 있다.
  
**<List Interface의 대표적인 메소드>**
<p align="center">
       <img src="/images/2021-03-31/list-interface-method.png" alt="" style="zoom: 75%;" />
</p>
  
------
- **ArrayList**는 Object[] + 동적 크기 할당이 가능하다. 요소 조회 성능이 우수하나, 중간 요소에 삽입, 삭제가 일어나는 경우에는 비효율적이다.
- **LinkedList**는 데이터와 주소로 이루어진 클래스인 Node(노드)를 이전 노드와 다음 노드를 연결하는 방식으로 이뤄져 있다. 인덱스가 없어 조회 성능이 떨어지나, 해당 노드를 삽입, 삭제하는 경우에는 성능이 우수하다.
- **Vector**는 Collection Framework가 도입되기 전부터 지원하던 클래스로, 기본적으로 ArrayList와 거의 동일하다. 항상 동기화를 지원하는데, (쉽게 말해 여러 쓰레드가 동시에 데이터에 접근하려하면 순차적으로 처리하도록 한다.) 멀티 쓰레드에서는 안전하지만, 단일쓰레드에서도 동기화를 하기 때문에 ArrayList에 비해 성능이 약간 떨어진다.
- **Stack**은 LIFO(Last-in First-Out : 후입선출) 구조로 되어 있다. Vector 클래스를 상속받고 있다.
  
#### Queue
Queue Interface는 선형 자료구조로 주로 순서가 있는 데이터를 기반으로 FIFO(First-in First-out : 선입선출)을 위해 만들어진 인터페이스다.
  
**<Queue/Deque Interface의 대표적인 메소드>**
<p align="center">
       <img src="/images/2021-03-31/queue-interface-method.png" alt="" style="zoom: 75%;" />
</p>
  
------
- **LinkedList**는 Node 객체를 연결해서 관리한다. Queue와 Deque의 둘 다의 용도로 사용 가능하다.
- **ArrayDeque**는 Object[]로 구현되어 있다. Deque 또한 Queue를 상속받았기 때문에 Queue로도 사용 가능하다.
- **PriorityQueue**는 직역한 그대로 우선순위 큐다. 데이터 우선순위에 기반하여 우선순위가 높은 데이터가 먼저 나오는 원리다. 기본값으로 낮은 숫자가 높은 우선순위를 갖는다. 사용자가 정의한 객체를 타입으로 쓸 경우 반드시 정렬 방식을 구현해줘야 한다.
  
#### Set
말 그대로 '집합'이다. 데이터 중복이 불가능하며, 저장 순서를 보장하지 않는다는 특징이 있다. (물론 예외도 있다.)
  
**<Set Interface의 대표적인 메소드>**
<p align="center">
       <img src="/images/2021-03-31/set-interface-method.png" alt="" style="zoom: 75%;" />
</p>
  
------
- **HashSet**은 가장 기본이 되는 Set으로, Set의 특징을 고스란히 갖고 있다. 삽입, 삭제, 색인이 매우 빠른 컬렉션 중 하나다.
- **LinkedHashSet**은 중복은 허용하지 않으면서 순서를 보장받고 싶은 경우에 사용한다.
- **TreeSet**은 SortedSet Interface를 상속받은 Set으로, 가중치에 따른 순서대로 정렬되어진다. 중복되지 않으면서 특정 규칙에 의해 정렬된 형태의 집합을 사용하고 싶을 때 쓴다.
  
### Map 인터페이스
키와 값이 한 쌍으로 이루어지는 데이터의 집합으로 순서가 없다. 키는 중복을 허용하지 않지만, 값은 중복이 가능하다.
<p align="center">
       <img src="/images/2021-03-31/map-interface-1.png" alt="" style="zoom: 85%;" />
</p>
  
### 적절한 자료구조 사용하기
<p align="center">
       <img src="/images/2021-03-31/data-structure-javabeans.png" alt="" style="zoom: 90%;" />
</p>
  
###### 참고 문헌
[ 컬렉션 프레임워크의 개념 / TCP School ](http://tcpschool.com/java/java_collectionFramework_concept)
  
[ 자바 컬렉션 프레임워크 / st-lab 티스토리 블로그 ](https://st-lab.tistory.com/142?category=856997)