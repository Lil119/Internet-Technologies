# How to Start a Project with Next.js

## Introduction

This tutorial is inspired by Derek Turner’s guide on [installing React](https://derekturner.github.io/IT-docs-24/#/Block_REACT/section_5/reactDevelopment1?id=dockervite-client-side-app), covering the initial setup for a Next.js project in a Docker container with Node.js and TypeScript.

## Setting Up a Docker Container with Node.js & TypeScript

To get started, ensure you have both **Node.js** and **Docker** installed, as well as the **Dev Containers** extension in **VSCode**.

1. Create a new folder on your PC called `next-tutorial`, then open it in VSCode.

   ![Creating the Folder](/Internet-Technologies/src/assets/images/create-folder.png)

2. Press:

   > `CTRL + SHIFT + P`

   and search for the command **"Dev Containers: Open Folder in Container"**. Select the newly created folder.

3. When prompted to store the configuration file, choose to store it in the workspace.

   ![Storing Configuration File](/Internet-Technologies/src/assets/images/add-config-workspace.png)

4. A dialog will appear asking you to select a container type. Search for **"Node & TypeScript"** and select it.

   ![Choosing Environment](/Internet-Technologies/src/assets/images/choose-environement.png)

5. Choose a Node.js version. For this tutorial, select **LTS version 20-bookworm**.

   ![Choosing Node Version](/Internet-Technologies/src/assets/images/choose-node-version.png)

6. You’ll see a couple of prompts with additional options. You can leave these blank and click **OK**.

   ![No Option 1](/Internet-Technologies/src/assets/images/no-option-1.png)

   ![No Option 2](/Internet-Technologies/src/assets/images/no-option-2.png)

The container will now start creating, and after a short wait, it will be up and running in Docker Desktop.

   ![Docker Container Running](/Internet-Technologies/src/assets/images/docker-container-running.png)

## Installing Next.js

With the container running, let’s install Next.js:

1. Open the terminal and run:

   > `npx create-next-app@latest`

   ![Installing Next.js](/Internet-Technologies/src/assets/images/press-y-to-install.png)

2. During installation, Next.js will ask you some setup questions. Name your project **next-demo**, and respond to the prompts as shown below:

   ![Questions Before Installing](/Internet-Technologies/src/assets/images/questions-asked.png)

3. Tailwind CSS is a popular CSS framework for styling Next.js projects, so consider including it if needed.

4. Once the installation completes, your project directory should look like this:

   ![File Tree](/Internet-Technologies/src/assets/images/file-tree-next.png)

5. Navigate into your new project folder:

   > `cd next-demo`

6. Start the development server by running:

   > `npm run dev`

7. You can now access your Next.js site at [http://localhost:3000/](http://localhost:3000/).

   ![Next.js Website Example](/Internet-Technologies/src/assets/images/next-website.png)

---
