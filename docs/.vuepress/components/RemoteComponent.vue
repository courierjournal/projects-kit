<template>
  <ul>
    <li v-for="(item, index) in items" :key="index">{{item.email}}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: []
    };
  },
  beforeMount() {
    fetch("https://reqres.in/api/users")
      .then(res => res.json())
      .then(data => {
        this.items = data.data;
      });
  }
};
</script>