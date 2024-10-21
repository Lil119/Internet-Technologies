# Basic Code Examples

## Introduction

This tutorial assumes you have a foundational understanding of HTML, CSS, TypeScript, and React. We'll focus on the unique features of Next.js and how it differs from standard React development.

Next.js offers several advantages over React, such as:
- Faster development for key features like routing.
- Improved SEO optimization out of the box.
- Quicker page load times.

These benefits make Next.js particularly useful for building blogs, websites, e-commerce platforms, or any other apps that need to be accessible and performant in a web browser.

In this tutorial, we’ll build a simple review website to demonstrate the core features of Next.js.



## Simplified routing with folders and files

### Basic routes

In Next.js, routing is simplified using folders and files to structure your app. Each folder corresponds to a route on your website, and files contain the code for your components.

Next.js also introduces several special files that serve specific purposes:
- **Layout**: Shared UI components that are reused across multiple pages.
- **Page**: Defines the content and UI for an individual page.
- **Loading**: A UI element that appears while data is loading.
- **Not-Found**: The UI displayed when a page or route is not found.
- **Error**: Handles specific errors for individual pages.
- **Global-error**: Manages errors that affect the entire app.
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

### Example: Having parameters in the URL

You can also pass multiple parameters through the URL.

To demonstrate this, you can update the `DetailsPage` function with the following code:

    ```tsx
    "use client";

    import { useSearchParams } from 'next/navigation';

    export default function DetailsPage({ params }: { params: { reviewId: string } }) {
        const searchParams = useSearchParams();
    
        return (
            <div>
                <h1>Review ID: {params.reviewId}</h1>
                <h2>Title: {searchParams.get("title")}</h2>
                <p>Description: {searchParams.get("description")}</p>
                <p>Stars: {searchParams.get("stars")}</p>
            </div>
        );
    }
    ```

In this example, we are using the `useSearchParams` function from Next.js, which is a **Client Component**. Since the page relies on client-side features, it's important to declare that the component will run on the client by including `"use client"` at the top of the file.

The `useSearchParams` function allows you to retrieve query parameters from the URL and use them in your component.

You can test this implementation by navigating to the following URL:

[http://localhost:3000/reviews/1?title=Great%20Product&description=This%20product%20was%20fantastic!&stars=5](http://localhost:3000/reviews/1?title=Great%20Product&description=This%20product%20was%20fantastic!&stars=5)

This will render the following:

![Review Details](/Internet-Technologies/src/assets/images/code_example/review-details.png)

In this example:
- The **Review ID** is retrieved from the URL path.
- The **Title**, **Description**, and **Stars** are extracted from the query parameters.



## Simplified API gestion

Next.js enables you to build fullstack applications with React, providing tools to easily create APIs.

### Example: Create an API for Reviews

To create an API endpoint for handling reviews, follow these steps:

1. Inside the `app` folder, create a new folder named `api`.
2. Within the `api` folder, create another folder named `reviews`.
3. In the `reviews` folder, create a file named `route.tsx`.
4. Add the following code to `route.tsx`:

    ```tsx
    import { NextResponse } from 'next/server';

    export async function GET() {
        return NextResponse.json([
            {
                id: 1,
                title: "Positive review",
                description: "This is my good review",
                stars: 5
            },
            {
                id: 2,
                title: "Negative review",
                description: "This is my bad review",
                stars: 1
            }
        ]);
    }
    ```

This code defines a simple `GET` endpoint that returns a list of reviews in JSON format. 

You can access the reviews API by visiting the following URL in your browser or using a tool like Postman : [http://localhost:3000/api/reviews](http://localhost:3000/api/reviews) 

This will display the list of reviews as shown below :

![Api for reviews](/Internet-Technologies/src/assets/images/code_example/api-reviews.png)

### Example : Access an API

Now that we have created an API route, the next step is to display the data on our website.

A basic way to retrieve data in React would be to use `useEffect` and `useState`. However, in Next.js, we have a more efficient approach. We'll use the `fetch` function to retrieve data on the Client-Side.

Let's update the reviews list page to display the reviews from our API:

### Steps:

1. Open the `app/reviews/page.tsx` file.
2. Replace the existing code with the following:

    ```tsx
    import Link from "next/link"

    type Review = {
      id: number;
      title: string;
      description: string;
      stars: number;
    }

    export default async function Home() {
      const data = await fetch('http://localhost:3000/api/reviews', { cache: 'no-store' })
      const reviews: Review[] = await data.json();
      return (
        <ul>
          {reviews.map((review, index) => (
            <li key={index} style={{
              backgroundColor: '#f9f9f9',
              padding: '15px',
              marginBottom: '10px',
              borderRadius: '8px',
              boxShadow: '0px 2px 5px rgba(0, 0, 0, 0.1)'
            }}>
              <strong>Title :</strong> {review.title}<br></br>
              <strong>Description :</strong> {review.description}<br></br>
              <strong>Stars :</strong> {review.stars}<br></br>
              <Link href={"/reviews/" + review.id + "?title=" + review.title + "&description=" + review.description + "&stars=" + review.stars} style={{
                color: '#0070f3',
                textDecoration: 'underline',
                fontWeight: 'bold',
              }}>
                Details of review {review.id}
              </Link>
            </li>
          ))}
        </ul>
      )
    }
    ```
We specified a no-store configuration for the cache in the `fetch` function, so the page will retrieve the data every time it is loaded.

Now, you can see the list of reviews by navigating to the following address: [http://localhost:3000/reviews](http://localhost:3000/reviews).

![Better reviews](/Internet-Technologies/src/assets/images/code_example/better-reviews.png)


We used the Next.js `Link` component instead of the standard HTML `<a>` tag. This is because `Link` enhances user experience by allowing seamless client-side navigation without reloading the page. It's best practice to use the `Link` component throughout your Next.js project for internal navigation.






## Better SEO by pre-rendering pages

One of the biggest advantages of Next.js is to improve the SEO by loading pages quicker.
This can be achieved by using two functions Next.js offers : getServerSideProps and getStaticProps.








#### Optimizing fonts and images




## Using Tailwind CSS