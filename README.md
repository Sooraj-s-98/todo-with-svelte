# 🔖 Todo With Svelte

A simple todo app built with Appwrite and Vue

If you simply want to try out the App, go ahead and check out the demo at https://appwrite-todo-with-vue.vercel.app/

## 🎬 Getting Started

### 🤘 Install Appwrite 
Follow our simple [Installation Guide](https://appwrite.io/docs/installation) to get Appwrite up and running in no time. You can either deploy Appwrite on your local machine or, on any cloud provider of your choice. 

> Note: If you setup Appwrite on your local machine, you will need to create a public IP so that your hosted frontend can access it.
  
We need to make a few configuration changes to your Appwrite server. 



### 🚀 Deploy the Front End
You have two options to deploy the front-end and we will cover both of them here. In either case, you will need to fill in these environment variables that help your frontend connect to Appwrite.

* VITE_APP_ENDPOINT - Your Appwrite endpoint
* VITE_APP_PROJECT - Your Appwrite project ID
* VITE_APP_COLLECTION_ID - Your Appwrite collection ID 
* VITE_APP_DATABASE_ID - Your Appwrite database ID

### **Deploy to a Static Hosting Provider**

Use the following buttons to deploy to your favourite hosting provider in one click! We support Vercel, Netlify and DigitalOcean. You will need to enter the environment variables above when prompted.

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template/YMe32a?referralCode=Yh2rJK)


### **Run locally**

Follow these instructions to run the demo app locally

```sh
$ git clone https://github.com/appwrite/todo-with-vue
$ cd todo-with-vue
```

Run the following command to generate your `.env` vars  

```sh
$ cp .env.example .env
```

Now fill in the envrionment variables we discussed above in your `.env`

Now run the following commands and you should be good to go 💪🏼 
```
$ npm install
$ npm run dev
```
