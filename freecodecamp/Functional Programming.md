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
 - The **slice method does not mutate the original array**, but returns a new one.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNDE1MzgxMDEsNDMyOTUyMzA4LC0xNj
AyNDQyNDAyLDkxNjM3MTQ4OCwxNzkzNjE4MjMyLC03NzE1MTg4
NTAsNDA3NDA1NzE3LC0xODg4NDc1MzEyLC0xMTQwMzQ3MjkwXX
0=
-->