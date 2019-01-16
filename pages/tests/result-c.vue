<template>
  <section class="container">
    <div>
      <h1 class="title">
        result-c
      </h1>

      <div class="links">
        <nuxt-link
          :to="{ name: 'tests-result', params: 'result' }"
          class="button--green">result</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {}
  },
  computed: {
    params() {
      return this.$route.params.id
    },

    tests() {
      return this.$store.state.tests.list
    },

    test() {
      return this.tests.filter(test => {
        return test.id === Number(this.params)
      })[0]
    },

    next() {
      return (Number(this.params) + 1).toString()
    },

    prev() {
      return (Number(this.params) - 1).toString()
    }
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
