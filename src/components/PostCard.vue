<template>
   <div class="post-card">
      <h3 class="text-title">{{ post.title }}</h3>
      <formatted-date-time :date-time-string="post.created_at"></formatted-date-time>
      <p class="text-content">{{ post.content }}</p>
   </div>
</template>

<script>
import FormattedDateTime from './FormattedDateTime.vue';

export default {
   props: {
      post: {
         type: Object,
         required: true,
      },
   },
   components: {
      FormattedDateTime
   }
}
</script>

<style>
.post-card {
   border: 1px solid gray;
   border-radius: 5px;
   padding: 20px;
   margin: 10px;
}

.text-muted {
   color: gray;
}

.texty-content {
   white-space: nowrap;
   overflow: hidden;
   text-overflow: ellipsis;
}
</style>