# Basic Code Examples

## Introduction

This tutorial assumes you have a foundational understanding of HTML, CSS, TypeScript, and React. We'll focus on the unique features of Next.js and how it differs from standard React development.

Next.js offers several advantages over React, such as:
- Faster development for key features like routing.
- Improved SEO optimization out of the box.
- Quicker page load times.

These benefits make Next.js particularly useful for building blogs, websites, e-commerce platforms, or any other apps that need to be accessible and performant in a web browser.

In this tutorial, we’ll build a simple review website to demonstrate some core features of Next.js.





## Simplified routing with folders and files

In this tutorial, we will use the App Router because it is the most recent and complete router for Next.js. It offers more features and improvements compared to the older Page Router. However, you might come across older tutorials that still use the Page Router. You can easily recognize them because they have a "pages" folder in their project structure. The App Router, on the other hand, uses an "app" folder to manage routes in a more organized and modern way.


### Basic routes

In Next.js, routing is simplified using folders and files to structure your app. Each folder corresponds to a route on your website, and files contain the code for your components.

Next.js also introduces several special files that serve specific purposes:
- **layout**: Shared UI components that are reused across multiple pages.
- **page**: Defines the content and UI for an individual page.
- **loading**: A UI element that appears while data is loading.
- **not-Found**: The UI displayed when a page or route is not found.
- **error**: Handles specific errors for individual pages.
- **global-error**: Manages errors that affect the entire app.
- **route**: Defines server-side API endpoints.
- **template**: A custom layout for specific pages.
- **default**: Acts as a fallback UI for routes with multiple matches.

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

Now, you can run your application with the command :
> `npm run dev`

