
## Sum All Numbers in a Range

> We'll pass you an array of two numbers. Return the sum of those two
> numbers plus the sum of all the numbers between them. The lowest
> number will not always come first.
> 
> For example, sumAll([4,1]) should return 10 because sum of all the
> numbers between 1 and 4 (both inclusive) is 10.

**Normal Solution**

    function sumAll(arr) {
      let sum=0;
      for(let i=Math.min(...arr);i<=Math.max(...arr);i++){
        console.log(i);
        sum +=i;
      }
      return sum;
    }
    
    console.log(sumAll([1, 4]));
**Using Mathematic formula:**

 - The formula for calculating the sum of a continuous range is “(startNum + endNum) * numCount / 2”.
 - Get the count of numbers between the two numbers by subtracting them and add 1 to the absolute value.


	    const sumAll = arr => {
	      // Buckle up everything to one!
	      const startNum = arr[0];
	      const endNum = arr[1];
	    
	      // Get the count of numbers between the two numbers by subtracting them and add 1 to the absolute value.
	      // ex. There are |1-4| + 1 = 4, (1, 2, 3, 4), 4 numbers between 1 and 4.
	      const numCount = Math.abs(startNum - endNum) + 1;
	    
	      // Using Arithmetic Progression summing formula
	      const sum = ((startNum + endNum) * numCount) / 2;
	      return sum;
	    };
## Diff Two Arrays

> Compare two arrays and return a new array with any items only found in
> one of the two given arrays, but not both. In other words, return the
> symmetric difference of the two arrays.
> 
> Note You can return the array with its elements in any order.

	    function diffArray(arr1, arr2) {
	    
	      return arr1.concat(arr2).
	            filter(item=>!arr1.includes(item) || !arr2.includes(item));
	    }
	    
	    diffArray([1, 2, 3, 5], [1, 2, 3, 4, 5]);

		// Another solution:
		
	    function diffArray(arr1, arr2) {
	      return [...diff(arr1, arr2), ...diff(arr2, arr1)];
	    
	      function diff(a, b) {
	        return a.filter(item => b.indexOf(item) === -1);
	      }
	    }
## Seek and Destroy
You will be provided with an initial array (the first argument in the destroyer function), followed by one or more arguments. Remove all elements from the initial array that are of the same value as these arguments.

Note
You have to use the arguments object.

	    function destroyer(arr,...arg) {
	     return arr.filter(item=>{
	       return !arg.includes(item);
	        //return arg.every(argItem=>argItem!==item);
	      });
	    }
	    
	    destroyer([1, 2, 3, 1, 2, 3], 2, 3);
	    console.log(destroyer([1, 2, 3, 1, 2, 3], 2, 3))

## Wherefore art thou

> Make a function that looks through an array of objects (first
> argument) and returns an array of all objects that have matching name
> and value pairs (second argument). Each name and value pair of the
> source object has to be present in the object from the collection if
> it is to be included in the returned array.

For example, if the first argument is [{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }], and the second argument is { last: "Capulet" }, then you must return the third object from the array (the first argument), because it contains the name and its value, that was passed on as the second argument.

	    function whatIsInAName(collection, source) {
	      var arr = [];
	      // Only change code below this line
	      var srcKeys = Object.keys(source);
	      arr=collection.filter(item=>{
	        return srcKeys.every(srcKey=>{
	          console.log(item[srcKey]===source[srcKey]);
	          return item.hasOwnProperty(srcKey) && item[srcKey]===source[srcKey];
	        })
	      });
	      // Only change code above this line
	      return arr;
	    }
	    
	    console.log(whatIsInAName([{ first: "Romeo", last: "Montague" }, { first: "Mercutio", last: null }, { first: "Tybalt", last: "Capulet" }], { last: "Capulet" }))
