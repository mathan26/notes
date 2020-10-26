



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

## Drop it
Given the array arr, iterate through and remove each element starting from the first element (the 0 index) until the function func returns true when the iterated element is passed through it.

Then return the rest of the array once the condition is satisfied, otherwise, arr should be returned as an empty array.

	    function dropElements(arr, func) {
	      const index = arr.findIndex(func);
	      
	      return index=== -1 ?[]:arr.slice(index);
	    }
	    
	    dropElements([1, 2, 3], function(n) {return n < 3; });

## Binary Agents
Return an English translated sentence of the passed binary string.

The binary string will be space separated.

	    function binaryAgent(str) {
	    
	      return str.split(' ').map(item=> String.fromCharCode(parseInt(item,2))).join('');
	    }
	    
	    binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111");
## Everything Be True
Check if the predicate (second argument) is truthy on all elements of a collection (first argument).

In other words, you are given an array collection of objects. The predicate pre will be an object property and you need to return true if its value is truthy. Otherwise, return false.

In JavaScript, truthy values are values that translate to true when evaluated in a Boolean context.

Remember, you can access object properties through either dot notation or [] notation.

	function truthCheck(collection, pre) {
		  return collection.every(item=>{
		    console.log(item.hasOwnProperty(pre),item[pre]);
		    if(!item.hasOwnProperty(pre) || !item[pre]){
		      console.log('here')
		      return false;
		    }else{
		      return true;
		    }
		  });
		}
		console.clear();
		console.log(truthCheck([{"user": "Tinky-Winky", "sex": "male"}, {"user": "Dipsy"}, {"user": "Laa-Laa", "sex": "female"}, {"user": "Po", "sex": "female"}], "sex"))


## Arguments Optional
Create a function that sums two arguments together. If only one argument is provided, then return a function that expects one argument and returns the sum.

For example, addTogether(2, 3) should return 5, and addTogether(2) should return a function.

Calling this returned function with a single argument will then return the sum:

var sumTwoAnd = addTogether(2);

sumTwoAnd(3) returns 5.

If either argument isn't a valid number, return undefined.

	    function addTogether(first, second) {
	      if (typeof first !== "number") {
	        return undefined;
	      }
	      const sum = second =>
	        typeof second === "number" ? first + second : undefined;
	      return typeof second === "undefined" ? second => sum(second) : sum(second);
	    }
	    
	    console.log(addTogether(5));
## Steamroller
latten a nested array. You must account for varying levels of nesting.

    function steamrollArray(arr) {
      let flat = [].concat(...arr);
      console.log(flat)
      return flat.some(Array.isArray) ? steamrollArray(flat) : flat;
    }
    
    steamrollArray([1, [2], [3, [[4]]]]);
## Make a Person
Fill in the object constructor with the following methods below:

    getFirstName()
    getLastName()
    getFullName()
    setFirstName(first)
    setLastName(last)
    setFullName(firstAndLast)

Run the tests to see the expected output for each method. The methods that take an argument must accept only one argument and it has to be a string. These methods must be the only available means of interacting with the object.

        var Person = function(firstAndLast) {
      var fullName = firstAndLast;
    
      this.getFirstName = function() {
        return fullName.split(" ")[0];
      };
    
      this.getLastName = function() {
        return fullName.split(" ")[1];
      };
    
      this.getFullName = function() {
        return fullName;
      };
    
      this.setFirstName = function(name) {
        fullName = name + " " + fullName.split(" ")[1];
      };
    
      this.setLastName = function(name) {
        fullName = fullName.split(" ")[0] + " " + name;
      };
    
      this.setFullName = function(name) {
        fullName = name;
      };
    };
    
    var bob = new Person("Bob Ross");
    bob.getFullName();



## Map the Debris
Return a new array that transforms the elements' average altitude into their orbital periods (in seconds).

The array will contain objects in the format {name: 'name', avgAlt: avgAlt}.

You can read about orbital periods on Wikipedia.

The values should be rounded to the nearest whole number. The body being orbited is Earth.

The radius of the earth is 6367.4447 kilometers, and the GM value of earth is 398600.4418 km3s-2.

    function orbitalPeriod(arr) {
      var GM = 398600.4418;
      var earthRadius = 6367.4447;
      var newArr = [];
    
      //Looping through each key in arr object
      for (var elem in arr) {
        //Rounding off the orbital period value
        var orbitalPer = Math.round(
          2 * Math.PI * Math.sqrt(Math.pow(arr[elem].avgAlt + earthRadius, 3) / GM)
        );
        //Adding new object with orbitalPeriod property
        newArr.push({name: arr[elem].name, orbitalPeriod: orbitalPer});
      }
    
      return newArr;
    }
    
    
    orbitalPeriod([{name : "sputnik", avgAlt : 35873.5553}]);

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNTE5NzU3OSwtMTU4NTgyMjYwLC0xMD
Q0MzcyMDcxLC03MTE2NzM0NzFdfQ==
-->