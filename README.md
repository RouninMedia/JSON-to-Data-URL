# JSON to Data URL
The function `JSONtoDataURL(JSONString)` converts any **valid JSON** into a **Data URL**.

The function `dataURLtoJSON(dataURL)` converts a **Data URL** which satisfies certain criteria into a **valid JSON**.

______

## JSON to Data URL Function

### Step 1

The `JSONtoDataURL(JSONString)` function verifies that the string passed to the function:

 - represents **valid JSON**

If this condition is not met, the `JSONtoDataURL(JSONString)` function will return a verbose error detailing how the string may be fixed.

### Step 2

If the condition above is met, the `JSONtoDataURL(JSONString)` function returns the validated JSON as a **Data URL**.

______

### `JSONtoDataURL(JSONString)` :

```

const JSONtoDataURL = (JSONString) => {

  let jsonIsValid = validateJSON(JSONString);

  let dataURL = JSONString;
  dataURL = dataURL.replace(/(\s*\n)+\s*/g, ' ');
  dataURL = dataURL.replace(/\"/g, '\'');
  dataURL = dataURL.trim();

  const characterArray = dataURL.split('');

  for (let i = 0; i < characterArray.length; i++) {

    if (characterArray[i].match(/[A-Za-z0-9\.\,\;\:\/\*\-\=\_\~\'\!\$\@]/) === null) {

     characterArray[i] = encodeURIComponent(characterArray[i]);
    }
  }
  
  dataURL = characterArray.join('');
  
  if (jsonIsValid !== true) {
  
    dataURL = `%7B'AshivaConsole':'Data submitted does not represent valid JSON.','DataSubmitted':'${dataURL.replace(/\'/g, '\`')}'%7D`;
  }
  
  dataURL = 'data:text/plain;charset=utf-8,' + dataURL;

  return dataURL;
}

```

_____

## Data URL to JSON Function

Naturally, a function like `JSONtoDataURL(JSONString)`, above, needs a corresponding function which can perform the same transformation in reverse.

`dataURLtoJSON(dataURL)` will convert the **Data URL** (which conforms to certain constraints) into a valid **JSON**.

If the function cannot build a **JSON** out of the **Data URL**, it will return a verbose error, explaining why not.

### Step 1

The `dataURLtoJSON(dataURL)` function converts the **Data URL** provided into an **unformatted JSON**.

### Step 2

The `dataURLtoJSON(dataURL)` function then verifies that the **unformatted JSON**:

 - represents valid JSON

If this condition is not met, the `dataURLtoJSON(dataURL)` function will return a verbose error detailing how the string may be fixed.

### Step 3

If the condition above is met, the `dataURLtoJSON(dataURL)` function will format the **valid JSON** and return a **formatted, valid JSON**.

______

### `dataURLtoSVG(dataURL)` :

```
const dataURLtoJSON = (dataURL) => {

}

```
______

## Practical use-cases for JSON as a Data URL

 - Any function like `importJSON()` which, during execution, `fetch`-es a supplied url (pointing to a remotely-hosted **JSON**) and then processes the contents will be able to do the same with **JSON as a Data URL** but without the JSON needing to be hosted remotely.
