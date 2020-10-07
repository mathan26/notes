## Use an Array to Store a Collection of Data

 - All arrays have a length property, which as shown above, can be very easily accessed with the syntax `Array.length`.
 - Array also contains JavaScript objects.
 ## Access an Array's Contents Using Bracket Notation
 

    let ourVariable = ourArray[0];
    
   ## Add Items to an Array with push() and unshift()
   

 - arrays are mutable
 - programmatically modify an array: `Array.push(`) and `Array.unshift()`.

> We have defined a function, mixedNumbers, which we are passing an array as an argument. Modify the function by using push() and unshift() to add 'I', 2, 'three' to the beginning of the array and 7, 'VIII', 9 to the end so that the returned array contains representations of the numbers 1-9 in order.

   

     function mixedNumbers(arr) {
      // Only change code below this line
        arr.unshift('I', 2, 'three');
        arr.push(7, 'VIII', 9);
      // Only change code above this line
      return arr;
    }
    
    console.log(mixedNumbers(['IV', 5, 'six']));

    Output: [ 'I', 2, 'three', 'IV', 5, 'six', 7, 'VIII', 9 ]
   
   ## Remove Items from an Array with pop() and shift()
   

 - The key difference between `pop()` and `shift()` and their cousins `push()` and `unshift()`.

> We have defined a function, popShift, which takes an array as an
> argument and returns a new array. Modify the function, using pop() and
> shift(), to remove the first and last elements of the argument array,
> and assign the removed elements to their corresponding variables, so
> that the returned array contains their values.

    function popShift(arr) {
      let popped = arr.pop(); // Change this line
      let shifted = arr.shift(); // Change this line
      return [shifted, popped];
    }
    
    console.log(popShift(['challenge', 'is', 'not', 'complete']));
    
       Output:  [ 'challenge', 'complete' ]

## Remove Items Using splice()

 - remove any number of consecutive elements from anywhere in an array.
 - splice() can take up to 3 parameters
 - splice() not only modifies the array it's being called on, but it also returns a new array containing the value of the removed elements:
 

> We've initialized an array arr. Use splice() to remove elements from
> arr, so that it only contains elements that sum to the value of 10.

    const arr = [2, 4, 5, 1, 7, 5, 2, 1];
    // only change code below this line
    arr.splice(1, 4);
    // only change code above this line
    console.log(arr); // [ 2, 5, 2, 1 ]
## Add Items Using splice()
    

 - you can use the third parameter, comprised of one or more element(s), to add to the array. 

> We have defined a function, htmlColorNames, which takes an array of HTML colors as an argument. Modify the function using splice() to remove the first two elements of the array and add 'DarkSalmon' and 'BlanchedAlmond' in their respective places.


    function htmlColorNames(arr) {
      // Only change code below this line
         arr.splice(0,2,'DarkSalmon','BlanchedAlmond');
      // Only change code above this line
      return arr;
    }
    
    console.log(htmlColorNames(['DarkGoldenRod', 'WhiteSmoke', 'LavenderBlush', 'PaleTurquoise', 'FireBrick']));
   

     [ 'DarkSalmon',
      'BlanchedAlmond',
      'LavenderBlush',
      'PaleTurquoise',
      'FireBrick' ]

## Copy Array Items Using slice()

 - Rather than modifying an array, slice() copies or extracts a given number of elements to a new array, leaving the array it is called upon untouched.
 - the first is the index at which to begin extraction, and the second is the index at which to stop extraction 

    

>  We have defined a function, forecast, that takes an array as an
> argument. Modify the function using slice() to extract information
> from the argument array and return a new array that contains the
> elements 'warm' and 'sunny'.

    function forecast(arr) {
      // Only change code below this line
      let result = arr.slice(2,4);
      return result;
    }
    
    // Only change code above this line
    console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));
    //[ 'warm', 'sunny' ]
## Copy an Array with the Spread Operator

 - ES6's new spread operator allows us to easily copy all of an array's elements, in order, with a simple and highly readable syntax. 
 - The spread syntax simply looks like this: `...`
 
 

> We have defined a function, copyMachine which takes arr (an array) and num (a number) as arguments. The function is supposed to return a new array made up of num copies of arr. We have done most of the work for you, but it doesn't work quite right yet. Modify the function using spread syntax so that it works correctly (hint: another method we have already covered might come in handy here!).

    function copyMachine(arr, num) {
      let newArr = [];
      while (num >= 1) {
        // Only change code below this line
        let copyArr = [...arr];
          newArr.push(copyArr);
        // Only change code above this line
        num--;
      }
      return newArr;
    }
    
    console.log(copyMachine([true, false, true], 2));
    // [ [ true, false, true ], [ true, false, true ] ]
