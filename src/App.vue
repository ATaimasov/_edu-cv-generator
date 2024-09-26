<template>
  <div class="container column">
    <ResumeForm @addInfo="addInfo" />

    <div class="card card-w70">
    <ResumeView :blocks="blocks" />
    </div>
  </div>

  <app-loader v-if="loading"></app-loader>
  <app-comments 
  :comments="comments" 
  v-else
  @load-comments="loadComments"
  
  ></app-comments>



</template>

<script>
import ResumeView from './components/ResumeView.vue'
import ResumeForm from './components/ResumeForm.vue'
import AppLoader from './components/AppLoader.vue'
import AppComments from './components/AppComments.vue'

export default {
    data() {
        return {
          blocks: [],
          comments: [],
          loading: false,
        }
    },
    methods: {
      addInfo(block) {
        console.log(block)

        this.blocks.push(block)
        console.log(this.blocks)
      },
      async loadComments() {
        console.log('loadComments')
        this.loading = true
        const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
        const data = await response.json()
        this.comments = data
        this.loading = false
      }
    },
    components: {
      ResumeView,
      ResumeForm,
      AppLoader,
      AppComments
    },
    
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
