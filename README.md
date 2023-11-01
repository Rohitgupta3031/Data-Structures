package LinkedList;

import java.util.Scanner;

class Node

{
	int data;

	Node left, right;

	Node(int data)

	{
		this.data = data;

		left = right = null;

	}
}

public class CircularDoubly {
	Node root, last;

	void createList() {
		root = last = null;// root is not created but assigned
	}

	void insertLeft(int data) {

		Node n = new Node(data);// created node

		if (root == null)// not created

		{

			root = last = n;// 1st one assigned as root

		}

		else

		{
			n.right = root;// 1

			root.left = n;// 2

			root = n;// 3

			last.right = root;

			root.left = last;

		}

		System.out.println("Inserted");

	}

	void deleteLeft()

	{

		if (root == null)// not created

		{

			System.out.println("List Empty:");

		}

		else

		{
			Node t = root;// 1

			if (root.right == null)// single node

				root = null;

			else

			{

				root = root.right;// 2

				root.left = null;// 3

				last.right = root;

				root.left = last;

			}

			System.out.println(t.data + " deleted");

		}

	}

	void deleteRight()

	{

		if (root == null)// not created

			System.out.println("List Empty:");

		else

		{

			if (last == root)// single node only

				root = null;// maual deletion

			else

			{

				Node t2 = last.left;// 3

				t2.right = null;//

				last = t2;

				last.right = root;

				root.left = last;

			} // 3

			System.out.println(" deleted");

		}

	}

	void insertRight(int data)

	{

		Node n = new Node(data);// created node

		if (root == null)// not created

		{

			root = last = n;// 1st one assigned as root

		}

		else

		{

			last.right = n;// 3

			n.left = last;// 4

			last = n;

			last.right = root;

			root.left = last;

		}

		System.out.println("Inserted");

	}

	void printListLR()

	{

		if (root == null)// not created

		{

			System.out.println("Empty list:");

		}

		else

		{
			Node t = root;// 1

			// 2

			do {

				System.out.print("|" + t.data + "|->");

				t = t.right;

			} while (t != root);

		}

	}

	void printListRL()

	{

		if (root == null)// not created

		{

			System.out.println("Empty list:");

		}

		else

		{
			Node t = last;// 1

			// 3

			do {
				System.out.print("|" + t.data + "|->");

				t = t.left;

			} while (t != last);

		}

	}

	public static void main(String args[])

	{

		CircularDoubly obj = new CircularDoubly();

		Scanner in = new Scanner(System.in);

		int ch, e;

		obj.createList();// creating LinkedList

		do

		{

			System.out.println(
					"\n 1.Insert Left "
					+ "\n 2.Insert Right "
					+ "\n 3.DeleteLeft "
					+ "\n 4.DeleteRight"
					+ "\n 5.Print_Start_To_End"
					+ "\n 6.Print_End_To_Start"
					+ "\n 0.Exit ");

			ch = in.nextInt();

			switch (ch)

			{

			case 1:

				System.out.println("Enter element:");

				e = in.nextInt();

				obj.insertLeft(e);

				System.out.println("Element Inserted");

				break;

			case 2:

				System.out.println("Enter element:");

				e = in.nextInt();

				obj.insertRight(e);

				System.out.println("Element Inserted");

				break;

			case 3:

				obj.deleteLeft();

				break;

			case 4:

				obj.deleteRight();

				break;

			case 5:

				obj.printListLR();

				break;

			case 6:

				obj.printListRL();

				break;

			case 0:

				System.out.println("Exiting....");

				break;

			default:

				System.out.println("Wrong option selected");

				break;

			}

		} while (ch != 0);

	}

}