Then, open [http://localhost:3000/about](http://localhost:3000/about) in your browser to view the `About Us` page.

![Content of about page](/Internet-Technologies/src/assets/images/code_example/about-page.png)



### Example: Creating a dynamic route

Next.js makes it easy to create dynamic routes using bracket notation for folder and file names. Let’s create pages for different reviews.

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
   
Now, if you relaunch the app, you can see the list of review on [http://localhost:3000/reviews](http://localhost:3000/reviews).

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

This code allows you to personalize each page with the review id used in the route.

You can now access [http://localhost:3000/reviews/1](http://localhost:3000/reviews/1) and you will see "Review 1" on the page.

![Review 1](/Internet-Technologies/src/assets/images/code_example/review-1.png)

If you access [http://localhost:3000/reviews/2](http://localhost:3000/reviews/2), it will show "Review 2".




### Example: Having parameters in the URL with **useSearchParams**

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


In this example, we are using the `useSearchParams` function from Next.js, which is a **Client Component**. Since the page relies on client-side features, it's important to declare that the component will run on the client by including `"use client"` at the top of the file. You need to specify it because all component in the app folder are rendered server side by default.

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

A basic way to retrieve data in React would be to use `useEffect` and `useState`. However, in Next.js, we have a more efficient approach. We'll use the `fetch` function to retrieve data.

Let's update the reviews list page to display the reviews from our API:

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

    export default async function ReviewPage() {
      const data = await fetch('http://localhost:3000/api/reviews')
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

Now, you can see the list of reviews by navigating to the following address: [http://localhost:3000/reviews](http://localhost:3000/reviews).

![Better reviews](/Internet-Technologies/src/assets/images/code_example/better-reviews.png)


We used the Next.js `Link` component instead of the standard HTML `<a>` tag. This is because `Link` enhances user experience by allowing seamless client-side navigation without reloading the page. It's best practice to use the `Link` component throughout your Next.js project for internal navigation.

You can click on the link to see the details page of each review.




### Fetching Data in Next.js App Router

But let's analyse more our `fetch` component, cause it is way more complex than it looks.

There are two primary ways to fetch data in the **App Router**:

1. **Static Rendering (Static API):** Data fetched during build time using `fetch` with caching.
2. **Dynamic Rendering (Dynamic API):** Data fetched at runtime using dynamic `fetch`.

#### Static Rendering with Static API (Using Cache)

In the **App Router**, components are server-side by default and can directly fetch data. To fetch data from a **static API** (an API where data does not change often), you use the `fetch` method with cache control. The default behavior of `fetch` in server components is to cache the result, making it static and suitable for **Static Site Generation (SSG)**.

In the code used for fetching our reviews, our data is fetched statically. 
This means the page will be **statically generated**, and the data will only be fetched once during the build.

You can test this by modifying the content of the API and relaunching the server.

In app/api/reviewsroute.tsx :

```tsx
import { NextResponse } from 'next/server';

export async function GET() {
    return NextResponse.json([
        {
            id: 1,
            title: "Changed review",
            description: "this is a changed review",
            stars: 3
        },
        {
            id: 2,
            title: "Negative review",
            description: "this is my bad review",
            stars: 1
        }
    ]);
}
```

 If you go back to [http://localhost:3000/reviews](http://localhost:3000/reviews), you will noticed the data has not been updated on the page.

That is because the data has been stored in cache without any expiration time.




#### Dynamic Rendering with Dynamic API (No Cache)

For **dynamic APIs** (where data changes frequently or needs to be fetched on every request), you can explicitly disable caching in the `fetch` call. This ensures that the data is fetched at runtime on each request.

Example (Dynamic Fetch without Cache):

```tsx
  const data = await fetch('http://localhost:3000/api/reviews', {
    cache: 'no-store', 
  })
```

In this example, the `cache: 'no-store'` option forces the `fetch` request to be **dynamic**, meaning that data is fetched on **every request**.  

This is useful when the API data is frequently updated, or when each response of the API depends on who is asking (authentification for example is a dynamic API).

If you test this code in app/reviews/page.tsx, you will now see the data you modified at [http://localhost:3000/reviews](http://localhost:3000/reviews).

![Changed review](/Internet-Technologies/src/assets/images/code_example/changed-review.png)


#### Key Differences Between Static and Dynamic API Fetching in App Router


| **Feature**                    | **Static API (SSG)**                                              | **Dynamic API (SSR)**                                                  |
| ------------------------------ | ----------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **When Data is Fetched**       | During build time (or with revalidation)                          | On every request                                                       |
| **Cache Behavior**             | Cached by default (can be revalidated)                            | No caching (`cache: 'no-store'`)                                       |
| **Fetch Method in App Router** | `fetch('api-url', { next: { revalidate: X } })`                   | `fetch('api-url', { cache: 'no-store' })`                              |
| **Use Case**                   | Static data that rarely changes (e.g., blog posts, product pages) | Dynamic data that changes frequently (e.g., user dashboard, live data) |
| **Performance**                | Faster, since pre-rendered at build time                          | Slightly slower, since data is fetched on each request                 |




#### Revalidation (ISR) in App Router

If you want to fetch data statically but also periodically revalidate it, you can use **ISR (Incremental Static Regeneration)** in the **App Router**. This allows pages to be regenerated in the background based on a time interval without rebuilding the entire site.

```tsx
  const data = await fetch('http://localhost:3000/api/reviews', {
    next: { revalidate: 60 },
  })
```

With this setup, the data will be cached and updated every 60 seconds when a new request comes in, ensuring up-to-date content without fetching on every request.



## Optimizing images

Next.js also optimizes several components, including images through its built-in `next/image` component, which provides several automatic optimizations:

- **Responsive Images**: Automatically resizes and serves the right image for different devices.
- **Lazy Loading**: Loads images only when they are about to enter the viewport.
- **Image Compression**: Compresses images without quality loss to reduce file sizes.

Let's try to show a star image on our home page that will link to the list of reviews.

1. Add a star.png image to a folder next-demo/assets that you can create
2. Add this code to your app/page.tsx file :

```tsx
import Image from 'next/image';
import Link from "next/link"
import star from '../assets/star.png'

export default async function Home() {
  return (
    <Link href="/reviews" passHref>
      <Image
        src={star}
        alt="Star"
        width={360}
        height={360}
      />
    </Link>
  )
}
```

You can check the results at [http://localhost:3000](http://localhost:3000).

![Star image](/Internet-Technologies/src/assets/images/code_example/star.png)

If you click on the star image, you will be redirected to the list of reviews pages.


## Conclusion

In this tutorial, we've covered the essentials of using Next.js to build a web application. By exploring core features such as simplified routing, dynamic and static data fetching, API creation, and image optimization, you've gained insight into why Next.js can be an amazing framework for modern web development. 

With these tools and techniques, you’re now ready to leverage Next.js’s capabilities to build fast, accessible, and SEO-optimized web applications. Whether creating a blog, an e-commerce site, or a complex interactive platform, Next.js empowers you to deliver a high-quality user experience.