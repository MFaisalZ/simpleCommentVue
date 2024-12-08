<template>
  <div id="app">
    <comment-list />
  </div>
</template>

<script>
import CommentList from './components/CommentList.vue';

export default {
  name: 'App',
  components: {
    CommentList
  }
};
</script>

<style src="./assets/styles.css"></style>
