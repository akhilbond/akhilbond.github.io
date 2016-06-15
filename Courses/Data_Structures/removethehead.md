---
layout: page
title: Remove the Head
permalink: /Courses/Data_Structures/removethehead/
mathjax: true
---
~~~
public AnyType removeFirst()
	{
		AnyType tmp = getFirst();
		head = head.next;
		return tmp;
	}
~~~
