<template>
  <FlexboxLayout flexDirection="column">
    <SearchBar hint="Search..." />
    <ListView class="category-list" for="c in categories" @itemTap="tapItem">
      <v-template>
        <Label :text="c.title" class="category-item" />
      </v-template>
    </ListView>
  </FlexboxLayout>
</template>

<script>
export default {
  computed: {
    categories() {
      return [
        { title: '縣市', code: 'town', list: [] },
        { title: '類型', code: 'type', list: [] },
        { title: '售金', code: 'price', list: [] },
        { title: '格局', code: 'layout', list: [] },
        { title: '坪數', code: 'size', list: [] },
      ];
    },
  },

  methods: {
    tapItem(event) {
      console.log(`item：${event.item.code}`);
    },
  },
};
</script>

<style>
.category-list {
  border: 1px solid #777;
}

.category-item {
  height: 150px;
  padding: 50px;
}
</style>
