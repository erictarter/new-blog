<script setup lang="ts">
  import { ref } from 'vue'
  import BlogImage from './utilities/BlogImage.vue'
  import CodeSnippet from './utilities/CodeSnippet.vue'

  const toggleExample = ref(false)

  const part1 = ref<HTMLElement | null>(null)
  const part2 = ref<HTMLElement | null>(null)

  function exampleToggle() {
    toggleExample.value = !toggleExample.value
  }

  function scrollPart1() {
    part1.value?.scrollIntoView({ behavior: 'smooth' })
  }
  function scrollPart2() {
    part2.value?.scrollIntoView({ behavior: 'smooth' })
  }
</script>
<template>
  <div class="blog-main blog-container">
    <div class="blog">
      <div class="blog-links mb-4 d-flex">
        <span @click="scrollPart1" class="mx-1">Smooth Scrolling React</span>
        <span @click="scrollPart2" class="mx-1">Centering A Div</span>
      </div>
      <h2 ref="part1">Smooth Scrolling React</h2>
      <p>
        While not essential, smooth scrolling is a delightful feature to enhance
        the user experience on web pages with internal links. This web page
        utilizes smooth scrolling to provide a seamless navigation experience.
        Traditionally, implementing smooth scrolling involves using jQuery,
        which requires importing the jQuery plugin, setting up jQuery classes,
        writing JavaScript functions for those classes, and applying them to
        HTML links. While this approach works well, there is a simpler
        alternative called react-scroll. React-scroll offers a straightforward
        solution without the need for jQuery, making the implementation process
        much simpler and more streamlined.
      </p>
      <p>
        First, install react-scroll. Go to your terminal and run this command.
      </p>
      <CodeSnippet lang="" code="npm i -S react-scroll" />
      <p>
        Next import the react-scroll package. Put the following code at the top
        of the react JS file.
      </p>
      <CodeSnippet
        lang="js"
        code="import { Link, animateScroll as scroll } from 'react-scroll';" />
      <p>Instead of using an anchor tag, use a react Link Component.</p>
      <CodeSnippet
        lang="js"
        code="<Link
activeClass='active'
to='link-1'
spy={true}
smooth={true}
offset={-70}
duration={500}
>
This is the link
</Link>" />
      <p>
        Set the to property to the ID of the element you want to link to. That's
        all it takes to implement smooth scrolling in react.
      </p>
      <h2 ref="part2">Centering A Div</h2>
      <p>
        Even something as seemingly simple as centering an item can sometimes be
        frustrating. However, there are a few straightforward ways to achieve
        it. If the parent element has its display property set to grid, you can
        easily center an item by applying the appropriate grid properties. Let
        me show you how.
      </p>
      <p>In CSS grid, centering grid items can be done in one line.</p>
      <CodeSnippet lang="css" code="place-items: center;" />
      <p>
        Let me provide you with an example to illustrate how it works. I have
        created a 3D cube, which is contained within a parent element
        highlighted by a salmon-colored border. The parent element has a class
        named '.square', while the cube itself has a class named '.cube'. First,
        I will show you the CSS code, followed by the cube's appearance before
        applying the 'place-items' property.
      </p>
      <CodeSnippet
        lang="css"
        code=".square {
width: 30rem;
height: 30rem;
border: 1px solid salmon;
display: grid;
}
.cube {
width: 20rem;
height: 20rem;
color: #FFF
}" />
      <BlogImage
        url="https://github.com/erictarter/my-blog/blob/main/src/img/Screen%20Shot%202020-12-11%20at%2010.58.36%20AM.png?raw=true" />
      <p>Now lets add the place-items property to center the cube.</p>
      <CodeSnippet
        lang="css"
        code=".square {
width: 30rem;
height: 30rem;
border: 1px solid salmon;
display: grid;
place-items: center; <====
}" />
      <BlogImage
        url="https://github.com/erictarter/my-blog/blob/main/src/img/Screen%20Shot%202020-12-11%20at%2010.59.13%20AM.png?raw=true" />
      <p>
        Let's explore the concept of flexbox. By default, the 'flex-direction'
        property is set to 'row'. To center flex items in a row, we need to set
        two properties: 'align-items' and 'justify-content'. Setting both of
        these properties to 'center' achieves vertical and horizontal centering
        respectively. Below, you'll find a flex container with three circles
        (flex items) inside it. Clicking the button below will apply the two
        properties to the container, resulting in centered alignment.
      </p>
      <button @click="exampleToggle" v-if="!toggleExample">Center</button>
      <button @click="exampleToggle" v-if="toggleExample">Undo</button>
      <div
        :class="
          toggleExample
            ? 'example d-flex align-items-center justify-content-center mt-3'
            : 'example d-flex mt-3'
        ">
        <span>!!! CENTER ME !!!</span>
      </div>
      <p>
        If the 'flex-direction' property is set to 'column', the centering
        properties work differently. To horizontally center the flex items, you
        need to set the 'justify-items' property to 'center'. On the other hand,
        to vertically center the items, you should set the 'align-content'
        property to 'center'. It can be confusing because these four properties
        have similar names, but their functionality differs depending on the
        flex direction.
      </p>
    </div>
  </div>
</template>

<style scoped lang="scss">
  p {
    margin: 2em 0;
    line-height: 1.75;
  }
  button {
    border-radius: 4px;
    background-color: #829f9e;
    border: none;
    padding: 4px 10px;
    color: #fff;
  }

  .example {
    border: 1px solid #333;
    padding: 2em;

    span {
      background-color: pink;
      color: white;
      padding: 4px;
      border-radius: 8px;
    }
  }
</style>
