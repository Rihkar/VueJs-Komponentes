<template>
  <div class="animal-toggle">
    <div class="form-check">
      <input
        @click="toggleView"
        class="form-check-input"
        type="checkbox"
        value=""
        id="flexCheckDefault"
      />
      <label class="form-check-label" for="flexCheckDefault">
        {{ viewMode === "all" ? "Show Cats" : "Show All" }}</label
      >
    </div>
  </div>
  <div class="input-container">
    <input v-model="inputValue" type="text" v-on:keyup.enter="addAnimal" />
    <select v-model="dogOrCat">
      <option value="DOG">DOG</option>
      <option value="CAT">CAT</option>
    </select>
    <button @click="addAnimal">ADD</button>
  </div>
  <div v-for="animal in animalsView" :key="animal.id" class="single-animal">
    <div>{{ animal.type }}</div>
    <div>{{ animal.name }}</div>
    <button @click="removeAnimal(animal.id)" class="btn-delete">x</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

type animalList = {
  name: string;
  type: string;
  id: number;
};

type ViewMode = "all" | "cats";

export default defineComponent({
  name: "HomeView",
  emits: ["addAnimal"],

  data() {
    return {
      viewMode: "all" as ViewMode,
      initialId: 0,
      inputValue: "",
      dogOrCat: "",
      outputValue: [] as animalList[],
    };
  },
  created() {
    this.outputValue = JSON.parse(localStorage.getItem("animals") || "[]");
  },
  watch: {
    animals(newAnimals) {
      localStorage.setItem("animals", JSON.stringify(newAnimals));
    },
  },
  computed: {
    animalsView() {
      if (this.viewMode === "cats") {
        return this.showCats;
      }

      return this.outputValue;
    },
    showCats() {
      console.log(this.outputValue);
      return this.outputValue.filter(({ type }) => type === "CAT");
    },
  },
  methods: {
    toggleView() {
      if (this.viewMode === "all") {
        this.viewMode = "cats";
      } else {
        this.viewMode = "all";
      }
    },
    addAnimal() {
      this.outputValue.push({
        name: this.inputValue,
        type: this.dogOrCat,
        id: this.initialId++,
      });
      this.inputValue = "";
    },
    submitHandler() {
      this.$emit("addAnimal", this.inputValue);

      this.inputValue = "";
    },
    removeAnimal(id: number) {
      this.outputValue = this.outputValue.filter((el) => el.id !== id);
    },
  },
});
</script>
