<template>
  <section class="container">
    <div>
      <h1 class="title">
        result
      </h1>

      <div class="links">
        <nuxt-link
          :to="{ name: 'tests-result-c', params: 'result-c' }"
          class="links--item">C {{ c }} %</nuxt-link>
        <nuxt-link
          :to="{ name: 'tests-result-p', params: 'result-p' }"
          class="links--item">P {{ p }} %</nuxt-link>
        <nuxt-link
          :to="{ name: 'tests-result-f', params: 'result-f' }"
          class="links--item">F {{ f }} %</nuxt-link>
        <nuxt-link
          :to="{ name: 'tests-result-a', params: 'result-a' }"
          class="links--item">A {{ a }} %</nuxt-link>
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

    r1() {
      return this.$store.state.tests.r1
    },

    c() {
      return this.$store.state.tests.c
    },

    p() {
      return this.$store.state.tests.p
    },

    f() {
      return this.$store.state.tests.f
    },

    a() {
      return this.$store.state.tests.a
    }
  },
  methods: {
    calculation() {
      console.log('Calculation')
      this.$store.state.tests.r1 =
        Number(this.$store.state.tests.list[39 - 1].answer) +
        Number(this.$store.state.tests.list[40 - 1].answer)
    }
  },
  beforeRouteEnter(to, from, next) {
    next(vm => {
      vm.calculation()
    })
  }
}
</script>

<style lang="scss" scoped>
.container {
  height: 100vh;
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
  display: flex;
  flex-flow: row wrap;
  height: calc(100vh - 118px);
  overflow: hidden;
  .links--item {
    width: 50vw;
    height: calc(50vh - 67px);
    border: 1px solid #ccc;
    text-decoration: none;
    padding-top: calc(calc(50vh - 67px) / 2);
    font-size: 30px;
    font-weight: bold;
    color: #35495e;
    /* transition: all 0.5s ease-in-out 0s; */
    &:hover {
      background: #35495e;
      color: #fff;
    }
  }
}
</style>
