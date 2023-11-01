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
Array.from(document.getElementsByTagName("input"), ({ type }) => {
  console.log(type);
  return type;
});
```
