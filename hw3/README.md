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

Task 4

Validate the presence and visibility of the site search icon on the webpage, and ensure the image associated with the search icon has the appropriate alt text and a source (src) path.

```javascript
const searchIcon = Array.from($x('.//li[@aria-label="site search"]/img'));

if (searchIcon.length === 1) {
  console.log("The site search icon on the webpage is presence.");

  const { alt: altAttr, src: srcAttr, style: styleProp } = searchIcon[0];

  styleProp.display === "none" ||
    console.log("The site search icon on the webpage is visibile.");
  (altAttr.length > 0) |
    console.log(
      "The image associated with the search icon has the appropriate alt text."
    );
  srcAttr.includes("https://www.") |
    console.log(
      "The image associated with the search icon has a source (src) path."
    );
} else {
  console.log("No way!");
}
```

Task 5

Log into your profile at https://www.greencity.social/#/profile. At the bottom of the page, there are checkboxes. Find them, check their state (checked or not), and display a message about the number of checked and unchecked checkboxes.

```javascript
const inputsCheckbox = Array.from(
  $x(
    './/p[contains(text(), "Конфіденційність профілю")]/following-sibling::ul/li/label/input'
  )
);

let checkedCheckbox = 0;
let uncheckedCheckbox = 0;

inputsCheckbox.forEach(({ checked }) => {
  checked ? (checkedCheckbox += 1) : (uncheckedCheckbox += 1);
});

console.log(`Number of checked checkboxes is ${checkedCheckbox}`);
console.log(`Number of unchecked checkboxes is ${uncheckedCheckbox}`);
```

Task 6 \*

Validate the website's ability to switch languages effectively.

1. Initiate a search to identify the user interface element designated for language toggling.
2. If the specified element is successfully pinpointed, activate it to attempt a language change.
3. Log the result in the console, specifying whether the language toggle element was detected.
4. Should the language alteration succeed, log the preceding and new language settings into the console for verification purposes.

```javascript
const languageSwitcher = $x('.//ul[@aria-label="language switcher"]')[0];

let previousLanguage = $x('.//ul[@aria-label="language switcher"]/li/span')[0]
  .innerText;
let currentLanguage = " ";

function handleSwitcherClick() {
  console.log("The language toggle element was detected");

  languageSwitcher.removeEventListener("click", handleSwitcherClick);
}

languageSwitcher.addEventListener("click", handleSwitcherClick);

function handleChangeLang() {
  let ulLangSwitch = document.querySelectorAll(
    'ul[aria-label="language switcher"]'
  );
  let ariaExpanded = ulLangSwitch[0].ariaExpanded;

  if (
    document.querySelectorAll("li.lang-option span")[0].innerText !==
    previousLanguage
  ) {
    console.log("the preceding language is: " + previousLanguage);
    currentLanguage = document.querySelectorAll("li.lang-option span")[0]
      .innerText;
    console.log("the new language is: " + currentLanguage);
    previousLanguage = currentLanguage;
  }
}

languageSwitcher.addEventListener("click", handleChangeLang);
```
