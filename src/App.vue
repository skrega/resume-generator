<template>
  <div class="container column">
    <resume-form @block-added="addBlock"></resume-form>
    <app-resume :blocks="blocks"></app-resume>
  </div>
  <app-loader v-if="loading"></app-loader>
  <app-comments v-else
    :comments="comments"
    @load-comments="loadComments"
  ></app-comments>

</template>

<script>
import ResumeForm from "@/components/ResumeForm";
import AppResume from "@/components/AppResume";
import AppComments from "@/components/AppComments";
import AppLoader from "@/components/AppLoader";

export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {

    async loadComments() {
      this.loading = true
      const result = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await result.json()
      this.loading = false
    },
    addBlock(block){
      this.blocks.push(block)
    },
  },
  components: {AppLoader, AppResume, AppComments, ResumeForm}
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
