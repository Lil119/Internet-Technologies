# Presentation

![Slide1](src/assets/images/Slide1.PNG)
---

This is line 1
This is line 2
This is line 3  
This is line 4  
This is line 5  

---

![Slide2](src/assets/images/Slide2.PNG)  
---
This is para 1

This is para 2

This is para 3


---

![Slide3](src/assets/images/Slide3.PNG)  
---
Descriptive text here.

---

![Slide4](src/assets/images/Slide4.PNG)
---
Descriptive text here.

---

![Slide5](src/assets/images/Slide5.PNG)
---
Descriptive text here.

---

![Slide6](src/assets/images/Slide6.PNG)
---
Descriptive text here.

---

![Slide7](src/assets/images/Slide7.PNG)
---
Descriptive text here.

---

![Slide8](src/assets/images/Slide8.PNG)
---
The best way for us to demonstrate some of the key features of Next.js was to use it to build a simple example project and show you the code used and the output produced.

On the left here we can see the directory structure of the application. The section highlighted in green shows the app folder which the app router uses to create routes for each page of the application. A route is created for each folder inside the app folder.

The red section shows the posts folder inside the api folder. This structure creates an API route which points to this folder. An API route can then be used by the application to connect to backend services like databases and APIs.

The blue section shows a folder named blog which contains a file named page.tsx. This means that when a user visits …/blog, Next.js will serve this page.tsx file.

Inside the blog folder is a nested folder named [id]. You will notice that this folders name is wrapped in square brackets. This makes it a dynamic folder which in turn creates a dynamic route. This means that when a user visits …/blog/123, the page.tsx file inside the [id] folder captures 123 as the id and uses it to fetch corresponding data in order to render the page. 

---

![Slide9](src/assets/images/Slide9.PNG)
---
Here we can see the contents of the route.ts file inside the api/posts folder. This is the endpoint of the API route /api/posts. As we can see it contains an array of blog posts.

Pages can make fetch requests using the API route and the route.ts file acts as an internal API, which takes the request and returns the data.

---

![Slide10](src/assets/images/Slide10.PNG)
---
This is the code for the main posts page which displays a list of all posts
The top highlighted section shows the page making a fetch request to the API to get the posts array
After getting the posts array, it uses the map function to cycle through and create a div for each post in the array.

The link for each post is created using that posts unique id.

Using SSR, all of this work is done on the server and only the fully rendered page is sent to the browser so there is no loading time for the user.

---

![Slide11](src/assets/images/Slide11.PNG)
---
The individual post page also makes a fetch request to the API to get the posts array but instead of returning the entire array, we use the id which was included in the URL to only get the corresponding post.

---

![Slide12](src/assets/images/Slide12.PNG)
---
Descriptive text here.

---

![Slide14](src/assets/images/Slide14.PNG)
---
Next.js is considered a full-stack framework because it provides both frontend and backend capabilities.
It handles frontend tasks such as …
It also functions as a backend by using API routes.

---

![Slide15](src/assets/images/Slide15.PNG)
---
Descriptive text here.

---

![Slide16](src/assets/images/Slide16.PNG)
---
Descriptive text here.

---

![Slide17](src/assets/images/Slide17.PNG)
---
Descriptive text here.

---

![Slide18](src/assets/images/Slide18.PNG)
---
Descriptive text here.

---

![Slide19](src/assets/images/Slide19.PNG)
---
Descriptive text here.

---

![Slide20](src/assets/images/Slide20.PNG)
---
Descriptive text here.

---

![Slide21](src/assets/images/Slide21.PNG)
---
Descriptive text here.

---

![Slide22](src/assets/images/Slide22.PNG)
---
Descriptive text here.

---
