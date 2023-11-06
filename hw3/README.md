Task 1

To find the first h1 element on the main page.

```javascript
$x('.//*[@id="main-content"]/h1');
```

Task 2

Find all images that have the 'alt' attribute. Output the message in the console "Found (number) images with the alt attribute."

```javascript
const images = Array.from($x(".//img")).filter(({ alt }) => alt.length > 0);
console.log(`Found ${images.length} images with the alt attribute.`);
```

Task 3

Find the button element with the text "Start forming a habit!". If an element with such text is not found, display a corresponding message. Output the message with numbers of buttons in the console.

\*Check the accuracy of the number of buttons found. If you get an incorrect value, analyze why this happened. To do this, find the code for the required elements and, if necessary, modify your script.

```javascript
console.log(
  $x('.//button[contains(text(), "Почати формувати звичку!")]').length |
    "Element with such text is not found!"
);
```
