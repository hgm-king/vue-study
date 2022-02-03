<template>
  <div class="input-engine-wrapper">
    <button @click="prev">&lt;</button>
    {{activeItem}} / {{ToDoItems.length}}
    <button @click="next">&gt;</button>
    <form @submit.prevent="onSubmit">
      <label>{{ToDoItems[activeItem-1].label}}</label>
      <input name="questions" @input="onInput" :value=ToDoItems[activeItem-1].answer>
    </form>
  </div>
</template>

<script>
export default {
  name: 'InputEngine',
  data() {
    return {
      activeItem: 1,
      ToDoItems: [
        { id: 1, label: '1. How Are You?', answer: '' },
        { id: 2, label: '2. How Are You?', answer: '' },
        { id: 3, label: '3. How Are You?', answer: '' },
        { id: 4, label: '4. How Are You?', answer: '' }
      ]
    };
  },
  methods: {
    onInput(words) {
      this.ToDoItems[this.activeItem-1].answer = words.target.value;
    },
    next() {
      this.activeItem += this.activeItem < this.ToDoItems.length ? 1 : 0
    },
    prev() {
      this.activeItem -= this.activeItem > 1 ? 1 : 0
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
