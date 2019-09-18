# NATALIA VOLKOVA
# Junior JavaScript Developer | Entry-Level Front-end Developer | IT Analyst
## Contact Info:
* Tel.: +7(950)449-43-66 (Russia)
* Tel.: +48(732)201-880
* email: Natalia.Volkofff@gmail.com
* skype: live:natalia.volkofff
## Summary
>I am a **self-taught Front-End Developer** with Bachelor’s Degree in *Economics*, Master's Degree in *Public Administration*, prior experience in *Financial Analysis, Mathematics, and Tutorship*. I’ve always found coding intuitive and have pushed myself to learn the most effective way to achieve a result. 
>
>I’m a fast learner and can quickly integrate into a team so I can provide value to the company and the customers. 

## Skills
* Microsoft Office: 
    * Word, 
    * Excel,
    * PowerPoint,
    * Outlook,
    * Access, 
    * VBA) 
* Excel: 
    * VBA, 
    * Pivot Tables, 
    * Dashboards and Reports, 
    * look-ups,
    * index & match formulas
* Operating systems: 
    * Windows, 
    * Linux (basics) 
* Computer languages: 
    * C (basics), 
    * Python (basics),
    * JavaScript (including ES6, Regular Expressions, Debugging)
* Front-end libraries: 
    * Bootstrap, 
    * jQuery, 
    * Sass, 
    * React, 
    * Redux
* Web-programming languages: 
    * HTML (HTML5), 
    * CSS (CSS3, Flexbox, Grid)
* Photoshop
* Econometrics and Statistics software: 
    * SPSS, 
    * STATISTICA,
    * Smart-PLS,
    * EViews

## Code Examples
### Task: No Repeats Please (freeCodeCamp)
Return the number of total permutations of the provided string that don't have repeated consecutive letters. Assume that all characters in the provided string are each unique.
For example, `aab` should return 2 because it has 6 total permutations (`aab`, `aab`, `aba`, `aba`, `baa`, `baa`), but only 2 of them (`aba` and `aba`) don't have the same letter (in this case a) repeating.

```javascript
function permAlone(str) {
    if (str.length === 1) return 1; //if there's only 1 letter in a string
    let repeated = [];
    let strArr = str.split('');
    strArr.sort((a,b) => a > b ? 1 : -1);
    repeated = strArr.join('').match(/(.)\1+/ig); //all repeated substrings
    if (repeated[0] === str) return 0; //if all letters are repeated
    let totalN = str.length; //total number of letters in the string
    let total = factorial(totalN); // total permutations
    let unique = totalN; // number of unique chars
    let invalid = 0; //number of permutations which have the same letter repeating
    let overlap = 0; //if we have more than one repeated character
    //iterate through each repetitions:
    for (let i = 0; i < repeated.length; i++) {
        let repeatedN = repeated[i].length; //number of repeated letters in substrings
        unique -= (repeatedN - 1);
        for (let j = 2; j <= repeatedN; j++) {
            invalid += factorial(totalN - j + 1) * factorial(j);
        }
    }
    if (repeated.length > 1) {
        overlap = factorial(unique);
        for (let i = 0; i < repeated.length; i++) {
        overlap *= factorial(repeated[i].length);
        }
    }
    return total - invalid + overlap;
}
// a handle function
const factorial = (n) => {
    if (n === 1) return 1;
    else return n * factorial(n - 1);
}

// Test
console.log(permAlone("aab")); // should return 2.
console.log(permAlone("aaa")); // should return 0.
console.log(permAlone("aabb")); // should return 8.
console.log(permAlone("abcdefa")); // should return 3600.
console.log(permAlone("abfdefa")); // should return 2640.
console.log(permAlone("zzzzzzzz")); // should return 0.
console.log(permAlone("a")); // should return 1.
console.log(permAlone("aaab")); // should return 0.
console.log(permAlone("aaabb")); // should return 12.
```

