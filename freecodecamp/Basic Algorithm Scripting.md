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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzIwODkyNTYxLDI2MDUxNDY2OSwxMjg2Mz
gzOTA3LDE2Njg2MTIwNDIsLTE3ODc3MTk5NzhdfQ==
-->