<template>
  <li>
    <template v-if="isEditing">
      <input type="text" v-model="newValue">
      <button @click="onApplyClick">apply</button>
    </template>
    <template v-else>
      {{task}}
      <button @click="isEditing=true">edit</button>
      <button class="delete" @click="$emit('delete')">delete</button>
    </template>
  </li>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    task: String
  },
  data() {
    return {
      isEditing: false,
      newValue: this.task,
    }
  },
  methods: {
    onApplyClick() {
      this.$emit('apply', this.newValue);
      this.isEditing = false;
    }
  }
}
</script>

<style scoped>
li {
  width: 300px;
  color: black;
  font-size: 30px;
  cursor: pointer;
  border: 1px solid black;
  padding: 20px;
  margin: 10px;
  border-radius: 10px;
  text-align: center;
}
input {
  display: block;
  width: 100%;
  font-size: 20px;
  text-align: center;
}
button {
  display: block;
  background: green;
  border-radius: 5px;
  width: 100%;
  margin: 10px 0;
  padding: 2px;
  cursor: pointer;
  color: white;
}
.delete {
  background: red;
}
</style>
