<template>
        <div class="container card" v-if="comments.length">
         <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item"
        v-for="comment in comments"
        :key="comment.id"
        >
          <div>
            <p><strong>{{comment.email}}</strong></p>
            <small>{{comment.body}}</small>
          </div>
        </li>
      </ul>
    </div>

      <div class="container" v-else>
    <p>
      <button class="btn primary" @click="$emit('load-comments')">Загрузить комментарии</button>
    </p>
    
  </div>
</template>

<script>
    export default {
        props: ['comments'],
    }
</script>

<style lang="scss" scoped>

</style>