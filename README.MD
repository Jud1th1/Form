# Form Notes

## Table of contents

- [Form Basics](#Form-Basics)
  - [Form Attributes](#form-attributes)
  - [Form Elements](#form-elements)
- [Form Validation](#Form-Validation)

## Form Basics

### Form Attributes

- **Method**: specifies how form data should be sent to the server.
  - Form data can be sent as URL variables <span style="color:pink"> **(method="get")** </span> or as post transaction <span style="color:pink"> **(method = "post")** </span>
    - GET sends form data as URL parameters, making it visible in the address bar. It can be cached, bookmarked and remain in browser history
    - GET request should not be used with sensitive data
    - GET request are only used to request data (not modify)
    - GET is typically used for retrieving data, like search queries.
    - POST sends form data in the request body, keeping it out of the URL.
    - POST request can not be cached, bookmarked or remain in history
    - POST request do not have a data length restriction
    - POST is for form submissions or uploads and is more appropriate for sensitive information. (Not inherently secure but less visible )
- **Action**: defines action to be performed when the form is submitted.

i.e

```html
<form method="post" action="processor.php"></form>
```

---

- **Target**: specifies where to display the response received after subbmitting the form

i.e

```html
<form action="processor.php" target="_blank"></form>
```

| Value       | Description                                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------------- |
| \_blank     | Response displays in new window or tab (can be a security concern without rel="noopener noreferrer") |
| \_self      | Response displays in current window                                                                  |
| \_parent    | Response displays in parent frame                                                                    |
| \_top       | Response displays in full body of the window                                                         |
| _framename_ | Response displays in named iframe                                                                    |

---

## Form Elements

- <span style="color:pink"> **< input >** </span> Defines an input control
- <span style="color:pink"> **< label >** </span> Defines a label for an <span style="color:pink"> **< input >** </span> element
  - The <span style="color:salmon"> **for** </span> attribute of the <span style="color:pink"> **< label >** </span> tag should be equal to the <span style="color:salmon"> **id** </span> attribute of the <span style="color:pink"> **< input >** </span> element to bind them.
- <span style="color:pink"> **< select >** </span> Defines a drop-down list
- <span style="color:pink"> **< option >** </span>
  Defines an option in a drop-down list
  - Use **multiple** attribute to allow more than one selection
  - If multiple is used, the name must end with []
    - i.e < select name="pets[]" multiple>

  i.e

  ```html
  <label for="pets">Choose a pet:</label>
  <select id="cars" name="cars">
    <option value="cat">Cat</option>
    <option value="dog">Dog</option>
    <option value="bird">Bird</option>
  </select>
  ```

- <span style="color:pink"> **< optgroup >** </span>
  Defines a group of related options in drop down list
- <span style="color:pink"> **< textarea >** </span>
  Defines a multiline input control
  - The <span style="color:salmon"> **rows** </span> attribute specifies the visible number of lines in a text area.
  - The <span style="color:salmon"> **cols** </span>
    attribute specifies the visible width of a text area.

  ```html
  <textarea name="message" rows="5" cols="10">
    Leave us a message!
  </textarea>
  ```

- <span style="color:pink"> **< button >** </span>
  Defines a clickable button
- <span style="color:pink"> **< fieldset >** </span>
  Used to group related data
- <span style="color:pink"> **< legend >** </span>
  Defines a caption for a <span style="color:pink"> **< fieldset >** </span> element
  ```html
  <fieldset>
    <legend>Person:</legend>
    <label for="fname">First name:</label><br />
    <input type="text" id="fname" name="fname" value="John" /><br />
    <label for="lname">Last name:</label><br />
    <input type="text" id="lname" name="lname" value="Doe" /><br /><br />
  </fieldset>
  ```
- <span style="color:pink"> **< datalist >** </span>
  Specifies a list of pre-defined options for input controls
  - The <span style="color:salmon"> **list** </span> attribute of the <span style="color:pink"> **< input >** </span> element, must refer to the <span style="color:salmon"> **id** </span> attribute of the <span style="color:pink"> **< datalist >** </span> element.
  ```html
  <input list="pets" />
  <datalist id="pets">
    <option value="cat"></option>
    <option value="dog"></option>
    <option value="bird"></option>
  </datalist>
  ```
- <span style="color:pink"> **< output >** </span>
  Defines the result of a calculation

## Form Validation

### Back End Validation (Ex.1)

- Checking and validating user input from the server side after the form is submitted.
- Ensures data received is accurate, secure, and meets specific criteria before being processed.
  - **Purpose** : To prevent invalid or malicious data from being processed, leading to security vulnerabilities and data integrity issues.
- <span style="color:#7b9ea8"> **How it Works:** </span>
  - When form is submitted PHP script retrieves the data via <span style="color:pink"> $\_POST </span> or <span style="color:pink"> $\_GET </span>
  - Script checks each input field against defined rules _(i.e !empty, Validating email formats, URLS)_
  - If data fails validation the appropriate error msg is sent to the user
- PHP must be run through a server environment like localhost because it needs the server to process the code.
  Opening files directly or using Live Server bypasses the server, so only front-end code runs, not backend validation.

### Plain JavaScript Validation (Ex.2)

- JS validates form instead of HTML's required attribute
- Error msg are displayed in spans associated with each input field
- <span style="color:#7b9ea8"> **How it Works:** </span>
  - A counter tracks number of validation failures if any fail the form submission is prevented
  - Regular expressions are used to validate names and email addresses ensuring they meet the criteria specified.

### jQuery Validation

- Similar to JS validation but more compact (Ex.3)
- <span style="color:pink"> submit </span> event captures for submissions, and <span style="color:pink"> event.preventDefault() </span> is used to stop form submission if validation fails.
- You can use the validator plugin [jQuery plugin](https://jqueryvalidation.org/) to simplify form validation (Ex. 4)
  - <span style="color:#7b9ea8"> **How it Works:** </span>
    1. The jQuery library loads first
    2. The form validator plugin loads second
    3. Your script, initializing the validation loads third
- JQuery Advanced Plug in
  - Includes <span style="color:pink"> object </span> to define advanced validation rules and messages.
  - A method called <span style="color:pink"> phoneRegEx </span> is created to validate US phone numbers (found in class ppt)

### <span style="color:Red"> Importance of Validation:</span>

Front-end validation improves user experience by giving immediate feedback and guiding users to fix errors before submission.
Back-end validation ensures that the data received is accurate, secure, and meets required criteria, even if front-end validation is bypassed.

Without back-end validation, incorrect or malicious data could be stored, leading to system issues such as users being unable to receive emails, log in, or recover accounts.
