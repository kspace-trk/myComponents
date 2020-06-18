<template>
  <div>
    <div class="container">
      <myHeader1 />
      <myHeader2 />
    </div>
  </div>
</template>

<script>
import myHeader1 from "~/components/myHeader1.vue";
import myHeader2 from "~/components/myHeader2.vue";

export default {
  components: {
    myHeader1,
    myHeader2
  }
};
</script>

<style scoped>
.container {
  height: 100vh;
  background-color: #e7e7e7;
}
</style>
