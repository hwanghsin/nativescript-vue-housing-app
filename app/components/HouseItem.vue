<template>
  <Page actionBarHidden="false">
    <ActionBar>
      <FlexboxLayout width="100%" justifyContent="space-between">
        <Label width="33%" text="返回" @tap="$navigateBack" />
        <Label width="34%" text="詳細資料" class="header-center" />
        <Label width="33%" text="" />
      </FlexboxLayout>
    </ActionBar>
    <FlexboxLayout flexDirection="column">
      <Image width="100%" :src="house.src" />
      <FlexboxLayout flexDirection="column" class="detail">
        <Label class="title" :text="house.title" />
        <Label class="titaddressle" :text="house.address" />
        <FlexboxLayout>
          <FlexboxLayout flexDirection="column">
            <Label :text="house.price" />
            <Label text="售金" />
          </FlexboxLayout>
          <FlexboxLayout flexDirection="column">
            <Label :text="house.layout" />
            <Label text="格局" />
          </FlexboxLayout>
          <FlexboxLayout flexDirection="column">
            <Label :text="house.size" />
            <Label text="權狀坪數" />
          </FlexboxLayout>
        </FlexboxLayout>
      </FlexboxLayout>
    </FlexboxLayout>
  </Page>
</template>

<script>
export default {
  props: {
    house: {
      type: Object,
      default: () => ({}),
    },
  },
};
</script>

<style>
.header-center {
  text-align: center;
}

.detail {
  padding: 20px;
}

.title {
  font-size: 36px;
  margin: 10px 0;
}

.address {
}
</style>
