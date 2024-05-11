<template>
  <div>
    <h1>Vue To Do List</h1>
    <input type="text" v-model="newItem" @keyup.enter="addItem">
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <span :class="{ 'completed': item.completed }">{{ item.name }}</span>
        <button @click="toggleComplete(index)">{{ item.completed ? 'Undo' : 'Complete' }}</button>
        <button @click="removeItem(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: '',
      items: []
    }
  },
  methods: {
    addItem() {
      if (this.newItem.trim() !== '') {
        this.items.push({ name: this.newItem, completed: false });
        this.newItem = '';
      }
    },
    removeItem(index) {
      this.items.splice(index, 1);
    },
    toggleComplete(index) {
      this.items[index].completed = !this.items[index].completed;
    }
  }
}
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>

<style>
h1{
color: black;
}

body{
  background-color: rgb(13, 107, 189);
}
</style>




