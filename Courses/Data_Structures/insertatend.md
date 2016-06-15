---
layout: page
title: Insert at End
permalink: /Courses/Data_Structures/insertatend/
mathjax: true
---
~~~
public void addLast(AnyType item)
	{
		if( head == null)
			addFirst(item);
		else
			addLast(head, item);
	}
	private void addLast(Node<AnyType> node, AnyType item)
	{
		if(node.next != null) addLast(node.next, item);
		else
			node.next = new Node<AnyType>(item, null);
	}
~~~
