---
layout: page
title: Insert after Node
permalink: /Courses/Data_Structures/insertafternode/
mathjax: true
---
~~~
public static boolean addAfter(IntNode front, int target, int item){
	for (IntNode ptr = front; ptr != null; ptr = ptr.next){
	    if (ptr.data == target){
		ptr.next = new IntNode(item, ptr.next);
		return true;
	    }
	}
	return false;
    }
~~~