### Task: Bubble Sort (freeCodeCamp)
The bubble sort method starts at the beginning of an unsorted array and 'bubbles up' unsorted values towards the end, iterating through the array until it is completely sorted. It does this by comparing adjacent items and swapping them if they are out of order. The method continues looping through the array until no swaps occur at which point the array is sorted.
This method requires multiple iterations through the array and for average and worst cases has quadratic time complexity. While simple, it is usually impractical in most situations.
Instructions: Write a function bubbleSort which takes an array of integers as input and returns an array of these integers in sorted order from least to greatest.

```javascript 
function bubbleSort(array) {
    var swapped = true;
    let length = array.length; // to save some time
    while (swapped) { // keep doing unless no elements can be swapped anymore
        swapped = false;
        for (let i = 1; i < length; i++) {
            if (array[i] < array[i-1]) {
                swap(array, i-1, i);
                swapped = true;
            }
        }
    }
    return array;
}

// handle function for swapping
const swap = (arr, i1, i2) => {
    let temp = arr[i1];
    arr[i1] = arr[i2];
    arr[i2] = temp;
}

// test array:
console.log(bubbleSort([1, 4, 2, 8, 345, 123, 43, 32, 5643, 63, 123, 43, 2, 55, 1, 234, 92]));
```

### Task: Selection Sort (freeCodeCamp)
Selection sort works by selecting the minimum value in a list and swapping it with the first value in the list. It then starts at the second position, selects the smallest value in the remaining list, and swaps it with the second element. It continues iterating through the list and swapping elements until it reaches the end of the list. Now the list is sorted. Selection sort has quadratic time complexity in all cases.
Instructions: Write a function selectionSort which takes an array of integers as input and returns an array of these integers in sorted order from least to greatest.

```javascript
function selectionSort(array) {
    let length = array.length;
    for (let i = 0; i < length - 1; i++) { // we don't need to swap the last element
        let min = Math.min.apply(null, array.slice(i + 1));
        if (array[i] > min) {
            swap(array, i, array.slice(i+1).indexOf(min) + i + 1);
        }
    }
    return array;
}

// handle function for swapping
const swap = (arr, i1, i2) => {
    let temp = arr[i1];
    arr[i1] = arr[i2];
    arr[i2] = temp;
    return arr;
}
// test array:
var array = [1, 4, 2, 8, 345, 123, 43, 32, 5643, 63, 123, 43, 2, 55, 1, 234, 92];
console.log(selectionSort(array));
```

### Task: Insertion Sort (freeCodeCamp)
This method works by building up a sorted array at the beginning of the list. It begins the sorted array with the first element. Then it inspects the next element and swaps it backwards into the sorted array until it is in sorted position. It continues iterating through the list and swapping new items backwards into the sorted portion until it reaches the end. This algorithm has quadratic time complexity in the average and worst cases.
Instructions: Write a function insertionSort which takes an array of integers as input and returns an array of these integers in sorted order from least to greatest.

