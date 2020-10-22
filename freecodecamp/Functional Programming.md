## Learn About Functional Programming

 - Functional programming is a style of programming where solutions are simple, isolated functions, without any side effects outside of the function scope.
 - `INPUT -> PROCESS -> OUTPUT`
 - Functional programming is about:
 - 1) Isolated functions - there is no dependence on the state of the
   program, which includes global variables that are subject to change
   
   2) Pure functions - the same input always gives the same output
   
   3) Functions with limited side effects - any changes, or mutations,
   to the state of the program outside the function are carefully
   controlled

		    // Function that returns a string representing a cup of green tea
		    const prepareTea = () => 'greenTea';
		    
		    /*
		    Given a function (representing the tea type) and number of cups needed, the
		    following function returns an array of strings (each representing a cup of
		    a specific type of tea).
		    */
		    const getTea = (numOfCups) => {
		      const teaCups = [];
		    
		      for(let cups = 1; cups <= numOfCups; cups += 1) {
		        const teaCup = prepareTea();
		        teaCups.push(teaCup);
		      }
		      return teaCups;
		    };
		    
		    // Only change code below this line
		    const tea4TeamFCC = getTea(40);
		    // Only change code above this line
## Understand Functional Programming Terminology

**Callbacks**

> Callbacks are the functions that are slipped or passed into another
> function to decide the invocation of that function. You may have seen
> them passed to other methods, for example in filter, the callback
> function tells JavaScript the criteria for how to filter an array.
 
 **first class functions**
>  Functions that can be assigned to a variable, passed into another
> function, or returned from another function just like any other normal
> value, are called first class functions. In JavaScript, all functions
> are first class functions.
> 
**higher order functions**
> The functions that take a function as an argument, or return a
> function as a return value are called higher order functions.

*Prepare 27 cups of green tea and 13 cups of black tea and store them in tea4GreenTeamFCC and tea4BlackTeamFCC variables, respectively. Note that the getTea function has been modified so it now takes a function as the first argument.*

    // Function that returns a string representing a cup of green tea
    const prepareGreenTea = () => 'greenTea';
    
    // Function that returns a string representing a cup of black tea
    const prepareBlackTea = () => 'blackTea';
    
    /*
    Given a function (representing the tea type) and number of cups needed, the
    following function returns an array of strings (each representing a cup of
    a specific type of tea).
    */
    const getTea = (prepareTea, numOfCups) => {
      const teaCups = [];
    
      for(let cups = 1; cups <= numOfCups; cups += 1) {
        const teaCup = prepareTea();
        teaCups.push(teaCup);
      }
      return teaCups;
    };
    
    // Only change code below this line
    const tea4GreenTeamFCC = getTea(prepareGreenTea,27);
    const tea4BlackTeamFCC = getTea(prepareBlackTea,13);
    // Only change code above this line
    
    console.log(
      tea4GreenTeamFCC,
      tea4BlackTeamFCC
    );
## Refactor Global Variables Out of Functions

> Rewrite the code so the global array bookList is not changed inside
> either function. The add function should add the given bookName to the
> end of the array passed to it and return a new array (list). The
> remove function should remove the given bookName from the array passed
> to it.
> 
> Note: Both functions should return an array, and any new parameters
> should be added before the bookName parameter.

    // The global variable
    var bookList = ["The Hound of the Baskervilles", "On The Electrodynamics of Moving Bodies", "Philosophiæ Naturalis Principia Mathematica", "Disquisitiones Arithmeticae"];
    
    // Change code below this line
    function add (bookList, bookName) {
      return [...bookList, bookName]  
      // Change code above this line
    }
    
    // Change code below this line
    function remove (bookList,bookName) {
    return bookList.filter(book=>book!==bookName);
    }
    
    var newBookList = add(bookList, 'A Brief History of Time');
    var newerBookList = remove(bookList, 'On The Electrodynamics of Moving Bodies');
    var newestBookList = remove(add(bookList, 'A Brief History of Time'), 'On The Electrodynamics of Moving Bodies');
    
    console.log(bookList);
    console.log(newBookList);
## Use the map Method to Extract Data from an Array

> The watchList array holds objects with information on several movies.
> Use map on watchList to assign a new array of objects with only title
> and rating keys to the ratings variable. The code in the editor
> currently uses a for loop to do this, so you should replace the loop
>functionality with your map expression.

    const ratings = watchList.map(item => ({
      title: item["Title"],
      rating: item["imdbRating"]
    }));
    // Another approach
    const ratings = watchList.map(({ Title: title, imdbRating: rating }) => ({title, rating}));
    
## Implement map on a Prototype

