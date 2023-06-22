<script setup lang="ts">
  import { ref } from 'vue'
  import BlogImage from './utilities/BlogImage.vue'
  import CodeSnippet from './utilities/CodeSnippet.vue'

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
        <span @click="scrollPart1" class="mx-1">Styling</span>
        <span @click="scrollPart2" class="mx-1">Trigger Sounds</span>
        <span @click="scrollPart3" class="mx-1">Options/Features</span>
      </div>
      <p>
        Creating the Piano Project using
        <span class="highlight-text">Tone.js</span>, a web audio framework, was
        an enjoyable and straightforward experience. This application serves as
        an educational tool, providing users with a solid foundation in piano
        fundamentals. It offers the ability to visualize and listen to major
        scales and chords. Simply clicking on any note produces its
        corresponding sound. Additionally, users can play notes and chords using
        their laptop keyboard. The app provides various sound effects and allows
        for customization of note durations, enhancing the overall experience.
      </p>
      <h2 ref="part1">Styling</h2>
      <p>
        To design the piano, I opted for a grid-based approach. The piano
        container is displayed as a grid, with the grid-template-columns
        property set to (1fr, 1.3fr, 1fr, 1.3fr, 1fr). This configuration spans
        the entire length of the keyboard. Each 1fr unit accommodates three
        white notes and two black notes within it. Similarly, each 1.3fr unit
        accommodates four white notes and three black notes within it. The black
        frame of the piano is created using a border, with the left and right
        borders set to 3rem solid black, and the top border set to a thick 5rem.
        Each of these grid items also utilizes a grid display. For the items
        with three white notes, the grid-template-columns property is set to
        repeat(3, 1fr). As for the highlighted item in the image below, the
        grid-template-columns property is set to repeat(4, 1fr), which evenly
        spaces out the white notes.
      </p>
      <BlogImage
        url="https://github.com/erictarter/my-blog/blob/main/src/img/Screen%20Shot%202020-12-06%20at%202.35.05%20PM.png?raw=true" />
      <p>
        Regarding the black notes, their positioning is set to absolute, while
        each parent div element is set to relative. This approach ensures that
        the black notes are not part of the grid structure but instead placed
        inside the corresponding elements. To handle the black notes, five
        classes are required, each with a different left position. Here is an
        example of one of these classes:
      </p>
      <CodeSnippet
        class="mb-5"
        lang="css"
        code=".black-1 {
          position: absolute;
          left: 24.5%;
          width: 14%;
          height: 6rem;
          background: black;
          border: 3.5px solid grey;
          border-bottom-color: rgb(52, 52, 52);
          border-top-color: white;
        }" />
      <h2 ref="part2">Triggering Piano Sounds</h2>
      <p>
        First let's bring in the
        <span class="highlight-text">Tone JS</span> framework. To do this, go
        into your terminal and use this command.
      </p>
      <CodeSnippet lang="" code="npm install tone" />
      <p>
        To bring in a sound, create an object, and choose the sound. In the
        below example. We create a sampler instance which is a piano sound.
      </p>
      <CodeSnippet
        lang="js"
        code="const piano = new Tone.Sampler().toDestination();" />
      <p>
        To trigger a sound, use this function called triggerAttackRelease. This
        takes two arguments. First is the note you want to get played. The
        second is the duration of the note. To play middle C(middle note on a
        piano), This would get called. Using the instance example above.
      </p>
      <CodeSnippet lang="js" code='piano.triggerAttackRelease("C3", "8n");' />
      <p>
        In this app, there are four ways to trigger the
        <span class="highlight-text">Tone JS</span> to make a sound.
      </p>
      <ol>
        <li>Clicking on notes.</li>
        <li>Keydown events.</li>
        <li>Selecting a chord.</li>
        <li>Selecting a scale.</li>
      </ol>
      <p>
        To enable sound when clicking on notes, we can follow these steps.
        Firstly, we need to select all the white notes in the
        <span class="highlight-text">DOM</span>. We can achieve this by using
        the querySelectorAll method, which returns a node list containing all
        the matching elements. Next, we can iterate through the node list using
        the forEach method to perform actions on each white note. Similarly, we
        can target the black notes using the same approach.
      </p>
      <CodeSnippet
        lang="js"
        code='const whiteNotes = document.querySelectorAll (".white"); 
    const blackNotes = document.querySelectorAll (".black");' />
      <p>Here is a part of what the piano HTML looks like.</p>
      <CodeSnippet
        lang="js"
        code='<div class="c3-e3">
      <div class="white" id="c3"></div>
      <div class="black-1 black" id="c#3"></div>
      <div class="white" id="d3"></div>
      <div class="black-2 black" id="d#3"></div>
      <div class="white" id="e3"></div>
      </div>' />
      <p>
        Each note in these node lists has a specific ID. The ID is the first
        argument when the triggerAttckRelease gets called. The second argument
        is whatever gets selected by the user(duration selection in the top
        right of the screen).
      </p>
      <CodeSnippet
        lang="js"
        code="whiteNotes.forEach(wn => {
