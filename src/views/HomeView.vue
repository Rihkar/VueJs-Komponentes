<template>
  <!-- <filterSwitch></filterSwitch> -->
  <animalInput></animalInput>
  <!-- <animalOutput></animalOutput> -->
</template>

<script lang="ts">
import { defineComponent } from "vue";
// import filterSwitch from "@/components/homeViewComponents/filterSwitch.vue";
import animalInput from "@/components/homeViewComponents/animalInput.vue";
// import animalOutput from "@/components/homeViewComponents/animalOutput.vue";

export default defineComponent({
  name: "HomeView",
  components: {
    // filterSwitch,
    animalInput,
    // animalOutput,
  },
});
</script>
