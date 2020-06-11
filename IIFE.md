
## IIFEs

try to answer the questions below first, then read the rest of the page

<details>
  <summary>What is an IIFE</summary>
  An IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.
</details>
<details>
  <summary>State the advantages of an IIFE</summary>
  
  #### Create a private state for any variable
  ```jsx
let reference = (function() {   
   let secret = "I cannot be changed by simple assignment";    
    return {     
         change(value) {       
           secret = value;     
         },      
         get secret() {       
           return secret;     
         }   
       }; 
     })();  
console.log(reference.secret); // "I cannot be changed by simple assignment"
reference.change("I am changed"); 
console.log(reference.secret); // "I am changed"
```
  
  #### doesnt pollute the global scope
</details>


An **IIFE** (Immediately Invoked Function Expression - pronounced "iffy") is a JavaScript function that runs as soon as it is defined.

```jsx
(function () {
    statements
})();
```

this is an anonymous function with lexical scope. This prevents accessing variables within the IIFE, as well as polluting the global scope.
