---
layout: page
title: Traverse the List
permalink: /Courses/Data_Structures/travrselist/
mathjax: true
---
~~~
public static void traverse(IntNode front) {
		if (front == null) {
		    System.out.println("null");
		} else {
		    System.out.print(front.data);
		    for (IntNode ptr=front.next; ptr != null; ptr=ptr.next) {
			System.out.print(" --> ");
			System.out.print(ptr.data);
		    }
		    System.out.println();
		}
	}
~~~
