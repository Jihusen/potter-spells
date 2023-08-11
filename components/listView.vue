<script setup>
import { ref, onMounted } from 'vue'
const spellData = ref(null)

onMounted(async () => {
  console.log("Entered onMounted");
  spellData.value = null
  const res = await fetch(
    'https://hp-api.onrender.com/api/spells'
  )
  console.log(res);
  spellData.value = await res.json()
  console.log(spellData.value);
})
</script>

<template>
  <p v-if="!spellData">Conjuring...</p>
  <!-- <pre v-else>{{ spellData }}</pre> -->
  <ul v-else id="spellList">
    <li v-for="spell in spellData" :key="spell.id">
        <div>
            {{ spell.name }}
        </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'ListView',
}
</script>
