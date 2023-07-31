<script setup lang="ts">
  import { ref } from 'vue'
  import BlogImage from './utilities/BlogImage.vue'
  import CodeSnippet from './utilities/CodeSnippet.vue'
  import Credit from './Credit.vue';

  const part1 = ref<HTMLElement | null>(null)
  const part2 = ref<HTMLElement | null>(null)
  const part3 = ref<HTMLElement | null>(null)

  function scrollPart1() {
    part1.value?.scrollIntoView({ behavior: 'smooth' })
  }
  function scrollPart2() {
    part2.value?.scrollIntoView({ behavior: 'smooth' })
  }
  function scrollPart3() {
    part3.value?.scrollIntoView({ behavior: 'smooth' })
  }
</script>
<template>
  <div class="blog-main blog-container">
    <div class="blog">
      <div class="blog-links mb-4 d-flex">
        <span @click="scrollPart1" class="mx-1">Setup</span>
        <span @click="scrollPart2" class="mx-1">Create Server</span>
        <span @click="scrollPart3" class="mx-1">Deploy</span>
      </div>
      <p>
        Node.js is a server-side JavaScript environment that allows developers to run JavaScript code on the server rather than just in the browser. Here will explain the simplest way to set up a counter incrementer server.
      </p>
      <h2 ref="part1">Setup</h2>
      <p>
        To implement a Node.js Express server and maintain a counter, you'll need to set up a simple API endpoint from the front-end app to increment/decrement and update the counter accordingly.
      </p>
      <p>
        Create a new directory for your project and initialize a Node.js project using npm or yarn.
      </p>
      <CodeSnippet lang="" code="npm init" />
      <p>Install Express to create the server.</p>
      <CodeSnippet lang="" code="npm install express" />
      <h2 class="mt-5" ref="part2">Create Server</h2>
      <p>In the root of the project, create a file that will contain the express server code. Call it server.js or index.js</p>
      <p>In the server.js lets import express, and use it. Lets also use bodyParser to parse JSON data from the request body.</p>
      <CodeSnippet
        lang="server.js"
        code="const express = require('express');
const app = express();
const bodyParser = require('body-parser'); 

app.use(bodyParser.json());" />
      <p>Now lets try to start the server. Add in this code and run the command node server.js in the terminal</p>
      <CodeSnippet  lang="server.js" code="const port = 3000; // You can change this to any desired port number
app.listen(port, () => {
  console.log(`Server is running on ${port}`);
});"/>
      <p>You will see the console log if the server is running successfully.</p>  
      <p>Next we will need to initialize a counter variable.</p>
      <CodeSnippet lang="server.js" code="let counter = 0;" />
      <p>Create end point to update the counter.</p>
      <CodeSnippet lang="server.js" code="app.get('/increment', (req, res) => {
  counter++
  res.json({ vueCounter })
})"/>
      <p>Add another end point to subtract from the counter if you'd like.</p>
      <p>In your front end app, you can make requests to this end point to update the counter. Here is a simple Vue template that will work for this. We will use axios to make requests.</p>
      <CodeSnippet lang="vue" code="<script setup lang='ts'
      import { ref } from 'vue'
      import axios from 'axios'

      const counter = ref(0);
      
      function increment (){
        axios
      .get('https //localhost:3000/increment')
      .then((response: any) => {
        counter.value = response.data.counter
      }
    </script>
    <template>
        <div class='counter-app'>
            <button @click='increment'>add</button>
            <span>{{ counter }}</span>
        </div>    
    </template>    
      "
      />
      <p>Test it out and see if it works. Make sure the server is running and are making the request to the correct url. That's it!</p>
<h2 class="mt-5" ref="part2">Deploy</h2>
    </div>
    <p>There are several user-friendly hosting platforms that make it easy to deploy and manage web applications, including Node.js apps. Here are some simple and popular hosting </p>
    <div class="blog-links mb-4 d-flex">
        <a target="_blank" href="https://id.heroku.com/login" class="mx-1">Heroku</a>
        <a target="_blank" href="https://vercel.com/" class="mx-1">Vercel</a>
        <a target="_blank" href="https://www.netlify.com/" class="mx-1">Netlify</a>
    </div>
    <p>Make sure to switch to the correct url in the front-end given from the hosting platform after deploying.</p>
    <Credit />
  </div>
</template>

<style scoped lang="scss">
  p {
    margin: 2em 0;
    line-height: 1.75;
  }
  a {
    color: #527570;
    transition: 0.2s ease all;
    text-decoration: underline;
    cursor: pointer;
  }
  a:hover {
    color: #465b57;
    transition: 0.2s ease all;
  }
</style>
