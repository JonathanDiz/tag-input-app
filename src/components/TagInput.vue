<template>
  <div class="tag-input">
    <div v-for="(tag, index) in tags" :key="index" class="tag-item">
      {{ tag }}
      <button @click="removeTag(index)" class="tag-remove">x</button>
    </div>
    <input type="text" v-model="inputValue" @keydown.enter.prevent="addTag" class="tag-input-field" />
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      tags: [] as string[],
      inputValue: '' as string,
    };
  },
  methods: {
    addTag() {
      if (this.inputValue !== '') {
        this.tags.push(this.inputValue);
        this.inputValue = '';
      }
    },
    removeTag(index: number) {
      this.tags.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.tag-input {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
}

.tag-item {
  font: arial, sans-serif;
  color: black;
  font-weight: bold;
  display: flex;
  align-items: center;
  background-color: #e2e8f0;
  padding: 0.25rem 0.5rem;
  margin: 0.25rem;
}

.tag-input-field {
  background-color: white;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
  border: 1px solid #cbd5e0;
  margin-top: 0.25rem;
}
</style>
