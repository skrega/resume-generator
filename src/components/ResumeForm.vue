<template>
  <form class="card card-w30" @submit.prevent="createResume">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="typeBlock">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model="contentBlock"></textarea>
    </div>

    <button class="btn primary" :disabled="contentBlock.length <=  3">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: ['block-added'],
  data() {
    return {
      typeBlock: 'title',
      contentBlock: ''
    }
  },
  methods: {
    createResume() {
      this.$emit('block-added', {
        typeBlock: this.typeBlock,
        contentBlock: this.contentBlock,
        id: Date.now()
      })
      this.typeBlock = 'title'
      this.contentBlock = ''
    }
  },
}
</script>

<style scoped>

</style>
