---
layout: post
title: C# Collection 순회 도중에 원소 삭제 하는 방법
published: false
date: 2017-01-03
categories: [C#]
---

C#에서 List, Dictionary 등의 Collection을 사용하면서 원소를 순회할 때는 보통 foreach 구문을 사용한다.
그런데 다음과 같이 foreach 중에 원소를 삭제하면, Exception이 발생한다.

```C#
foreach (var item in items)
{
   ...
   if (some condition)
      items.delete(item);
}
```