> Write your own Array.prototype.myMap(), which should behave exactly
> like Array.prototype.map(). You may use a for loop or the forEach
> method.
var s = [23, 65, 98, 5];

    Array.prototype.myMap = function(callback){
      var newArray = [];
      this.forEach(a => newArray.push(callback(a)));
      return newArray;
    };
    
    var new_s = s.myMap(function(item){
      console.log('called')
      return item * 2;
    });

**Explantion**

 - Here s is an Object which calls the myMap Prototype fucntion.
 - Annonymous function passed as callback.
 - for each element call back has been.
 - Result is stored in the newArray.
 - Finally the new array has been returned.
 - [Refer](https://forum.freecodecamp.org/t/implement-map-on-a-prototype-detailed-description/336272/6) detailed explantion on `this` keyword.
## Use the filter Method to Extract Data from an Array

> The variable watchList holds an array of objects with information on
> several movies. Use a combination of filter and map on watchList to
> assign a new array of objects with only title and rating keys. The new
> array should only include objects where imdbRating is greater than or
> equal to 8.0. Note that the rating values are saved as strings in the
> object and you may need to convert them into numbers to perform
> mathematical operations on them.

    // Only change code below this line
    
    var filteredList;
    filteredList = watchList.filter(movie => movie.imdbRating > 8.0).map(({Title:title,imdbRating: rating })=>({title,rating}));
    // Only change code above this line
    
    console.log(filteredList);
## Implement the filter Method on a Prototype

> Write your own Array.prototype.myFilter(), which should behave exactly
> like Array.prototype.filter(). You may use a for loop or the
> Array.prototype.forEach() method.

	    // The global variable
	    var s = [23, 65, 98, 5];
	    
	    Array.prototype.myFilter = function(callback){
	      // Only change code below this line
	      var newArray = [];
	      this.forEach(item=>{
	        if(callback(item)){
	          newArray.push(item);
	        }
	      })
	      // Only change code above this line
	      return newArray;
	    
	    };
	    
	    var new_s = s.myFilter(function(item){
	      return item % 2 === 1;
	    });
## Return Part of an Array Using the slice Method

 - The slice method returns a copy of certain elements of an array. 
 - It can take two arguments, the first gives the index of where to begin the slice, the second is the index for where to end the slice (and it's non-inclusive). 
 - *If the arguments are not provided*, the default is to start at the beginning of the array through the end, which is an easy way to make a *copy of the entire array*. 
 - The *slice method does not mutate the original array*, but returns a new one.

> Use the slice method in the sliceArray function to return part of the
> anim array given the provided beginSlice and endSlice indices. The
> function should return an array.

	    function sliceArray(anim, beginSlice, endSlice) {
	      // Only change code below this line
	        return anim.slice(beginSlice,endSlice);
	      // Only change code above this line
	    }
	    var inputAnim = ["Cat", "Dog", "Tiger", "Zebra", "Ant"];
	    sliceArray(inputAnim, 1, 3);
## Remove Elements from an Array Using slice Instead of splice
A common pattern while working with arrays is when you want to remove items and keep the rest of the array. JavaScript offers the splice method for this, which takes arguments for the index of where to start removing items, then the number of items to remove. If the second argument is not provided, the default is to remove items through the end. However, the splice method mutates the original array it is called on.

> Rewrite the function nonMutatingSplice by using slice instead of
> splice. It should limit the provided cities array to a length of 3,
> and return a new array with only the first three items.
> 
> Do not mutate the original array provided to the function.

    function nonMutatingSplice(cities) {
      // Only change code below this line
      return cities.slice(0,3);
    
      // Only change code above this line
    }
    var inputCities = ["Chicago", "Delhi", "Islamabad", "London", "Berlin"];
    console.log(nonMutatingSplice(inputCities));
## Combine Two Arrays Using the concat Method
Concatenation means to join items end to end. JavaScript offers the concat method for both strings and arrays that work in the same way. For arrays, the method is called on one, then another array is provided as the argument to concat, which is added to the end of the first array. 

U

> se the concat method in the nonMutatingConcat function to concatenate
> attach to the end of original. The function should return the
> concatenated array.

	    function nonMutatingConcat(original, attach) {
	      // Only change code below this line
	    
	        return original.concat(attach);
	      // Only change code above this line
	    }
	    var first = [1, 2, 3];
	    var second = [4, 5];
	    nonMutatingConcat(first, second);

## Add Elements to the End of an Array Using concat Instead of push

 - Push adds an item to the end of the same array it is called on, which
   mutates that array.
  
 - Concat offers a way to add new items to the end of an array without
   any mutating side effects.

>    Change the nonMutatingPush function so it uses concat to add
> newItem to the end of original instead of push. The function should
> return an array.

	    function nonMutatingPush(original, newItem) {
	      // Only change code below this line
	      return original.concat(newItem);
	      // Only change code above this line
	    }
	    var first = [1, 2, 3];
	    var second = [4, 5];
	    nonMutatingPush(first, second);
## Use the reduce Method to Analyze Data
The reduce method allows for more general forms of array processing, and it's possible to show that both filter and map can be derived as special applications of reduce. The reduce method iterates over each item in an array and returns a single value (i.e. string, number, object, array). This is achieved via a callback function that is called on each iteration.

In addition to the callback function, reduce has an additional parameter which takes an initial value for the accumulator. If this second parameter is not used, then the first iteration is skipped and the second iteration gets passed the first element of the array as the accumulator.

> The variable watchList holds an array of objects with information on
> several movies. Use reduce to find the average IMDB rating of the
> movies directed by Christopher Nolan. Recall from prior challenges how
> to filter data and map over it to pull what you need. You may need to
> create other variables, and return the average rating from getRating
> function. Note that the rating values are saved as strings in the
> object and need to be converted into numbers before they are used in
> any mathematical operations.

    function getRating(watchList){
     var averageRating =
      watchList
        .filter(film => film.Director === "Christopher Nolan")
        .map(film => Number(film.imdbRating))
        // Use reduce to add together their ratings
        .reduce((sumOfRatings, rating) => sumOfRatings + rating) /
      // Divide by the number of Nolan films to get the average rating
      watchList.filter(film => film.Director === "Christopher Nolan").length;
      // Add your code above this line
      return averageRating;
    }
**Another Approach:**

    function getRating(watchList){
      // Add your code below this line
      var count = 0;
      var averageRating = watchList.reduce((sum,movie) =>  {
        if (movie.Director == "Christopher Nolan") {
          count+=1;
          return sum + parseFloat(movie.imdbRating);
        }
        return sum;
      }, 0) / count;
      // Add your code above this line
      return averageRating;
    }
## Use Higher-Order Functions map, filter, or reduce to Solve a Complex Problem

> We have defined a function named squareList. You need to complete the
> code for the squareList function using any combination of map(),
> filter(), and reduce() so that it returns a new array containing only
> the square of only the positive integers (decimal numbers are not
> integers) when an array of real numbers is passed to it. An example of
> an array containing only real numbers is [-3, 4.8, 5, 3, -3.2].
> 
> Note: Your function should not use any kind of for or while loops or
> the forEach() function.

    const squareList = (arr) => {
      // Only change code below this line
      return arr.filter(num => num > 0 
        && num % parseInt(num) === 0).map(num=>Math.pow(num,2));
      // Only change code above this line
    };
    
    const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]);
    console.log(squaredIntegers);

 - num % parseInt(num) === 0 find the given value is decimal or not
