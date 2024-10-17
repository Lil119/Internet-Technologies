# How to start a project on Next.js

## Introduction

The first part of this tutorial is heavily based on the tutorial of Derek Turner on [how to install React](https://derekturner.github.io/IT-docs-24/#/Block_REACT/section_5/reactDevelopment1?id=dockervite-client-side-app).

## Installing a Docker container with a Node & Typescript environment

First, you will need to have Node.js installed.

You will also need to have Docker running and the extension Dev Containers in VSCode.

Create a new folder "next-tutorial" on your PC and open it with VSCode.
![](/../Internet-Technologies/src/assets/images/create-folder.png)

Then click "CTRL + SHIFT + P" and search for the command "Dev Containers: Open Folder in Container".

This will open a dialog in which you will choose the new folder created.

VSCode will ask you where to store the configuration file and you can choose to store it in the workspace.
![](/src/assets/images/add-config-workspace.png)

A prompt then appears asking you to select the type of container needed. Search and click on "Node & Typescript."
![](/src/assets/images/choose-environement.png)

Then you can choose a Node version. For this tutorial, we will use LTS version 20-bookworm.
![](/src/assets/images/choose-node-version.png)

VSCode will then ask you two questions in which you can select none of the options and press Ok.
![](/src/assets/images/no-option-1.png)
![](/src/assets/images/no-option-2.png)

The system will finally start to create the container.
After a while, the container will start running in Docker Desktop.
![](/src/assets/images/docker-container-running.png)




## Installing Next.js

Now that you have a container running, let's install Next.js.

First, you will need to run the command "npx create-next-app@latest" in the terminal.
![](/src/assets/images/press-y-to-install.png)

Then, Next will ask you several questions before installing. Name your project "next-demo" and answer as the following :
![](/src/assets/images/questions-asked.png)
Tailwind CSS is a CSS framework that is often used with Next.js.

Once the installation is complete, the file tree will look like this :
![](/src/assets/images/file-tree-next.png)

Then you will need to place yourself in the right folder using "cd next-demo".

Then run "npm run dev".

You can then access the Next.js website at http://localhost:3000/.
![](/src/assets/images/next-website.png)