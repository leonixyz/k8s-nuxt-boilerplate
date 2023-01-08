<template>
  <section class="section">
    <div class="columns is-mobile">
      <card
        v-for="item in items"
        :key="item.id"
        :title="item.title"
        :icon="item.icon"
      >
        {{ item?.descr }}
      </card>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'

export default {
  name: 'IndexPage',

  components: {
    Card
  },

  data: () => ({
    items: []
  }),

  async fetch () {
    this.items = await this.$axios.$get('/api/items')
  },

  // disable ssr for fetch() on this page
  fetchOnServer: false
}
</script>
