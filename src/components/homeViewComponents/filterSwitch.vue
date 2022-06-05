<template>
  <div class="animal-toggle">
    <div class="form-check">
      <input
        class="form-check-input"
        type="checkbox"
        value=""
        id="flexCheckDefault"
      />
      <label class="form-check-label" for="flexCheckDefault"> SHOW </label>
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
export default defineComponent({
  name: "flexSwitchCheck",
  data() {
    return {
      greeting: "Hello World!",
    };
  },
});
</script>
