---
layout: page
title: Search the List
permalink: /Courses/Data_Structures/search/
mathjax: true
---
~~~
public static boolean search(IntNode front, int target) {
		for (IntNode ptr=front; ptr != null; ptr=ptr.next) {
			if (target == ptr.data) {
				return true;
			}
		}
		return false;
	}
~~~
