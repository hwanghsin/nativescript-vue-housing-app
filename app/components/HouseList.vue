<template>
  <StackLayout height="90%">
    <ListView
      class="house-list"
      for="item in list"
      @itemTap="tapItem"
      style="z-index: 50"
    >
      <v-template>
        <FlexboxLayout
          class="house-item"
          alignItems="flex-start"
          :key="item.code"
        >
          <Image width="40%" :src="item.src" class="img" />
          <FlexboxLayout width="60%" flexDirection="column">
            <Label :text="item.title" />
            <Label :text="item.town" />
            <Label :text="item.type" />
          </FlexboxLayout>
        </FlexboxLayout>
      </v-template>
    </ListView>
  </StackLayout>
</template>

<script>
import HouseItem from './HouseItem.vue';

export default {
  props: {
    list: Array,
  },

  components: {
    HouseItem,
  },

  data() {
    return {
      house: null,
    };
  },

  methods: {
    tapItem(event) {
      const house = this.list.find(({ code }) => code === event.item.code);

      this.house = house;
      this.$navigateTo(HouseItem, {
        props: {
          house,
        },
      });
    },
  },
};
</script>

<style>
.house-list {
}

.house-item {
  height: 450px;
  padding: 50px;
}

.house-item > .img {
  margin-right: 50px;
}
</style>
