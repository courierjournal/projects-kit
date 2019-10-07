<template>
  <div>
      Here's a data list:
    <ul>
      <li v-for="(item, index) in listData" :key="index">{{item}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["listData"]
};
</script>
