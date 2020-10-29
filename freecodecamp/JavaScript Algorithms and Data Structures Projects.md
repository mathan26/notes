## Palindrome Checker
Return true if the given string is a palindrome. Otherwise, return false.

A palindrome is a word or sentence that's spelled the same way both forward and backward, ignoring punctuation, case, and spacing.

Note
You'll need to remove all non-alphanumeric characters (punctuation, spaces and symbols) and turn everything into the same case (lower or upper case) in order to check for palindromes.

We'll pass strings with varying formats, such as "racecar", "RaceCar", and "race CAR" among others.

We'll also pass strings with special symbols, such as "2A3*3a2", "2A3 3a2", and "2_A3*3#A2".


	    function palindrome(str) {
	      const s = str.replace(/[_\W]/g,'');
	      return isPalindrome(s);
	    }
	    
	    
	    function isPalindrome(str){
	      return str.toLowerCase() === str.toLowerCase()
	              .split('').reverse().join('');
	    }
	    palindrome("0_0 (: /-\ :) 0-0");
## Caesars Cipher
One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function which takes a ROT13 encoded string as input and returns a decoded string.

All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.

	    function rot13(str) {
	      return str.replace(/[A-Z]/g,letter=>{
	        let asciiVal  =letter.charCodeAt(0) + 13;
	        if(asciiVal > 90){
	          asciiVal = (asciiVal % 90) + 64;
	        }
	        return String.fromCharCode(asciiVal);
	      })
	    }
	    
	    console.log(rot13("SERR PBQR PNZC"));
## Telephone Number Validator
Return true if the passed string looks like a valid US phone number.

The user may fill out the form field any way they choose as long as it has the format of a valid US number. The following are examples of valid formats for US numbers (refer to the tests below for other variants):

555-555-5555
(555)555-5555
(555) 555-5555
555 555 5555
5555555555
1 555 555 5555
For this challenge you will be presented with a string such as 800-692-7753 or 8oo-six427676;laskdjf. Your job is to validate or reject the US phone number based on any combination of the formats provided above. The area code is required. If the country code is provided, you must confirm that the country code is 1. Return true if the string is a valid US phone number; otherwise return false.

	    function telephoneCheck(str) {
	      var regex = /^(1\s?)?(\(\d{3}\)|\d{3})[\s\-]?\d{3}[\s\-]?\d{4}$/;
	      return regex.test(str);
	    }
	    
	    telephoneCheck("555-555-5555");
## Roman Numeral Converter

Convert the given number into a roman numeral.

All roman numerals answers should be provided in upper-case.

    function convertToRoman(num) {
    const converted = {
        M  :1000,
        CM : 900,
        D  : 500,
        CD : 400,
        C  : 100,
        XC : 90,
        L  : 50,
        XL : 40,
        X  : 10,
        IX : 9,
        V  : 5,
        IV : 4,
        I  : 1
    }
    let final='';
    for(let roman in converted){
        while(num>=converted[roman]){
            num -=converted[roman];
            final +=roman;
    
        }
    }
     return final;
    }
    
    convertToRoman(36);
## Cash Register
Design a cash register drawer function checkCashRegister() that accepts purchase price as the first argument (price), payment as the second argument (cash), and cash-in-drawer (cid) as the third argument.

cid is a 2D array listing available currency.

The checkCashRegister() function should always return an object with a status key and a change key.

Return {status: "INSUFFICIENT_FUNDS", change: []} if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return {status: "CLOSED", change: [...]} with cash-in-drawer as the value for the key change if it is equal to the change due.

Otherwise, return {status: "OPEN", change: [...]}, with the change due in coins and bills, sorted in highest to lowest order, as the value of the change key.

Currency Unit	Amount
Penny	$0.01 (PENNY)
Nickel	$0.05 (NICKEL)
Dime	$0.1 (DIME)
Quarter	$0.25 (QUARTER)
Dollar	$1 (ONE)
Five Dollars	$5 (FIVE)
Ten Dollars	$10 (TEN)
Twenty Dollars	$20 (TWENTY)
One-hundred Dollars	$100 (ONE HUNDRED)
See below for an example of a cash-in-drawer array:

[
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.1],
  ["QUARTER", 4.25],
  ["ONE", 90],
  ["FIVE", 55],
  ["TEN", 20],
  ["TWENTY", 60],
  ["ONE HUNDRED", 100]
]

    // Create an array of objects which hold the denominations and their values
    var denom = [
      { name: "ONE HUNDRED", val: 100.0 },
      { name: "TWENTY", val: 20.0 },
      { name: "TEN", val: 10.0 },
      { name: "FIVE", val: 5.0 },
      { name: "ONE", val: 1.0 },
      { name: "QUARTER", val: 0.25 },
      { name: "DIME", val: 0.1 },
      { name: "NICKEL", val: 0.05 },
      { name: "PENNY", val: 0.01 }
    ];
    
    function checkCashRegister(price, cash, cid) {
      var output = { status: null, change: [] };
      var change = cash - price;
    
      // Transform CID array into drawer object
      var register = cid.reduce(
        function(acc, curr) {
          acc.total += curr[1];
          acc[curr[0]] = curr[1];
          return acc;
        },
        { total: 0 }
      );
    
      // Handle exact change
      if (register.total === change) {
        output.status = "CLOSED";
        output.change = cid;
        return output;
      }
    
      // Handle obvious insufficient funds
      if (register.total < change) {
        output.status = "INSUFFICIENT_FUNDS";
        return output;
      }
    
      // Loop through the denomination array
      var change_arr = denom.reduce(function(acc, curr) {
        var value = 0;
        // While there is still money of this type in the drawer
        // And while the denomination is larger than the change remaining
        while (register[curr.name] > 0 && change >= curr.val) {
          change -= curr.val;
          register[curr.name] -= curr.val;
          value += curr.val;
    
          // Round change to the nearest hundreth deals with precision errors
          change = Math.round(change * 100) / 100;
        }
        // Add this denomination to the output only if any was used.
        if (value > 0) {
          acc.push([curr.name, value]);
        }
        return acc; // Return the current change_arr
      }, []); // Initial value of empty array for reduce
    
      // If there are no elements in change_arr or we have leftover change, return
      // the string "Insufficient Funds"
      if (change_arr.length < 1 || change > 0) {
        output.status = "INSUFFICIENT_FUNDS";
        return output;
      }
    
      // Here is your change, ma'am.
      output.status = "OPEN";
      output.change = change_arr;
      return output;
    }
    
    // test here
    checkCashRegister(19.5, 20.0, [
      ["PENNY", 1.01],
      ["NICKEL", 2.05],
      ["DIME", 3.1],
      ["QUARTER", 4.25],
      ["ONE", 90.0],
      ["FIVE", 55.0],
      ["TEN", 20.0],
      ["TWENTY", 60.0],
      ["ONE HUNDRED", 100.0]
    ]);

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI2OTc5NTY4OF19
-->