<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component v-for="block in blocks" :key="block.id"
        :is="'resume-' + block.typeBlock"
        v-bind="{value: block.contentBlock}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from './parts/ResumeTitle'
import ResumeSubtitle from './parts/ResumeSubtitle'
import ResumeAvatar from './parts/ResumeAvatar'
import ResumeText from './parts/ResumeText'
export default {
  props: ['blocks'],
  components: {
    ResumeTitle,
    ResumeText,
    ResumeSubtitle,
    ResumeAvatar
  }
}
</script>
<style scoped lang="scss">

</style>
