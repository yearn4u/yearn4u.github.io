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
      items.Remove(item);
}
```

이와 같은 문제를 해결하기 위해서 여러가지 방법이 있을 수 있다.

첫 번째로 foreach를 포기하고 while loop을 사용하는 방법이다.


```C#
int idx = 0;
while (idx < items.Count)
{
   ...
   if (some condition)
      items.RemoveAt(idx);
   else
      ++idx;
}
```

두 번째로 삭제해야 할 원소를 별도의 collection에 저장하고, 순회가 종료된 후에 일괄 삭제하는 방법이다.

```C#
for (int i = 0; i < elements.Count; i++)
{
    if (<condition>)
    {
        // Decrement the loop counter to iterate this index again, since later elements will get moved down during the remove operation.
        elements.RemoveAt(i--);
    }
}
```

[출처](http://stackoverflow.com/questions/1582285/how-to-remove-elements-from-a-generic-list-while-iterating-over-it)
