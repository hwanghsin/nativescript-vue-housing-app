<template>
  <ListView class="category-list" for="c in categories" @itemTap="tapItem">
    <v-template>
      <Label :text="c.title" class="category-item" />
    </v-template>
  </ListView>
</template>

<script>
export default {
  computed: {
    categories() {
      return [
        { title: '類型1', code: 'one' },
        { title: '類型2', code: 'two' },
        { title: '類型3', code: 'three' },
        { title: '類型4', code: 'four' },
        { title: '類型5', code: 'five' },
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
