---
layout: page
title: Remove nodes less than target
permalink: /Courses/Data_Structures/removeless/
mathjax: true
---
~~~
public void removeAllLesserItems(Comparable<AnyType> keyItem)
   {
      head = removeAllLesserItems(head, keyItem);
   }
   private Node<AnyType> removeAllLesserItems(Node<AnyType> p, Comparable<AnyType> key)
   {
      if(p == null) return null;
      else
      if(key.compareTo(p.data) > 0)
         return removeAllLesserItems(p.next, key);
      else
         p.next = removeAllLesserItems(p.next, key);
      return p;
   }
~~~
