COMP 313/413 Project 2 Report Template

TestList.java and TestIterator.java

	TODO also try with a LinkedList - does it make any difference?

		It doesn't seem to make any difference with functionality. However, performance may change.

TestList.java

	testRemoveObject()

		list.remove(5); // what does this method do?

			The method above removes the value at the given index from the list which in this case was index 5 (or the 6th element because zero indexing)

		list.remove(Integer.valueOf(5)); // what does this one do?

			The method above removes the literal value from that list, not the index position. We explicitly pass an Integer object so Java uses the overloaded remove method
            This call removes the first occurrence of the value 5 from the list, if it exists.

TestIterator.java

	testRemove()

		i.remove(); // what happens if you use list.remove(77)?

			If you use the list.remove() method instead of the existing iterator remove method, the iterator will throw an error because something has changed the list during
			iteration, and it doesn't like that so it throws a ConcurrentModificationException. this is why i.remove() is preferred, because it removes the current element safely

TestPerformance.java

	State how many times the tests were executed for each SIZE (10, 100, 1000 and 10000)
	to get the running time in milliseconds and how the test running times were recorded.

	I utilized the timing functions found when running tests through IntelliJs IDEA. It displays how long the test you just ran took, and they're recorded below

	SIZE 10
								 #1  #2  #3
        testArrayListAddRemove:  19  20  20
        testLinkedListAddRemove: 19  18  19
		testArrayListAccess:      9   9  10
        testLinkedListAccess:    11   9  11

	SIZE 100
								  #1   #2   #3
        testArrayListAddRemove:   27   26   26
        testLinkedListAddRemove:  15   20   19
		testArrayListAccess:      11    9    7
        testLinkedListAccess:     17   19   21

	SIZE 1000
								  #1    #2   #3
        testArrayListAddRemove:   106  109  105
        testLinkedListAddRemove:  19    14   15
		testArrayListAccess:       7    11    8
        testLinkedListAccess:     295  289  295

	SIZE 10000
								   #1     #2     #3
        testArrayListAddRemove:   998    992    996
        testLinkedListAddRemove:   20     19     18
		testArrayListAccess:       11      9     11
        testLinkedListAccess:    3976   3935   3912

	listAccess - which type of List is better to use, and why?

		ArrayLists would be preferred for access as we can see from the timing above. This makes sense because we can just lookup values instantly with an index in O(1)
		complexity, instead of needing to traverse the list like you would with a linkedlist

	listAddRemove - which type of List is better to use, and why?

        LinkedLists would be preferred for adding and remove values as proven by the timing above. This is because we can edit pointers whenever you add or remove an item, doing it
        in constant time O(1). If you we're to try to do this with an ArrayList, you would need to copy all of the values over, causing it to take O(N) time, which we can see above.
