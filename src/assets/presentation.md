# Presentation
---

![Slide1](src/assets/images/Slide1.PNG)
---

Our presentation covers an overview of next.js, it's key features, examples, how it fits into a full stack system,  
providing real world use cases, pros and cons, and a brief demonstration.

---

![Slide2](src/assets/images/Slide2.PNG)  
---

First, we provided an introduction to Next.js, where we discussed what it is and why it's important in modern  
web development.  

Next, we devlved into the key features that make Next.js a poweful framework, such as server-side rendering,  
static site generation, and it's unique file-based routing system.  

We then moved onto an example project where we expanded upon some of these key features. For this example, we  
demostrated the development of a simple blog.  

Following that, we showcased real-world use cases to illustarte how Next.js is being utilisted effectivley in the industry and the benefits it offers in that context.  

We also discussed the pros and cons of Next.js, highlighting its advantages as well as any potenial limitations or  
challeneges that developers might face.  

Finally, we concluded with a recap of the key points we covered and opened the floor for a Q&A session, where we  
encouraged viewers to ask any questions you may have about Next.js.

---

![Slide3](src/assets/images/Slide3.PNG)  
---

Next.js is an open-source framework built on top of React.  

It was developed by Vercel to simplify server-side rendering, static site generation, and other advanced features  
for React applications.  

With Next.js, developers can achieve better performance and SEO, thanks to features like server-side rendering  
and th ability to generate static pages.  

It's especially popular for builiding scalable, productions-ready applications with a seamless development  
experience.

---

![Slide4](src/assets/images/Slide4.PNG)
---

Next.js offer Server-Side Rendering, or SSR.  

This means pages are rendered on the server before they're sent to the browser, making the site load faster and  
improving SEO.  

It's useful for dynamic content that needs the stay up-to-date while still loading quickly for users.  

Then there's Static Site Generation or SSG.  

This feature builds static pages ahead of time at compile, so when users visit the site, those pages load almost  
instantly.  

It's great for content that doesn't change much, like blogs or marketing pages.

---

![Slide5](src/assets/images/Slide5.PNG)
---

Next.js also next us developers create API Routes directly within the app, so instead of setting up a seperate backend, we can handle requests, like fetching data or submitting forms, right in the Next.js code.  

This simplifies the development process a lot.

---

![Slide6](src/assets/images/Slide6.PNG)
---

Another standout feature is Built-In Image Optimisation.  

Next.js automatically resizes and optimises images for different screen sizes and formats, like WebP.  

It also lazy loads images, meaning they only load when they're needed, which really helps with performance.

---

![Slide7](src/assets/images/Slide7.PNG)
---

Finally, Next.js supports Dynamic Routing, which means we can create pages based on any parameter, like user  
profiles or product pages, without manually setting up each route.  

It keeps navigation efficient, especially in larger apps.

---

![Slide8](src/assets/images/Slide8.PNG)
---

We created a simple blog application to demonstrate some of the features of Next.js.

This slide shows the directory structure of the application.  
The section highlighted in green shows the app folder which the app router uses to create routes for each page of the application. A route is created for each folder inside the app folder.

The red section shows the posts folder inside the api folder. This structure creates an API route which points to this folder. An API route can then be used by the application to connect to backend services like databases and APIs.

The blue section shows a folder named blog which contains a file named page.tsx. This means that when a user visits …/blog, Next.js will serve this page.tsx file.

Inside the blog folder is a nested folder named [id]. You will notice that this folders name is wrapped in square brackets. This makes it a dynamic folder which creates a dynamic route. This means that when a user visits …/blog/123, the page.tsx file inside the [id] folder captures 123 as the id and uses it to fetch corresponding data in order to render the page. 

---

![Slide9](src/assets/images/Slide9.PNG)
---

This slide shows the contents of the route.ts file inside the api/posts folder.

This is the endpoint of the API route /api/posts and contains an array of blog posts.

Pages can make fetch requests using the API route and the route.ts file acts as an internal API, which takes the request and returns the data.


---


![Slide10](src/assets/images/Slide10.PNG)
---

This slide shows the code for the main posts page which displays a list of all posts.

The top highlighted section shows the page making a fetch request to the API to get the posts array.  
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

This slide shows screenshots of each page of the application.

The highlighted sections show the URLs for each page with the URLs of the post pages showing the id which is used in the dynamic routing.


---


![Slide14](src/assets/images/Slide14.PNG)
---

Next.js is considered a full-stack framework because it provides both frontend and backend capabilities.

It handles frontend tasks like rendering, routing, image optimisation, and UI interactions using React components.

It also functions as a backend by using API routes which allow you to build server-side logic into applications, interact with databases, and connect to external services.


---


![Slide15](src/assets/images/Slide15.PNG)
---

Next.js is a widely used framework built on a massively popular library. Next.js was built on top of the success of React.js, allowing it to be quickly and widely adopted across industries. In the 2024 Stack Overflow Developer survey Next.js was voted 4th most popular web framework/technology (with React.js in 2nd place).

---

![Slide16](src/assets/images/Slide16.PNG)
---

One major industry which has adopted Next.js is e-commerece. Next.js provides a wide range of out-of-the-box tools, making it a perfect framework for massive international e-commerce companies. The Next.js Image component features built-in image scaling and optimisation, which can greatly improve performance on image-heavy websites - as most e-commerce websites are. Next.js also offers massive SEO improvements over React.js helping companies perform better on Google search rankings and attracting more clicks. Next.js also has built-in features for internationalisation, making it easy for companies which work internationally to adapt currency, time, and text to the users' region.

---

![Slide17](src/assets/images/Slide17.PNG)
---

Next.js is also the platform of choice for many media and multimedia websites, including STV Player and The Washington Post. These platforms also use many images, using the Next.js Image component. Partial prerendering in Next.js can improve page load times by rendering static or slowly changing pages ahead of time.

---

![Slide18](src/assets/images/Slide18.PNG)
---

Many AI platforms are using Next.js to create their web presence and showcase their software. This is often because Next.js is easy to scale, allowing SAAS companies who start very small to scale their website rapidly as their business grows. Next.js also provides a good developer experience (especially when used with TypeScript), explaining its high ranking in the 2024 Stack Overflow Developer Survey.  

---

![Slide19](src/assets/images/Slide19.PNG)
---

As with all technologies, Next.js has both benefits and pitfalls and may not be the best solution in every scenario. The main benefits of using Next.js over React.js are the SEO benefits and the fact that Next.js is a full-stack framework. Next.js also has the capability to implement multiple different page rendering methods, from static server-generated pages to client-rendered pages to partially preloaded pages. 

Next.js also has great documentation and a large community of developers. It is easy to get started with Next.js and explore basic features. However, advanced features can be difficult to understand, and becoming an expert with the framework will require an investment of time and energy. Although Next.js has many great features out-of-the-box, it has poor state management by default, and additional packages will be required to manage state in large applications.

---

![Slide20](src/assets/images/Slide20.PNG)
---

![Slide21](src/assets/images/Slide21.PNG)
---

![Slide22](src/assets/images/Slide22.PNG)
---
