<script setup lang="ts">
</script>


<template>
  <div class="number-selector">
      <label class="number-label">{{name}}:</label>
      <div class="number-value">{{ v }}</div>
      <div class="button" @click="update(1)">+</div>
      <div class="button" @click="update(-1)">-</div>
  </div>
</template>


<style scoped>
.button:hover {
  background-color: aliceblue;
  color: black;
}

.button {
  background-color: darkslateblue;
  border: 1px solid whitesmoke;
  margin: 5px;
  text-align: center;
  min-width: 30px;
  user-select: none; /* Standard syntax */
}


.number-label {
  margin-right: 15px;
}

.number-value {
  min-width: 25px;
  text-align: center;
}

.number-selector {
  display: flex;
}

.input-items {
    display: flex;

}

</style>


<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({
  name: 'NumberSelector',
  props: {
    min: Number,
    max: Number,
    name: String,
    value: Number
  },
  data() {
      return {
        csvRes: {"__length__": 0},
        columns: 3,
        v: Number(this.value)
      }
  },
  methods: {
    update(x: number) {
      this.v = Number(this.v) + Number(x);
      if (this.v < Number(this.min)) {
        this.v = Number(this.min)
      }
      if (this.v > Number(this.max)) {
        this.v = Number(this.max)
      }
      this.$emit('change', this.v)
    },
  }
})
</script>
