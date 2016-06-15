---
layout: page
title: Find Last
permalink: /Courses/Data_Structures/findlast/
mathjax: true
---
~~~
public static IntNode last(IntNode front){
	if (front == null){
	    return null;
	} else {
	    IntNode ptr;
	    for (ptr = front; ptr.next != null; ptr = ptr.next){
	    }
	    return ptr;
	}
    }
~~~
