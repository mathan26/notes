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

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI4NjM4MzkwNywxNjY4NjEyMDQyLC0xNz
g3NzE5OTc4XX0=
-->