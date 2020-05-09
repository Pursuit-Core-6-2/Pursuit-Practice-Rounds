# Pursuit Interview Prep Rounds

Pick a classmate as the leader of the group. The leader is in charge of taking notes and managing time.
Each station will last for 30 minutes.

## Front-End Station
* Get get though all the cards in [Flashcards For Developers](https://www.flashcardsfordevelopers.com/) in the following decks
  * [HTML, CSS & Javascript](https://www.flashcardsfordevelopers.com/decks/5b945d730d9bd6cbc6e6634f)
  * [React.js](https://www.flashcardsfordevelopers.com/decks/5b945d730d9bd6cbc6e66361)
  * [Javascript Interview Questions](https://www.flashcardsfordevelopers.com/decks/5b945d730d9bd6cbc6e66349)
* As a group discuss and collect. Leader takes notes: 
  * Concepts learned.
  * Questions for which no-one knew the answer.

## Backend-End Station
* Get get though all the cards in [Flashcards For Developers](https://www.flashcardsfordevelopers.com/) in the following decks
  * [HTTP Methods](https://www.flashcardsfordevelopers.com/decks/5b945d730d9bd6cbc6e66329)
  * [Node.js](https://www.flashcardsfordevelopers.com/decks/5b945d730d9bd6cbc6e6635f)
  * [SQL Interview Questions](https://www.flashcardsfordevelopers.com/decks/5b9ff2e7320599b445294983)
* As a group discuss and collect. Leader takes notes: 
  * Concepts learned.
  * Questions for which no-one knew the answer.

## Whiteboarding Station
* As a group get through as many questions as possible. 
* One of you shares screen
* Create and use a [Google Doc](https://docs.google.com/document/u/0/?tgif=d) as your whiteboard and share it with team members.
* Follow all the whiteboarding steps. Taking notes, pseudocoding, coding and manually testing etc.
* REPL or any means of running code is forbidden.

### Question Prompts

Click to choose a question below at random. 

<details>
  <summary>Prompt</summary>

Given an array of integers, write a function that returns a sorted list of all
the duplicates in the array.

e.g.:

```js
dupes([1, 2, 3]); // = []
dupes([1, 2, 2]); // = [2]
dupes([3, 3, 3, 3, 3]); // = [3]
dupes([2, 1, 2, 1, 8]); // = [1, 2]
```

How would you make your solution more efficient?

[Source](https://www.byte-by-byte.com/findduplicates/)

</details>

<details>
  <summary>Prompt</summary>

A linked list is a list structure made up of nodes where each node contains a
value and a reference to the next node in the list:

![Linked
  List](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Linked%20Lists/pix/linkedlist.bmp)

Given an unsorted linked list, write a function that removes all duplicates
(i.e. returns a new linked list containing only the unique values).

[Source](https://www.byte-by-byte.com/deduplinkedlist/)

</details>

<details>
  <summary>Prompt</summary>

Given two strings, write a function to determine whether they are anagrams.

e.g.:

```js
isAnagram("", "") = true
isAnagram("A", "A") = true
isAnagram("A", "B") = false
isAnagram("ab", "ba") = true
isAnagram("AB", "ab") = true
```

[Source](https://www.byte-by-byte.com/anagrams/)

</details>

<details>
  <summary>Prompt</summary>

Given an array of numbers, write a function that returns the largest difference
between two consecutive numbers in the array.

e.g.:

```js
largestDifference([1, 3]); // => 2
largestDifference([1, 3, 8]); // => 5
largestDifference([1, 3, 8, 0, 9]); // => 9
```

</details>

<details>
  <summary>Prompt</summary>

Given two unsorted strings, write a function that will return the number of
common characters.

e.g.:

```js
commonChars("abc", "abc"); // => 3
commonChars("aef", "hqa"); // => 1
commonChars("ferlv", "evlrf"); // => 5
```

</details>

<details>
  <summary>Prompt</summary>

For each character in a string return the character and the count in a compressed format. 

Example:

```js
stringCompression("aaabbcca") // => "a3b2c2a1"
stringCompression("xyzmnooo") // => "x1y1z1m1n1o3"
```

<details>
<summary>Answer:</summary>

```js
const stringCompression = str => {
  let output = "";
  let count = 0;
  for (let i = 0; i < str.length; i++) {
    count++;
    if (str[i] != str[i + 1]) {
      output += str[i] + count;
      count = 0;
    }
  }
  return output;
};
```
</details>

</details>


<details>
  <summary>Prompt</summary>

Given an array of integers, return all unique element pairs that sum up to a specified value k. List the pairs in [min, max] order.

Clarify if asked:

Aim for better than O(n^2), you can do it!
Tips:

What would the O(n^2) approach look like?
Is there a data structure you can use to improve the time complexity?
Return value can be Array of arrays or a Set of arrays

Sample inputs:

```js
pairSum([1,5,6,7,2], 9) // [[2,7]]
pairSum([9,3,3,1], 2) // []
```

<details>
<summary>Answer:</summary>

```js
const pairSum = (arr, target) => {
  const seen = {}
  const pairs = new Set()

  arr.forEach(el => {
    const searching = target - el

    if (seen[el] !== undefined) {
      const pair = [Math.min(el, searching), Math.max(el, searching)]
      pairs.add(JSON.stringify(pair))
    } else {
      seen[searching] = el
    }
  })

  return pairs
}

```

</details>
</details>


<details>
  <summary>Prompt</summary>


Given a matrix of integers and the top left and bottom right coordinates of a rectangular area within the matrix, find the sum of numbers falling inside the rectangle.

Clarifying answers: 
* Input is a 2d array
* 2nd arg is an array of x,y coordinates (top left of rect)
* 3rd arg is an array of x,y coordinates (bottom right of rect)
* Row/column indices are inclusive (`sumMatrix(matrix, [1, 2], [3, 2])` will include values at 1,2 and 3,2

Example:
```js
// matrix
let matrix = [
  [1, 2, 3, 4]
  [5, 6, 7, 8]
  [9, 0, 1, 2]
]

sumMatrix(matrix, [1, 1], [3, 2]) //=> 24
```

<details>
<summary>Answer:</summary>

```js
const sumMatrix = (mtx, leftTop, rightBottom) => {
	let sum = 0;
	for(let i = leftTop[0]; i <= rightBottom[0]; i++) {
		for(let j = leftTop[1]; j <= rightBottom[1]; j++) {
			sum += mtx[j][i]
		}
	}
	return sum
}
```
</details>
</details>


<details>
  <summary>Prompt</summary>

Write a function that takes an array of integers and **recursively** computes the sum.

Clarify if needed:

Time complexity should be O(n)

Hints

What is the base case?
What is the result of sum_rec([])?
What is the time complexity of slice etc?
(It's O(n), so if we slice on each recursive call, time complexity bumps to O(n ^ 2))
How can we avoid creating a new array each time?


<details>
<summary>Answer:</summary>

```js
const sumRec = (arr, head = 0, tail = arr.length, sum = 0) => {
  if (head === tail) return sum;
  return sumRec(arr, head + 1, tail, sum + arr[head]);
}
```
</details>
</details>



<details>
  <summary>Prompt</summary>

### Flatten
Write a function that flattens a multi dimensional array

Example:

```js
flatten([[1,2,5], [3,3]]) // [1, 2, 5, 3, 3]
flatten([["apple", "banana"], ["fox", 1, "2"]]) // [ 'apple', 'banana', 'fox', 1, '2' ]
```

<details>
<summary>Answer:</summary>

```js
const flatten = (arr) => {
	return arr.reduce((acc, currEl) => {
		return acc.concat(Array.isArray(currEl) ? flatten(currEl) : currEl)
	}, [])
}
```
</details>
</details>




<details>
  <summary>Prompt</summary>

Write a function, findMiddle, that accepts a Linked List's head node as an argument, passes through the list once, and returns the value in the middle node. If there are two middle nodes, return the second middle node.

Hints:

A linked list is made of of nodes with the structure:

```js

let node = {
  value: 3,
  next: null // next value is null or is another object with the same structure
}
```


<details>
<summary>Answer:</summary>

```js
function findMiddle(head) {
  let [runner, walker] = [head, head];
  while(runner.next && runner.next.next) {
      runner = runner.next.next;
      walker = walker.next
  }
  if (runner.next) {
    return walker.next.value
  }
  else return walker.value
};
```

</details>
</details>

## Group Programming-Live Coding Station

* As a group
* Implement in REPL any of the questions from the whiteboarding station you and your group solved. Verify that it yields the correct output.
* Alternatively solve the following questions
  * https://leetcode.com/problems/merge-two-sorted-lists/
  * https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/

## Rotation
Front-End -> Back-End -> Whiteboarding -> Group-Programming ↴
↑                                                           |
↑⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵⟵ ↲
