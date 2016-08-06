---
layout: page
title: Generic Code for BST traversals
permalink: /Courses/Data_Structures/traversalgeneric/
mathjax: true
---

{% highlight Java %}
// Java program for different tree traversals

/* Class containing left and right child of current
node and key value*/
class Node<T>
{
	T key;
	Node<T> left, right;

	public Node(T item)
	{
		key = item;
		left = right = null;
	}
}

class BinaryTree<T>
{
	// Root of Binary Tree
	Node<T> root;

	BinaryTree()
	{
		root = null;
	}

	/* Given a binary tree, print its nodes according to the
	"bottom-up" postorder traversal. */
	void printPostorder(Node<T> node)
	{
		if (node == null)
			return;

		// first recur on left subtree
		printPostorder(node.left);

		// then recur on right subtree
		printPostorder(node.right);

		// now deal with the node
		System.out.print(node.key + " ");
	}

	/* Given a binary tree, print its nodes in inorder*/
	void printInorder(Node<T> node)
	{
		if (node == null)
			return;

		/* first recur on left child */
		printInorder(node.left);

		/* then print the data of node */
		System.out.print(node.key + " ");

		/* now recur on right child */
		printInorder(node.right);
	}

	/* Given a binary tree, print its nodes in preorder*/
	void printPreorder(Node<T> node)
	{
		if (node == null)
			return;

		/* first print data of node */
		System.out.print(node.key + " ");

		/* then recur on left sutree */
		printPreorder(node.left);

		/* now recur on right subtree */
		printPreorder(node.right);
	}

	// Wrappers over above recursive functions
	void printPostorder() {	 printPostorder(root); }
	void printInorder() {	 printInorder(root); }
	void printPreorder() {	 printPreorder(root); }

	// Driver method
	public static void main(String[] args)
	{
		BinaryTree<Character> tree = new BinaryTree<Character>();
		tree.root = new Node<Character>('A');
		tree.root.left = new Node<Character>('B');
		tree.root.right = new Node<Character>('C');
		tree.root.right.left = new Node<Character>('E');
		tree.root.right.right = new Node<Character>('F');

		BinaryTree<Integer> treeint = new BinaryTree<Integer>();
		treeint.root = new Node<Integer>(1);
		treeint.root.left = new Node<Integer>(2);
		treeint.root.right = new Node<Integer>(3);
		treeint.root.left.left = new Node<Integer>(4);
		treeint.root.left.right = new Node<Integer>(5);


		System.out.println("Preorder traversal of binary tree is ");
		tree.printPreorder();

		System.out.println("\nInorder traversal of binary tree is ");
		tree.printInorder();

		System.out.println("\nPostorder traversal of binary tree is ");
		tree.printPostorder();

		System.out.println("\nPreorder traversal of integer binary tree is ");
		treeint.printPreorder();

		System.out.println("\nInorder traversal of integer binary tree is ");
		treeint.printInorder();

		System.out.println("\nPostorder traversal of integer binary tree is ");
		treeint.printPostorder();
	}
}
{% endhighlight %}