## Spinal Tap Case
Convert a string to spinal case. Spinal case is all-lowercase-words-joined-by-dashes.

	    function spinalCase(str) {
	      // Create a variable for the white space and underscores.
	      var regex = /\s+|_+/g;
	    
	      // Replace low-upper case to low-space-uppercase
	      str = str.replace(/([a-z])([A-Z])/g, "$1 $2");
	    
	      // Replace space and underscore with -
	      return str.replace(regex, "-").toLowerCase();
	    }
	    
	    // test here
	    spinalCase("This Is Spinal Tap");
	    
	    spinalCase('This Is Spinal Tap');

## Pig Latin

> Pig Latin is a way of altering English Words. The rules are as
  > follows:
  > 
  > - If a word begins with a consonant, take the first consonant or consonant cluster, move it to the end of the word, and add "ay" to       it.
  > 
  > - If a word begins with a vowel, just add "way" at the end.

	    function translatePigLatin(str) {
	      let consonantRegex = /^[^aeiou]+/;
	      let myConsonants = str.match(consonantRegex);
	      return myConsonants !== null
	        ? str
	            .replace(consonantRegex, "")
	            .concat(myConsonants)
	            .concat("ay")
	        : str.concat("way");
	    }
	    
	    translatePigLatin("consonant");
## Search and Replace
Perform a search and replace on the sentence using the arguments provided and return the new sentence.

First argument is the sentence to perform the search and replace on.

Second argument is the word that you will be replacing (before).

Third argument is what you will be replacing the second argument with (after).

Note
Preserve the case of the first character in the original word when you are replacing it. For example if you mean to replace the word "Book" with the word "dog", it should be replaced as "Dog"

	    function myReplace(str, before, after) {
	    
	      if(/^[A-Z]/.test(before)){
	        after = after[0].toUpperCase() + after.substring(1);
	      }else{
	        after = after[0].toLowerCase() + after.substring(1);
	      }
	    
	      return str.replace(before,after);
	    }
	    
	    myReplace("A quick brown fox jumped over the lazy dog", "Jumped", "Leaped");
 "Leaped");

## DNA Pairing
The DNA strand is missing the pairing element. Take each character, get its pair, and return the results as a 2d array.

Base pairs are a pair of AT and CG. Match the missing element to the provided character.

Return the provided character as the first element in each array.

For example, for the input GCG, return [["G", "C"], ["C","G"],["G", "C"]]

The character and its pair are paired up in an array, and all the arrays are grouped into one encapsulating array.

	    const pairs = {
	      A:'T',
	      T:'A',
	      C:'G',
	      G:'C'
	    }
	    
	    function pairElement(str) {
	      return str.split('').map(item=>[item,pairs[item]]);
	    }
	    
	    console.log(pairElement("GCG"));

## Missing letters
Find the missing letter in the passed letter range and return it.

If all letters are present in the range, return undefined

	    function fearNotLetter(str) {
	    
	      const arr = str.split('').map(item=>item.charCodeAt(0));
	      for(let i = 0;i<arr.length - 1;i++){
	        if(arr[i]+1 !== arr[i+1]){
	          return String.fromCharCode(arr[i]+1);
	        }
	      }
	      
	    }
	    
	    fearNotLetter("abce");
## Sorted Union
Write a function that takes two or more arrays and returns a new array of unique values in the order of the original provided arrays.

In other words, all values present from all arrays should be included in their original order, but with no duplicates in the final array.

The unique numbers should be sorted by their original order, but the final array should not be sorted in numerical order.

	    function uniteUnique(...arr) {
	      return arr.reduce((acc,innerArr)=>{
	        innerArr.forEach(item=>{
	          if(!acc.includes(item)){
	            acc.push(item);
	          }
	        });
	        return acc;
	      },[]);
	    }
	    
	    console.log(uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]));

