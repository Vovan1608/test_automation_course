Task 1

On a Home page, there are a series of images. Write a script that:

    1. Iterates through all the images on the page.
    2. Logs to the console those images that have a height greater than 300 pixels.
    3. After analyzing all images, displays in the console the total number of images that meet the condition.

```javascript
const imgs = Array.from(document.getElementsByTagName("img"));
const imgsHeightGreater300 = imgs.filter((img) => img.clientHeight > 300);
imgsHeightGreater300.forEach((img) => console.log(img));
console.log(imgsHeightGreater300.length);
```

Task 2

Display the number of unique colors used in the elements on the page.

```javascript

```

Task 3

Find all button elements present on a specified web page and output the cumulative quantity of these buttons.

```javascript
console.log(document.getElementsByTagName("button").length);
```

Task 4

Find and determine the types of all input fields (input) on a web page.

```javascript
const inputsType = Array.from(
  document.getElementsByTagName("input"),
  ({ type }) => {
    return type;
  }
);
console.log(inputsType);
```

Task 5

Utilizing CSS selectors in conjunction with JavaScript, identify all the social media button elements present on a specified web page and determine their respective destination URLs.

```javascript
const socialMediaButtonElements = Array.from(
  document.querySelectorAll(".footer_social-link"),
  ({ baseURI }) => {
    return baseURI;
  }
);
console.log(socialMediaButtonElements);
```

Task 6
Log into your profile at https://www.greencity.social/#/profile, there is a calendar that displays the week, with navigation buttons (previous/next) and the days of the week.

1. Determine the current day: Locate the day that has the class current-number and display its value. (Expected result, for example, "Current day: 20 September 2023").

```javascript
const month = [
  "January",
  "February",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "September",
  "October",
  "November",
  "December",
];

const currentDay = document.getElementsByClassName(
  "day-number current-number ng-star-inserted"
)[0].innerText;

console.log(
  `Current day: ${currentDay} ${
    month[new Date().getMonth()]
  } ${new Date().getFullYear()}`
);
```

2. Check for navigation buttons: Ensure there are two navigation buttons (previous/next) and display their images.

```javascript
const arrowPrevious = document.querySelector('img[alt="arrow previous"]');
const arrowNext = document.querySelector('img[alt="arrow next"]');
console.log(
  arrowPrevious
    ? `Previos button image src is ${arrowPrevious.src}`
    : "Previos buttont dosen`t find!"
);
console.log(
  arrowNext
    ? `Next button image src is ${arrowNext.src}`
    : "Next buttont dosen`t find!"
);
```

3. Determine the displayed days of the week: Collect all elements with the class day-name and display their names.

```javascript
const daysName = Array.from(
  document.getElementsByClassName("day-name"),
  ({ innerText }) => {
    return innerText;
  }
);

daysName.forEach((day) => console.log(day));
```