```javascript
function insertionSort(array) {
    let length = array.length;
    for (let i = 1; i < length; i++) {
        for (let j = 0; j < i; j++) {
            if (array[i] < array[j]) {
                array = insert(array, i, j);
            }
        }
    }
    return array;
}
// handle function for inserting
const insert = (arr, i1, i2) => { // insert arr[i1] before arr[i2]
    return arr.slice(0, i2).concat(arr[i1]).concat(arr.slice(i2, i1)).concat(arr.slice(i1 + 1));
}

// test array:
var array = [1, 4, 2, 8, 345, 123, 43, 32, 5643, 63, 123, 43, 2, 55, 1, 234, 92];
console.log(insertionSort(array));
```
## Experience (IT related)
* [JavaScript Clock](https://github.com/unikvozm/Projects/tree/master/JS_clock)
* [JavaScript Palindrome Checker (HTML, CSS, JavaScript)](https://github.com/unikvozm/Projects/tree/master/Palindrome_checker)
* [JavaScript Caesar Cipher (HTML, CSS, JavaScript)](https://github.com/unikvozm/Projects/tree/master/Caesar_cipher)
* [JavaScript Roman Numeral Converter (HTML, CSS, JavaScript)](https://github.com/unikvozm/Projects/tree/master/roman-numerals-converter)
* [JavaScript Cash Register (HTML, CSS, JavaScript)](https://github.com/unikvozm/Projects/tree/master/cash-register)
* [JavaScript Calculator (HTML, CSS, JavaScript)](https://github.com/unikvozm/Projects/tree/master/Pure_JS_calculator) 
* [Image Changing](https://github.com/unikvozm/Projects/tree/master/image_changing)
* [Drum Kit](https://github.com/unikvozm/Projects/tree/master/drum_kit)
* Social Media Ape (Node.js, JavaScript, Firebase, Postman, Express, busboy, React, Redux, Material-UI, …) – Pursuing 

## Experience (no-IT related)

Dates | Position | Company | Location
------|----------|---------|---------
Sept 2010 – Present | Tutor in Maths, Economics, Econometrics, Finance and Related Subjects | SELF-EMPLOYED | PERM (RUSSIA) + ONLINE (STUDENTS FROM RUSSIA + THE USA)
Apr 2016 – Nov 2018 | Economist | YOU-RIGHT CONSULTING, LLC | PERM, RUSSIA
Mar 2011 – Nov 2018 | Tutor in Maths, Economics, and Financial Management | PROFI.RU | RUSSIA
Oct 2014 – Mar 2016 | Consultant | ONLINE-SCHOOL UMNICHKA | RUSSIA (online) 
Oct 2010 – Dec 2013 | Economist | TEKHSTROYINVEST, LLC | PERM, RUSSIA
Jan 2011 – Jul 2011 | Professor Assistant | NATIONAL RESEARCH UNIVERSITY – Higher School of Economics | PERM, RUSSIA
Jul 2010 – Oct 2010 | Credit Specialist | URALSIB BANK, LLC | PERM, RUSSIA

> Note: sometimes I worked for 3-4 organizations at the same time.

## Education
* Master’s Degree in Public Administration, National Research University – Higher School of Economics, Perm, Russia, 2012
* Bachelor’s Degree in Economics, National Research University – Higher School of Economics, Perm, Russia, 2010
* Front End Libraries Certification, Quincy Larson on freeCodeCamp, Pursuing
* Rolling Scope School - Pursuing
* [Introduction to HTML, Codecademy, 2019](https://www.codecademy.com/profiles/unikvozm)
* [Learn CSS, Codecademy, 2019](https://www.codecademy.com/profiles/unikvozm)
* [Responsive Web Design, Quincy Larson on freeCodeCamp, 2019](https://www.freecodecamp.org/certification/unikvozm/responsive-web-design)
* [JavaScript Algorithms and Data Structures, Quincy Larson on freeCodeCamp, 2019](https://www.freecodecamp.org/certification/unikvozm/javascript-algorithms-and-data-structures)
* [JavaScript Web Programming Language – A Smarter Way to Learn, Mark Myers, 2019](http://www.asmarterwaytolearn.com/javascript-certificate-of-completion-natalia-volkova.html)
* Excel Macros & VBA Course, Excel Developer Certification Professional Excel Certification, IACT & eLearning, 2019
* Excel Reporting & Dashboards Course, IACT and eLearning, 2019
* Excel Analyzing Data Course - Excel Specialist Certification / Excel Analyzing Data, IACT and eLearning, 2019
* Excel -Top Tips Course - Certificate of Completion / Excel – Top Tips, IACT and eLearning, 2019
* [Google IT Support Professional Certificate, Google on Coursera, 2018](https://www.coursera.org/account/accomplishments/professional-cert/certificate/SXWJBK6BAHDY)
* [IT Security: Defense against the digital dark arts, Google on Coursera, 2018](https://www.coursera.org/account/accomplishments/certificate/GQG9VV6NY8Y3)
* [System Administration and IT Infrastructure Services, Google on Coursera, 2018](https://www.coursera.org/account/accomplishments/certificate/QSPYBTHP6WT2)
* [Operating Systems and You: Becoming a Power User, Google on Coursera, 2018](https://www.coursera.org/account/accomplishments/certificate/KJQEEFYXVTEM)
* [The Bits and Bytes of Computer Networking, Google on Coursera, 2018](https://www.coursera.org/account/accomplishments/certificate/4WEPZYQ6PVP3)
* [Technical Support Fundamentals, Google on Coursera, 2018](https://www.coursera.org/account/accomplishments/certificate/7C6YDKPY8JMG)
