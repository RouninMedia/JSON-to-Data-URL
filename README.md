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

If the conditions above is met, the `JSONtoDataURL(JSONString)` function returns the validated JSON as a **Data URL**.

______

### `JSONtoDataURL(JSONString)` :

```

const JSONtoDataURL = (JSONString) => {

}

```

_____
