---
layout: page
title: Remove nodes greater than target
permalink: /Courses/Data_Structures/removegreater/
mathjax: true
---
~~~
public void removeAllGreaterItems(Comparable<AnyType> keyItem)
	{
		head = removeAllGreaterItems(head, keyItem);
	}
	private Node<AnyType> removeAllGreaterItems(Node<AnyType> p, Comparable<AnyType> key)
	{
		if(p == null) return null;
		else
		if(key.compareTo(p.data) < 0)
			return removeAllGreaterItems(p.next, key);
		else
			p.next = removeAllGreaterItems(p.next, key);
		return p;
	}
~~~
