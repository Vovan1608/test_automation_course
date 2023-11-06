Task 1

To find the first h1 element on the main page.

```javascript
$x('.//*[@id="main-content"]/h1');
```

Task 2

Find all images that have the 'alt' attribute. Output the message in the console "Found (number) images with the alt attribute."

```javascript
const images = Array.from(document.querySelectorAll("img")).filter(
  ({ alt }) => alt.length > 0
);
console.log(`Found ${images.length} images with the alt attribute.`);
```
