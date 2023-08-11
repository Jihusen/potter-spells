<script setup>
  import { ref } from 'vue';
  //import '../scss/main.scss';

  const blnCardView = ref(true);
  const spellData = ref(null);

  async function toggle() {
    blnCardView.value = !blnCardView.value;
    spellData.value = null;
    const res = await fetch(
      'https://www.potterapi.com/v1/spells?key=$2a$10$PlL30eUznCdeELwR/jfA1uMbI30nBrujfMSrd62NiFhAyddoWvn0a'
    )
    spellData.value = await res.json();
  }
</script>

<template>
  <div>
    <CardView v-if="blnCardView" ></CardView>
    <ListView v-else></ListView>

    <button @click="blnCardView = !blnCardView">toggle</button>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
}

</script>


<!-- <template>
  <h1>Here is a list of the Harry Potter Spells</h1>
</template>


<script>
export default {
  name: 'IndexPage',
}
// Use a promise to get the api call from the Postman Harry Potter API
// Use the v-bind to fill the list with the names of the spells
// See if you can get the description of the spell to appear on hover maybe in a tool tip or in its own thing. 
// Once the above is done make it so you can use flexbox or display grid to arrange the list a certain way

// Create separate page do show the spells a different way
// create cards for the spells, shows the name and description in a certain format
// Play around with Vue animations to have the cards move or do fun things

// have the previous two sections be their own component
// on index file have a button that will use v-show

</script> -->
