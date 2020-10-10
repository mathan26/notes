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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NzA4MzIyNDcsMTU5NDk4Mjc1LC05OT
QyMjg1MTgsLTE3NzQwNDY0MTgsLTMyMTU3ODgsMzIwODkyNTYx
LDI2MDUxNDY2OSwxMjg2MzgzOTA3LDE2Njg2MTIwNDIsLTE3OD
c3MTk5NzhdfQ==
-->