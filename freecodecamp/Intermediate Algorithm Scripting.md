## Sum All Numbers in a Range

> We'll pass you an array of two numbers. Return the sum of those two
> numbers plus the sum of all the numbers between them. The lowest
> number will not always come first.
> 
> For example, sumAll([4,1]) should return 10 because sum of all the
> numbers between 1 and 4 (both inclusive) is 10.

**Solution 1**

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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcxMTY3MzQ3MV19
-->