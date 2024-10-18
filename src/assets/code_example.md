# Basic Code Examples

## Introduction

This tutorial assumes you have a foundational understanding of HTML, CSS, TypeScript, and React. We'll focus on the unique features of Next.js and how it differs from standard React development.

Next.js offers several advantages over React, such as:
- Faster development for key features like routing.
- Improved SEO optimization out of the box.
- Quicker page load times.

These benefits make Next.js particularly useful for building blogs, websites, e-commerce platforms, or any other apps that need to be accessible and performant in a web browser.

In this tutorial, we’ll build a simple video game review website to demonstrate the core features of Next.js.

## Simplified routing with folders and files

### Basic routes

In Next.js, routing is simplified using folders and files to structure your app. Each folder corresponds to a route on your website, and files contain the code for your components.

Next.js also introduces several special files that serve specific purposes:
- **Layout**: Shared UI components that are reused across multiple pages.
- **Page**: Defines the content and UI for an individual page.
- **Loading**: A UI element that appears while data is loading.
- **Not-Found**: The UI displayed when a page or route is not found.
- **Error**: Handles specific errors for individual pages.
- **Global Error**: Manages errors that affect the entire app.
- **Route**: Defines server-side API endpoints.
- **Template**: A custom layout for specific pages.
- **Default**: Acts as a fallback UI for routes with multiple matches.

By simply naming a `.tsx` file with one of these predefined names, Next.js automatically assigns its role. This eliminates the need for React Router, simplifying the overall development process.

### Example: Creating a New Route

To demonstrate, let's create an "About" page in Next.js.

1. In the `app` folder, create a new folder named `about`. This folder will represent the `/about` route.
2. Inside the `about` folder, create a file named `page.tsx`.
3. Add the following code to `page.tsx` to define the "About Us" page:

   ```tsx
   export default function About() {
       return (
           <div>
               <h1>About Us</h1>
               <div>Email: email@email.com</div>
               <div>Phone: (123) 456-7890</div>
           </div>
       );
   }

After following these steps, your project structure should look like this:

![File tree](/Internet-Technologies/src/assets/images/code_example/file-structure-routing.png)

Now, you can run your application with the command:
> `npm run dev`

Then, open [http://localhost:3000/about](http://localhost:3000/about) in your browser to view the `About Us` page.

![Content of about page](/Internet-Technologies/src/assets/images/code_example/about-page.png)

### Example: Creating a dynamic route

Next.js makes it easy to create dynamic routes using bracket notation for folder and file names. Let’s create pages for different game reviews.

1. In the `app` folder, create a new folder named `reviews`. This will represent the `/reviews` route.

2. Inside the `reviews` folder, create a `page.tsx` file with the following code to display a list of reviews:

   ```tsx
   export default function ReviewPage() {
       return (
           <>
               <h1>Review List</h1>
               <ul>
                   <li><a href="/reviews/1">Review 1</a></li>
                   <li><a href="/reviews/2">Review 2</a></li>
                   <li><a href="/reviews/3">Review 3</a></li>
               </ul>
           </>
       );
   }
   
Now, you can see the list of review on [http://localhost:3000/reviews](http://localhost:3000/reviews).

![List of reviews](/Internet-Technologies/src/assets/images/code_example/review-list.png)

3. Inside the `reviews` folder, create a new folder named `[reviewId]`. This will represent dynamic routes for individual reviews.

4. In the `[reviewId]` folder, create a `page.tsx` file and add the following code:

   ```tsx
   export default function DetailsPage({ params }: { params: { reviewId: string } }) {
       return (
           <div>
               <h1>Review {params.reviewId}</h1>
           </div>
       );
   }


You can now access [http://localhost:3000/reviews/1](http://localhost:3000/reviews/1) and you will see "Review 1" on the page.

![Review 1](/Internet-Technologies/src/assets/images/code_example/review-1.png)

## Simplified API gestion

Next.js allows to write fullstack applications with React. It adds tools to code API easily.

### Example : Create an API for our reviews

in api/reviews : 
export default function handler(req, res) {
  res.status(200).json({ name: "Review of the game number 1" });
}

### Example : Access an API


## Better SEO

### Quicker loading

#### Optimizing fonts and images




## Using Tailwind CSS