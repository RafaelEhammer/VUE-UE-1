<template>
  <div id="app">
    <h3>Example</h3>
    <form @submit.prevent="addNew">
      <label>Enter new subject:</label>
      <input v-model="newSubject" />
      <button>Add subject</button>
      <hr />
    </form>
    <ul>
      <li v-for="(item, index) in subjectArray">
        {{ item.content }}
        <button @click="deleteItem(item)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import { ref } from 'vue';

export default {
  setup() {
    const newSubject = ref('');
    const subjectArray = ref([]);
    let id = 0;

    function addNew() {
      console.log('addNew...');
      subjectArray.value.push({
        content: newSubject.value,
        iid: id,
      });
      console.log(subjectArray.value);
      id++;
    }

    function deleteItem(item) {
      console.log(subjectArray.value[0].content);
      for (let i = 0; i < subjectArray.value.length; i++) {
        if (subjectArray.value[i].iid === item.iid) {
          subjectArray.value.splice(i, 1);
          return;
        }
      }
    }

    return {
      newSubject,
      subjectArray,
      addNew,
      deleteItem,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
