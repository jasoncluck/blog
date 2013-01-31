---
layout: post
title: "Amazon - third interview and offer"
date: 2013-01-30 10:08
comments: true
categories: Amazon Interviews
---

I was notified a few days after the first two Amazon interviews that they wanted to have a third interview.  They had to reschedule once due to a timing conflict but I had the third interview last Thursday (1/24).  The agenda was the same as the other interviews and began with questions about a Rails project I've done recently.  Next was some questions about binary search trees (glad I studied those).  I was able to answer these questions and figured out the number of leaf nodes and total nodes in a complete BST of height __h__ by writing out an example.

<!--more-->

The programming portion was next and I got on collabedit again.  The first question was to write a function to tell if two strings are anagrams of each other.  I knew this one! I actually reviewed the solutions the day before so I told the interviewer it was a familiar problem and he had me solve it anyways.  I mentioned three solutions: 

1. Sort the strings using a basic sort such as quicksort to avoid using additional space - O(nlogn) time.  If the sorted strings are the same they are anagrams.

2. Allocate an array that is the size of the total possible characters in the character set (ASCII or Unicode).  For the first string, increment the characters location in the array every time it is seen, then decrement it for the second string.  Check to see if the array is zeroed out and if so, its an anagram. This is similiar to counting sort.

3. If we constrict the requirements to only allowing unique lowercase ASCII characters it becomes more feasible to do a bitwise solution.  Using an 32-bit int, we can bit shift over by that character's value (subtract 'a' from character to get bits 0-25).  Then flip the bits back if the second string also has any of the bits from the first string.  At the end just check to see if the int is equal to 0 and the result is an anagram.

I implemented version 2. of the anagram code with ASCII in Java and then he asked me another problem.  Given a value k, what is a good approach for returning the max k values from an unsorted array.  So if k=1 we return the max, k=2 we return the max and the second max etc.  I thought about this by starting with k=1.  It will take at least O(n) time to return just 1, but as k grows the compute time will grow rapidly.  I started thinking of data structures to use beginning with a BST (probably because it was fresh in my mind).  This would work because the elements are sorted but the tree traversals would get ugly and complicated.  I then decided on using a max-heap because it takes n time to assemble and can easily reorganize to provide the next element.

I asked some questions about Amazon and then the interview was over.  After much anticipation I received an offer yesterday and spoke with a recruiter about all the details.  I have already accepted so I will moving to Seattle for the summer.  The team I will be working on is called eCPS which focuses on scalability and reliable with web services.  The website has more details [here]("http://ecps.amazon.com/").

Some lessons that I learned: 

* Practice programming problems! Tons of these on StackOverflow, Careercup, Glassdoor etc.

* Take Steve Yegge's advice and warm up the day of.  Do some really common interview problems like recursive tree traversals, hash tables, and string manipulation.

* Tell the interviewers if you've solved the problem before! People want honest teammates.

* Work on programming projects in your free time.  I'm pretty sure I only got an interview because I taught myself Rails and wrote some projects with it for fun.

Anyways, I hope this helps someone else with getting the job they want!  I'd be glad to answer any questions via email: jcluck@gwmail.gwu.edu.
