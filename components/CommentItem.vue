<template>
  <div class="comment-item">
    <strong>{{ username }}</strong>
    <p>{{ comment }}</p>
    <small class="comment-date">{{ date }}</small>
  </div>
</template>

<script>
export default {
  name: 'CommentItem',
  props: {
    username: {
      type: String,
      required: true
    },
    comment: {
      type: String,
      required: true
    },
    date: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped>
.comment-item {
  border: 1px solid #ddd;
  padding: 10px;
  margin: 5px 0;
  border-radius: 4px;
  background-color: #be29ec;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}
.comment-date {
  color: #dbdbdb;
  font-size: 0.9rem;
}
</style>