## Sort an Array Alphabetically using the sort Method
 - The sort method sorts the elements of an array according to the
   callback function.

   

 - JavaScript's default sorting method is by string Unicode point value,
   which may return unexpected results. Therefore, it is encouraged to
   provide a callback function to specify how to sort the array items.
   
 - When such a callback function, normally called compareFunction, is   
   supplied, the array elements are sorted according to the return value
   of the compareFunction:

    

 - If compareFunction(a,b) returns a value less    than 0 for two
   elements a and b, then a will come before b. 
   
 - If  compareFunction(a,b) returns a value greater than 0 for two
   elements     a and b, then b will come before a. If
   compareFunction(a,b) returns a    value equal to 0 for two elements a
   and b, then a and b will remain      unchanged.

	    function alphabeticalOrder(arr) {
	      // Only change code below this line
	        return arr.sort((a,b)=>a===b? 0: a>b?1:-1);
	    
	      // Only change code above this line
	    }
	    alphabeticalOrder(["a", "d", "c", "a", "z", "g"]);
	    console.log(alphabeticalOrder(["a", "d", "c", "a", "z", "g"]))
## Return a Sorted Array Without Changing the Original Array

> Use the sort method in the nonMutatingSort function to sort the
> elements of an array in ascending order. The function should return a
> new array, and not mutate the globalArray variable.

	    var globalArray = [5, 6, 3, 2, 9];
	    function nonMutatingSort(arr) {
	      // Only change code below this line
	    
	        return [...globalArray].sort();
	        //or 
	        //return [].concat(arr).sort();
	      // Only change code above this line
	    }
	    console.log(nonMutatingSort(globalArray));

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzOTY1MzYyMzksLTUyNzY3Nzg0NiwxND
c1NTExMDA3LC0xNDIyODUzMjI4LC05ODQ3NTI1MjgsMzI3MzUy
Mjc4LDQzMjk1MjMwOCwtMTYwMjQ0MjQwMiw5MTYzNzE0ODgsMT
c5MzYxODIzMiwtNzcxNTE4ODUwLDQwNzQwNTcxNywtMTg4ODQ3
NTMxMiwtMTE0MDM0NzI5MF19
-->