## Convert HTML Entities
Convert the characters &, <, >, " (double quote), and ' (apostrophe), in a string to their corresponding HTML entities.

    function convertHTML(str) {
      // Use Object Lookup to declare as many HTML entities as needed.
      const htmlEntities = {
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&apos;"
      };
      //Use map function to return a filtered str with all entities changed automatically.
      return str
        .split("")
        .map(entity => htmlEntities[entity] || entity)
        .join("");
    }
    
    // test here
    convertHTML("Dolce & Gabbana");
## Sum All Odd Fibonacci Numbers
Given a positive integer num, return the sum of all odd Fibonacci numbers that are less than or equal to num.

The first two numbers in the Fibonacci sequence are 1 and 1. Every additional number in the sequence is the sum of the two previous numbers. The first six numbers of the Fibonacci sequence are 1, 1, 2, 3, 5 and 8.

For example, sumFibs(10) should return 10 because all odd Fibonacci numbers less than or equal to 10 are 1, 1, 3, and 5.

	    function sumFibs(num) {
	      let a =1;
	      let b = 1;
	      let sum = a + b;
	      while(a<num){
	        const temp = a;
	        a=b;
	        b=temp+b;
	        if(b<=num)
	         sum +=(b % 2 !==0)? b: 0;
	      }
	      return sum;
	    }
	    
	    console.log(sumFibs(75025));

  
## Sum All Primes

A prime number is a whole number greater than 1 with exactly two divisors: 1 and itself. For example, 2 is a prime number because it is only divisible by 1 and 2. In contrast, 4 is not prime since it is divisible by 1, 2 and 4.
	function sumPrimes(num) {
	  let sum = 0;
	  for(let i=2;i<=num;i++){
	    if(isPrime(i))
	      sum +=i;
	  }
	  return sum;
	}


	function isPrime(n){
	  for(let i=2; i<=Math.sqrt(n);i++){
	    if(n % i === 0){
	      return false;
	    }
	  }
	  return true;
	}

	sumPrimes(10);
## Smallest Common Multiple*
Find the smallest common multiple of the provided parameters that can be evenly divided by both, as well as by all sequential numbers in the range between these parameters.

The range will be an array of two numbers that will not necessarily be in numerical order.

For example, if given 1 and 3, find the smallest common multiple of both 1 and 3 that is also evenly divisible by all numbers between 1 and 3. The answer here would be 6.



	    function smallestCommons(arr) {
	      // Sort array from greater to lowest
	      // This line of code was from Adam Doyle (http://github.com/Adoyle2014)
	      arr.sort(function(a, b) {
	        return b - a;
	      });
	    
	      // Create new array and add all values from greater to smaller from the
	      // original array.
	      var newArr = [];
	      for (var i = arr[0]; i >= arr[1]; i--) {
	        newArr.push(i);
	      }
	    
	      // Variables needed declared outside the loops.
	      var quot = 0;
	      var loop = 1;
	      var n;
	    
	      // Run code while n is not the same as the array length.
	      do {
	        quot = newArr[0] * loop * newArr[1];
	        for (n = 2; n < newArr.length; n++) {
	          if (quot % newArr[n] !== 0) {
	            break;
	          }
	        }
	    
	        loop++;
	      } while (n !== newArr.length);
	    
	      return quot;
	    }
	    
	    // test here
	    smallestCommons([1, 5]);


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODk3MDk2NTQsMTQ2NjI4NzQ5MSwxOT
UxOTcyODEsLTEwNDQzNzIwNzEsMTM0ODU3ODIxNywyMDAwMjE1
ODY1LDE2MTA2MDc3MzEsLTEwOTAyMzgxMTMsLTQ2Nzc5MTI0OC
wtMTM5NjUzNjIzOSwtNTI3Njc3ODQ2LDE0NzU1MTEwMDcsLTE0
MjI4NTMyMjgsLTk4NDc1MjUyOCwzMjczNTIyNzgsNDMyOTUyMz
A4LC0xNjAyNDQyNDAyLDkxNjM3MTQ4OCwxNzkzNjE4MjMyLC03
NzE1MTg4NTBdfQ==
-->