## Combine Arrays with the Spread Operator

 - Another huge advantage of the spread operator, is the ability to combine arrays, or to insert all the elements of one array into another, at any index.

> We have defined a function spreadOut that returns the variable
> sentence. Modify the function using the spread operator so that it
> returns the array ['learning', 'to', 'code', 'is', 'fun'].

     function spreadOut() {
      let fragment = ['to', 'code'];
      let sentence=['learning',...fragment, 'is', 'fun']; // Change this line
      return sentence;
    }
    
    console.log(spreadOut());
    [ 'learning', 'to', 'code', 'is', 'fun' ]
## Check For The Presence of an Element With indexOf()

 - indexOf() can be incredibly useful for quickly checking for the presence of an element on an array. 

> We have defined a function, quickCheck, that takes an array and an
> element as arguments. Modify the function using indexOf() so that it
> returns true if the passed element exists on the array, and false if
> it does not.

    function quickCheck(arr, elem) {
      // Only change code below this line
        return arr.indexOf(elem)!==-1;
      // Only change code above this line
    }
    
    console.log(quickCheck(['squash', 'onions', 'shallots'], 'shallots'));
    //true
## Iterate Through All an Array's Items Using For Loops

> We have defined a function, filteredArray, which takes arr, a nested array, and elem as arguments, and returns a new array. elem represents an element that may or may not be present on one or more of the arrays nested within arr. Modify the function, using a for loop, to return a filtered version of the passed array such that any array nested within arr containing elem has been removed.

    function filteredArray(arr, elem) {
      let newArr = [];
      // Only change code below this line
      for(let i=0;i<arr.length;i++){
          if(arr[i].indexOf(elem) == -1){
            newArr.push(arr[i]);
          }
      }
      // Only change code above this line
      return newArr;
    }
    
    console.log(filteredArray([[3, 2, 3], [1, 6, 3], [3, 13, 26], [19, 3, 9]], 3));
## Create complex multi-dimensional arrays

> We have defined a variable, myNestedArray, set equal to an array. Modify myNestedArray, using any combination of strings, numbers, and booleans for data elements, so that it has exactly five levels of depth (remember, the outer-most array is level 1). Somewhere on the third level, include the string 'deep', on the fourth level, include the string 'deeper', and on the fifth level, include the string 'deepest'.

    let myNestedArray = [
      // Only change code below this line
      ['unshift', false, 1, 2, 3, 'complex', 'nested'],
      ['loop', 'shift', 6, 7, 1000, 'method'],
      ['concat', false, true, 'spread', 'array'],
      ['mutate', 1327.98, 'splice', 'slice', 'push'],
      ['iterate', 1.3849, 7, '8.4876', 'arbitrary', 'depth'],
      [
        ['deep']
      ], 
      [
         [ 
            ['deeper']
         ]
      ],
       [
         [ 
            [
              ['deepest']
            ]
         ]
      ]
      // Only change code above this line
    ];
## Add Key-Value Pairs to JavaScript Objects

 - At their most basic, objects are just collections of key-value pairs.
 

> A foods object has been created with three entries. Using the syntax of your choice, add three more entries to it: bananas with a value of 13, grapes with a value of 35, and strawberries with a value of 27.

    let foods = {
      apples: 25,
      oranges: 32,
      plums: 28
    };
    
    // Only change code below this line
      foods['bananas']=13;
      foods['grapes'] = 35;
      foods['strawberries'] = 27;
    // Only change code above this line
    
    console.log(foods);
## Modify an Object Nested Within an Object

    let userActivity = {
      id: 23894201352,
      date: 'January 1, 2017',
      data: {
        totalUsers: 51,
        online: 42
      }
    };
    
    // Only change code below this line
    userActivity['data']['online']=45;
    // Only change code above this line
    
    console.log(userActivity);
 ## HeadingAccess Property Names with Bracket Notation
 

 - Bracket notation is very useful because sometimes object properties are not known before runtime or we need to access them in a more dynamic way.

> We've defined a function, checkInventory, which receives a scanned item as an argument. Return the current value of the scannedItem key in the foods object. You can assume that only valid keys will be provided as an argument to checkInventory.


    let foods = {
      apples: 25,
      oranges: 32,
      plums: 28,
      bananas: 13,
      grapes: 35,
      strawberries: 27
    };
    
    function checkInventory(scannedItem) {
      // Only change code below this line
          return foods[scannedItem];
      // Only change code above this line
    }
    
    console.log(checkInventory("apples"));

## Use the delete Keyword to Remove Object Properties

> Blockquote

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTA1OTAwNjU3LC0zNDQzNjY0NTUsMTA1NT
gxNzk5MiwxNzUxNTA5NzQyLDE0NzEwNTQyNDZdfQ==
-->