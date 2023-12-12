
In JavaScript, the only way to include variables and/or expressions in general within strings was this:
```javascript
let country = "France";
let capital = "Paris";
let numResidents = 67000000, numTourists = 90000000, numCities = 35000;
let officialLanguage = "French";
let myString = "The country is " + country + ", its capital is " + capital + ".\n It has " + numResidents + " residents and " + numTourists + " tourists annually. There are " + numCities + " cities in " + country + ". The official language is " + officialLanguage + ".";
```
Even from this small code snippet, it's evident that **the syntax is verbose**. I'm confident that if you've worked on a complex project or any code segment with specific strings, you've noticed how the content of these strings becomes unclear, and correctly placing quotes becomes a challenging task. This is precisely why template strings were introduced, resulting in a refactored version of the above example like this:
```javascript
let country = "France";
let capital = "Paris";
let numResidents = 67000000, numTourists = 90000000, numCities = 35000;
let officialLanguage = "French";
let myString = `The country is ${country}, its capital is ${capital}. It has ${numResidents} residents and ${numTourists} tourists annually. There are ${numCities} cities in ${country}. The official language is ${officialLanguage}.`;
```
We're allowed also to do is **perform arithmetic expressions** without the need to cast to the required type. Lastly, the newline character inserted will be appended to the string, becoming an actual newline character ```"\n"```.

Some of the most common **use cases** for template literals are:
- Dynamic Strings: Easily create strings that change based on variables or conditions.
- Multi-line Strings: Write cleaner code by avoiding concatenation for multi-line strings.
- HTML Templates: Generate HTML strings dynamically, particularly useful in frameworks like React or Angular.
- String Formatting: Create custom string formats easily by embedding expressions within the template literals.

```javascript
//HTML Templates
let user = {
    name: "John Doe",
    email: "john.doe@example.com",
    id: 123
};

let userCard = `
    <div class="user-card">
        <h2>${user.name}</h2>
        <p>Email: ${user.email}</p>
        <p>ID: ${user.id}</p>
    </div>
`;

console.log(userCard);
```
Another major feature is the **Tagged templates**: <br/>  
They are a more advanced form of template literals and they allow you to use a function to process the template literal, rather than just evaluating it as a string. This provides you with more control over how the strings and embedded expressions are concatenated.
  
```javascript
function tag(strings, ...values) {
  console.log(strings);
  console.log(values);
}

let name = "John Doe";
let age = 30;

tag`My name is ${name} and I'm ${age} years old.`;
```
The syntax of a tagged template is similar to calling a function with an argument, but instead of using parentheses, you use a template literal. The function that is used to tag the template is called a **tag function**. <br/>
The tag function receives two sets of parameters:
- An array of string values (the text between the expressions).
- The results of evaluating the expressions.
In this example, strings would be an array ["My name is ", " and I'm ", " years old."], and values would be an array ["John Doe", 30]. 

Tagged templates can be utilized also for **preventing Cross-Site Scripting (XSS) attacks** by escaping HTML characters. 

```javascript
function escapeHtml(strings, ...values) {
  const escaped = values.map((value) => {
    return String(value)
      .replace(/&/g, "&amp;")
      .replace(/</g, "&lt;")
      .replace(/>/g, "&gt;")
      .replace(/"/g, "&quot;")
      .replace(/'/g, "&#39;");
  });

  return strings.reduce(
    (result, string, i) => `${result}${string}${escaped[i] || ""}`,
    ""
  );
}

let userInput = '<script>alert("This is a potential XSS attack");</script>'; // Potentially harmful user input

let safeHtml = escapeHtml`<div>${userInput}</div>`;
console.log(safeHtml); // Outputs: <div>&lt;script&gt;alert(&quot;This is a potential XSS attack&quot;);&lt;/script&gt;</div>
```
The ```escapeHtml``` function takes the strings and values parameters and returns a new string. The strings parameter is an array of strings, and the values parameter is an array of values. The function then iterates over the values array and escapes any HTML characters. Finally, the function iterates over the strings array and concatenates the escaped values with the strings.
