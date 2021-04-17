# AJAX / XHR
A small widget to help me understand AJAX, JSON and XHR.
```javascript
/**
 * Small Ajax Project
 * By: Vincent Casilla
 */

let xhr = new XMLHttpRequest();

// Callback for when request is receieved
xhr.onreadystatechange = () => {
   if (xhr.readyState === 4) {
      console.log(typeof xhr.responseText); // checks type of data

      const data = JSON.parse(xhr.responseText);
      // This function will turn the data (JSON) that is a string into
      // an object

      // Create an element div
      const wrapper = document.querySelector("div.wrapper");
      const div = document.createElement("div");
      div.setAttribute("class", "names-list");
      wrapper.append(div);

      let namesUl = '<ul class="names-ul">';
      for (let i = 0; i < data.length; i++) {
         if (data[i].online === true) {
            namesUl += `<li class="online">${data[i].name} [Online]</li>`;
         } else {
            namesUl += `<li class="offline">${data[i].name} [Offline]</li>`;
         }
      }
      namesUl += "</ul>";

      console.log(namesUl);

      // Adds the looped list into the div
      div.innerHTML = namesUl;
   }
};
xhr.open("GET", "./data.json");
xhr.send();
```
