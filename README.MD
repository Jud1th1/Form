# Form Notes

## Table of contents

- [Form Basics](#Form-Basics)
  - [Form Attributes](#form-attributes)
  - [Form Elements](#form-elements)


## Form Basics
### Form Attributes
- **Method**: specifies how form data should be sent to the server. 
  - Form data can be sent as URL variables <span style="color:pink"> **(method="get")** </span> or as post transction <span style="color:pink"> **(method = "post")** </span>

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

| Value | Description |
|--------|------------|
| _blank  | Response displays in new window or tab |
| _self | Response displays in current window |
| _parent | Response displays in parent frame|
| _top | Response displays in full body of the window |
| _framename_ | Response displays in named iframe |

---

## Form Elements

- <span style="color:pink"> **< input >** </span> Defines an input control
- <span style="color:pink"> **< label >** </span> 	Defines a label for an <span style="color:pink"> **< input >** </span>  element
  - The <span style="color:salmon"> **for** </span> attribute of the <span style="color:pink"> **< label >** </span>  tag shold be equal to the <span style="color:salmon"> **id** </span> attribute of the <span style="color:pink"> **< input >** </span>  element to bind them.
- <span style="color:pink"> **< select >** </span> Defines a drop-down list
- <span style="color:pink"> **< option >** </span> 
Defines an option in a drop-down list
  - Use **mulitple** attribute to allow more than one selection

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
Defines a caption for a <span style="color:pink"> **< fieldset >** </span>  element
  ``` html
   <fieldset>
      <legend>Person:</legend>
      <label for="fname">First name:</label><br>
      <input type="text" id="fname" name="fname" value="John"><br>
      <label for="lname">Last name:</label><br>
      <input type="text" id="lname" name="lname" value="Doe"><br><br>
  </fieldset>
  ```
- <span style="color:pink"> **< datalist >** </span> 
Specifies a list of pre-defined options for input controls
  - The <span style="color:salmon"> **list** </span> attribute of the <span style="color:pink"> **< input >** </span> element, must refer to the <span style="color:salmon"> **id** </span> attribute of the <span style="color:pink"> **< datalist >** </span> element.
  ```html
    <input list="pets">
    <datalist id="pets">
      <option value="cat">
      <option value="dog">
      <option value="bird">
    </datalist>
  ```
- <span style="color:pink"> **< output >** </span> 
Defines the result of a calculation