wn.addEventListener('click', async e => {
let note = e.target.id.toUpperCase();
await Tone.start();
sound.triggerAttackRelease (note, duration);
});
});
    " />
      <p>
        When Tone gets triggered by an event listener(click or keydown),
        Tone.start() returns a promise. Resulting in audio only when the promise
        is resolved.
      </p>
      <p>
        Our next objective is to utilize the computer keyboard as a musical
        instrument. Each keyboard character on the window object is associated
        with a unique key code. To organize these key codes, I have created an
        object where the keys correspond to the key codes, and the values
        represent the ID of a specific note. When a key is pressed down, a
        keydown event will trigger the same triggerAttackRelease function, but
        with a different first argument, which corresponds to the note ID.
      </p>
      <CodeSnippet
        lang="js"
        code="window.addEventListener ('keydown', async e => {
await Tone.start();
fetch('keyCodes.json')
.then(response => response.json())
.then(data => {
sound.triggerAttackRelease (data[e.keyCode], duration);
});
});" />
      <p>
        When a major chord is selected, it will trigger the playback of the
        corresponding chord. Additionally, the piano keys associated with the
        notes of the chord will be highlighted. The event that is being listened
        for in this selection process is the change event.
      </p>
      <CodeSnippet
        lang="js"
        code="chordsSelect.addEventListener ('change', async e => {
await Tone.start();" />
      <p>
        We have a list of chord objects where the keys represent the name of the
        chord (e.g., "G") and the values contain a list of the notes in that
        chord (e.g., ["G", "B", "D"]). To retrieve the desired notes, we will
        iterate through these chords using a loop. The following code snippet is
        within the scope of the previous snippet.
      </p>
      <CodeSnippet
        lang="js"
        code="let notes = [];
playChords.map(i => {
if (i[e.target.value]) { // FIND CHORD SELECTED
i[e.target.value].map(n => { // GET NOTES IN CHORD
notes.push(n);
});
});" />
      <p>
        Now that we have the notes, let's trigger the sound and highlight the
        corresponding piano keys. To create a spread-out effect for playing the
        notes, we can utilize the setTimeout method. (The code snippet below is
        still within the function's scope).
      </p>
      <CodeSnippet
        lang="js"
        code="sound.triggerAttackRelease (notes[0], duration);
document.getElementById (notes[0].id).style.background = 'rgb(255, 214, 138)';

setTimeout(() => {
sound.triggerAttackRelease (notes[1], duration);
document.getElementById (notes[1].id).style.background = 'rgb(255, 214, 138)';
}, 100);
setTimeout(() => {
sound.triggerAttackRelease (notes[2], duration);
document.getElementById (notes[2].id).style.background = 'rgb(255, 214, 138)';
}, 200);
});" />
      <p>
        We don't need to delve into the scale select functionality as it works
        similarly to the chords. However, there are two key differences between
        scales and chords. First, scales have more notes to trigger, typically 8
        instead of 3. Second, the setTimeout intervals between the notes are
        longer, usually 200/1000 of a second instead of 100/1000 of a second.
      </p>
      <h2 ref="part3">Options/Features</h2>
      <p>
        In this app, you have the option to choose from four different sounds.
        The default and highest-quality sound is the piano, which provides the
        best auditory experience. However, I've also included three additional
        sounds to add variety. These sounds are imported from the Tone JS
        library.
      </p>
      <CodeSnippet
        lang="js"
        code="const synth = new Tone.Synth().toDestination();
const synthA = new Tone.FMSynth().toDestination();
const synthB = new Tone.AMSynth().toDestination();
const piano = new Tone.Sampler().toDestination();" />
      <p>
        We have a global variable called sound that gets used whenever a note is
        triggered
      </p>
      <CodeSnippet lang="js" code="let sound = piano;" />
      <p>
        Changing the sound effect is very easy. When the sound gets selected, it
        is listening for change. This will set the sound variable to what gets
        selected. In this scenario, I used a switch statement.
      </p>
      <CodeSnippet
        lang="js"
        code="soundSelect.addEventListener ('change', e => {
switch (e.target.value) {
case 'piano':
sound = piano;
break;
case 'synth':
sound = synth;
break;
case 'voilin':
sound = synthA;
break;
case 'synth-alt':
sound = synthB;
break;
default:
sound = piano;
}
});" />
      <p>
        Another option available in this app is the ability to change the
        duration of notes. There are five different durations to choose from,
        with the default set to an 8th note. To handle this functionality, we
        have a global variable called 'duration' that changes whenever a
        different duration is selected. When the 'triggerAttackRelease()'
        function is called, this 'duration' variable is used as the second
        argument, allowing us to control the length of the notes.
      </p>
      <CodeSnippet lang="ts" code="let duration = '8n';" />
      <p>This variable is changed the same way as the sound variable.</p>
      <h2>End</h2>
      <p>
        This project was an enjoyable and engaging endeavor, allowing me to
        explore and play around with the keyboard. I have also kept the option
        open to add more features in the future. One potential idea is to
        program a song playback functionality. Additionally, there is room for
        improvement in terms of the mobile user experience, as the keys are
        currently too small to be easily played. Thank you for taking the time
        to read about my project!
      </p>
    </div>
  </div>
</template>

<style scoped lang="scss">
  p {
    margin: 2em 0;
    line-height: 1.75;
  }
  li {
    text-align: start;
  }
</style>
