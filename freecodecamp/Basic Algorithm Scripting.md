## Convert Celsius to Fahrenheit

 - The algorithm to convert from Celsius to Fahrenheit is the temperature in Celsius times 9/5, plus 32.
 

> You are given a variable celsius representing a temperature in Celsius. Use the variable fahrenheit already defined and assign it the Fahrenheit temperature equivalent to the given Celsius temperature. Use the algorithm mentioned above to help convert the Celsius temperature to Fahrenheit.
> 

    function convertToF(celsius) {
      let fahrenheit;
      fahrenheit = ((9/5) * celsius) + 32;
      console.log(fahrenheit)
      return fahrenheit;
    }
    
    convertToF(0);
## Reverse a String

 - Reverse the provided string.
   You may need to turn the string into an array before you can reverse
   it.Your result must be a string.


		function reverseString(str) {
		  return str.split('').reverse().join('');
		}

		reverseString("hello");
## Factorialize a Number

 - Return the factorial of the provided integer.

	    function factorialize(num) {
	      for (var product = 1; num > 0; num--) {
	        product *= num;
	      }
	      return product;
	    }
	    
	    //Recursion
	    
	    factorialize(5);
	    
	    
	    function factorialize(num) {
	      if(num==0){
	        return 1;
	      }
	      return num * factorialize(num-1);
	    }
	    
	    console.log(factorialize(5));

## Find the Longest Word in a String

    function findLongestWordLength(s) {
      return s.split(' ')
        .reduce(function(x, y) {
          return Math.max(x, y.length)
        }, 0);
    }

Using .map()

    function findLongestWordLength(str) {
      return Math.max(...str.split(" ").map(word => word.length));
    }
## Return Largest Numbers in Arrays


>  Return an array consisting of the largest number from each provided
> sub-array. For simplicity, the provided array will contain exactly 4
> sub-arrays.
> 
> Remember, you can iterate through an array with a simple for loop, and
> access each member with array syntax arr[i].

    function largestOfFour(arr) {
      return arr.map(a=>{
        return a.reduce((prev,currentItem)=>{
          return prev > currentItem ? prev :currentItem;
        });
      });
    }
    console.log(largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]));
    largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
## Confirm the Ending

 - Check if a string (first argument, str) ends with the given target string (second argument, target).

	    function confirmEnding(str, target) {
	      console.log(str.substring(str.length-target.length)===target)
	      return str.substring(str.length-target.length)===target;
	    }
	    
	    confirmEnding("Congratulation", "on");
## Repeat a String Repeat a String

    function repeatStringNumTimes(str, num) {
      return num > 0 ? str + repeatStringNumTimes(str, num - 1) : '';
    }
    repeatStringNumTimes("abc", 3);
## Truncate a String

> Truncate a string (first argument) if it is longer than the given
> maximum string length (second argument). Return the truncated string
> with a ... ending.

    function truncateString(str, num) {
      return str.length > num ? str.slice(0,num) + "...": str;
    }
    
    truncateString("A-tisket a-tasket A green and yellow basket", 8);

## Finders Keepers

> Create a function that looks through an array arr and returns the
> first element in it that passes a 'truth test'. This means that given
> an element x, the 'truth test' is passed if func(x) is true. If no
> element passes the test, return undefined.

	    function findElement(arr, func) {
	      let num = 0;
	    
	      for (var i = 0; i < arr.length; i++) {
	        num = arr[i];
	        if (func(num)) {
	          return num;
	        }
	      }
	    
	      return undefined;
	    }
     //Another solution
    function findElement(arr, func) {
      return arr.find(func);
    }

## Boo who

> Check if a value is classified as a boolean primitive. Return true or
> false.
> 
> Boolean primitives are true and false.

    function booWho(bool) {
      return typeof bool === "boolean";
    }
    
    // test here
    booWho(null);

## Title Case a Sentence

> Return the provided string with the first letter of each word
> capitalized. Make sure the rest of the word is in lower case.
> 
> For the purpose of this exercise, you should also capitalize
> connecting words like "the" and "of".

    function titleCase(str) {
    
      let convertedArray = str.toLowerCase().split(" ");
      let result = convertedArray.map(e=>{
        return e.replace(e.charAt(0),e.charAt(0).toUpperCase());
      })
    
      return result.join(" ");
    }
    
    console.log(titleCase("I'm a little tea pot"));

## Slice and Splice

> You are given two arrays and an index.
> 
> Copy each element of the first array into the second array, in order.
> 
> Begin inserting elements at index n of the second array.
> 
> Return the resulting array. The input arrays should remain the same
> after the function runs.

    function frankenSplice(arr1, arr2, n) {
      // It's alive. It's alive!
      let localArray = arr2.slice();
      for (let i = 0; i < arr1.length; i++) {
        localArray.splice(n, 0, arr1[i]);
        n++;
      }
      return localArray;
    }

## Falsy Bouncer

> Remove all falsy values from an array.
> 
> Falsy values in JavaScript are false, null, 0, "", undefined, and NaN.
> 
> Hint: Try converting each value to a Boolean.

    function bouncer(arr) {
      return arr.filter(a=>a);
    }
    
     console.log(bouncer([7, "ate", "", false, 9]));

## Where do I Belong

> Return the lowest index at which a value (second argument) should be
> inserted into an array (first argument) once it has been sorted. The
> returned value should be a number.
> 
> For example, getIndexToIns([1,2,3,4], 1.5) should return 1 because it
> is greater than 1 (index 0), but less than 2 (index 1).
> 
> Likewise, getIndexToIns([20,3,5], 19) should return 2 because once the
> array has been sorted it will look like [3,5,20] and 19 is less than
> 20 (index 2) and greater than 5 (index 1).

    function getIndexToIns(arr, num) {
      return arr
        .concat(num)
        .sort((a, b) => a - b)
        .indexOf(num);
    }
    
    getIndexToIns([40, 60], 50);

## Mutations

> Return true if the string in the first element of the array contains
> all of the letters of the string in the second element of the array.
> 
> For example, ["hello", "Hello"], should return true because all of the
> letters in the second string are present in the first, ignoring case.
> 
> The arguments ["hello", "hey"] should return false because the string
> "hello" does not contain a "y".
> 
> Lastly, ["Alien", "line"], should return true because all of the
> letters in "line" are present in "Alien".

    function mutation(arr) {
      return arr[1]
        .toLowerCase()
        .split("")
        .every(function(letter) {
          return arr[0].toLowerCase().indexOf(letter) != -1;
        });
    }
    mutation(["hello", "hey"]);

## Chunky Monkey

> Write a function that splits an array (first argument) into groups the
> length of size (second argument) and returns them as a two-dimensional
> array.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDQzNzIzMDM5LC0xNDc4MDQyOTIwLDYzOD
MyMDUzMywtMTgyODU3OTg2MSwtMTU3MDgzMjI0NywxNTk0OTgy
NzUsLTk5NDIyODUxOCwtMTc3NDA0NjQxOCwtMzIxNTc4OCwzMj
A4OTI1NjEsMjYwNTE0NjY5LDEyODYzODM5MDcsMTY2ODYxMjA0
MiwtMTc4NzcxOTk3OF19
-->