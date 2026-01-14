<!-- <script>

export default {
  data() {
    return {
      name: 'Natan Pereira',
      status: true,
      tasks: ['Task One', 'Task Two', 'Task Three'],
      link: 'https://google.com',
    };
  },
  methods: {
    changeStatus(){
      if(this.status){
        this.status = false;
      }
      else{
        this.status = true;
      }
    }
  }
}

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">Status ok</p>
  <p v-else>Status no ok</p>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a v-bind:href="link">Click for google</a>
  <br>
  <button @click="changeStatus">Change</button>
</template>
 -->
