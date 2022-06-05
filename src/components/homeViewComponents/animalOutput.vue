<template>
  <div v-for="animal in animalsView" :key="animal" class="single-animal">
    <div>{{ animal.type }}</div>
    <div>{{ animal.name }}</div>
    <button @click="removeAnimal(animal.id)" class="btn-delete">x</button>
  </div>
</template>

<script>
import { defineComponent } from "vue";
export default defineComponent({
  name: "animalOutput",
  data() {
    return {
      greeting: "Hello World!",
    };
  },
  methods: {
    removeAnimal(id) {
      this.outputValue = this.outputValue.filter((el) => el.id !== id);
    },
  },
});
</script>
