<template>
    <div v-if="!blocks.length">
        <h3>Добавьте первый блок, чтобы увидеть результат</h3>
    </div>
    <div>
        <component
    v-for="block in blocks"
    :key="block.id"
    :is="'resume-' + block.type"
    v-bind="{value: block.value}"
></component>
    </div>
</template>

<script>
    import ResumeTitle from './resumeParts/ResumeTitle.vue'
    import ResumeSubtitle from './resumeParts/ResumeSubtitle.vue'
    import ResumeAvatar from './resumeParts/ResumeAvatar.vue'
    import ResumeText from './resumeParts/ResumeText.vue'   
    export default {

        props: ['blocks'],
       components: {
      ResumeTitle,
      ResumeSubtitle,
      ResumeAvatar,
      ResumeText,
    }, 
    }
    
</script>

<style lang="scss" scoped>

</style>