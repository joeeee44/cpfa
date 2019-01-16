<template>
  <section class="container">
    <div>
      <h1 class="title">
        cpfa
      </h1>
      <h2 class="subtitle">
        <p>Question{{ params }}</p>
        <p>{{ test.question }}</p>
        <p>Answer: {{ test.answer }}</p>
      </h2>

      <div>
        <label for="1">1</label>
        <input
          id="1"
          v-model="test.answer"
          type="radio"
          required
          value="1">
        <label for="2">2</label>
        <input
          id="2"
          v-model="test.answer"
          type="radio"
          value="2">
        <label for="3">3</label>
        <input
          id="3"
          v-model="test.answer"
          type="radio"
          value="3">
        <label for="4">4</label>
        <input
          id="4"
          v-model="test.answer"
          type="radio"
          value="4">
      </div>

      <div class="links">
        <template v-if="params !== '1'">
          <nuxt-link
            :to="{ name: 'tests-id', params: { id: prev } }"
            class="button--green"><font-awesome-icon :icon="['fas', 'arrow-circle-left']"/> Q {{ prev }}</nuxt-link>
        </template>
        <template v-if="params !== (tests.length).toString()">
          <nuxt-link
            :to="{ name: 'tests-id', params: { id: next } }"
            class="button--green">Q {{ next }} <font-awesome-icon :icon="['fas', 'arrow-circle-right']"/></nuxt-link>
        </template>
        <template v-if="params === (tests.length).toString()">
          <nuxt-link
            :to="{ name: 'tests-result', path: '/tests/result' }"
            class="button--green">result</nuxt-link>
        </template>
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
