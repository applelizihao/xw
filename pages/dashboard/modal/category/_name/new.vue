<template>
  <div>
    <v-btn color="success" @click="createCategory">
      保存
    </v-btn>
  </div>
</template>
<script>
export default {
  name: '',
  middleware: 'authenticated',
  components: {},
  data () {
    return {
      loading: {
        reg: false
      }
    }
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {},
  methods: {
    createCategory () {
      this.loading.reg = true
      const url = '/api/v1/tree/create'
      const formData = new FormData()
      formData.append('name', 'vzcx')
      this.$axios
        .post(url, formData)
        .then((res) => {
          this.$toast.success('分类创建成功')
        })
        .finally(() => {
          this.loading.reg = false
        })
    }
  },
  head () {
    return {
      title: '登录',
      meta: [
        { hid: 'description', name: 'description', content: '登录页面' }
      ]
    }
  }
}
</script>
<style lang='scss' scoped>
</style>
