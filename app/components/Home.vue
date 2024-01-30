<template>
  <Page actionBarHidden="true">
    <FlexboxLayout flexDirection="column">
      <SearchBar
        :city="city"
        :district="district"
        :selectCity="selectCity"
        :selectDistrict="selectDistrict"
        :selectReset="selectReset"
      />
      <HouseList :list="houseList" />
    </FlexboxLayout>
    <!-- <TabView androidTabsPosition="bottom" iosIconRenderingMode="alwaysOriginal">
      <TabViewItem title="首頁">
        <Label text="首頁" />
      </TabViewItem>
      <TabViewItem title="搜尋">
        <GridLayout>
          <Search />
        </GridLayout>
      </TabViewItem>
      <TabViewItem title="新聞">
        <Label text="新聞" />
      </TabViewItem>
    </TabView> -->
  </Page>
</template>

<script lang="ts">
import Vue from 'nativescript-vue';
import axios from 'axios';
import SearchBar from './SearchBar.vue';
import HouseList from './HouseList.vue';

const originalList = [
  {
    code: 0,
    title: '全新豪邸-信義御邸景觀樓',
    city: '台北市',
    type: '住宅',
    price: 260000000,
    layout: '4房2廳3衛2陽台',
    size: 157.99,
    address: '台北市大安區信義路二段44巷24-3號',
    age: 4,
    src: 'https://img2.591.com.tw/house/2023/07/06/168862081272240503.jpg!400x300.jpg',
  },
  {
    code: 1,
    title: '房2',
    city: '新北市',
    type: '套房',
    price: 52680000,
    layout: '4房2廳2衛2陽台',
    size: 71.93,
    address: '新北市新店區北宜路一段',
    age: 7,
    src: 'https://img2.591.com.tw/house/2023/07/06/168862081272240503.jpg!400x300.jpg',
  },
  {
    code: 2,
    title: '房3',
    city: '桃園市',
    type: '',
    price: 0,
    layout: '',
    size: '',
    address: '桃園市蘆竹區南崁路一段',
    age: 0,
    src: 'https://img2.591.com.tw/house/2023/07/06/168862081272240503.jpg!400x300.jpg',
  },
  {
    code: 3,
    title: '房4',
    city: '宜蘭縣',
    type: '',
    price: 0,
    layout: '',
    size: '',
    address: '宜蘭縣礁溪鄉仁愛路',
    age: 0,
    src: 'https://img2.591.com.tw/house/2023/07/06/168862081272240503.jpg!400x300.jpg',
  },
  {
    code: 4,
    title: '房5',
    city: '基隆市',
    type: '',
    price: 0,
    layout: '',
    size: '',
    address: '基隆市安樂區安和一街6巷',
    age: 0,
    src: 'https://img2.591.com.tw/house/2023/07/06/168862081272240503.jpg!400x300.jpg',
  },
  {
    code: 5,
    title: '房6',
    city: '新竹市',
    type: '',
    price: 0,
    layout: '',
    size: '',
    address: '新竹市東區光復路二段302號',
    age: 0,
    src: 'https://img2.591.com.tw/house/2023/07/06/168862081272240503.jpg!400x300.jpg',
  },
];

export default Vue.extend({
  data() {
    return {
      city: '縣市',
      district: '行政區',
      houseList: [...originalList],
    };
  },

  components: {
    HouseList,
    SearchBar,
  },

  methods: {
    selectCity(city) {
      this.city = city;
      this.houseList = originalList.filter(({ address }) => {
        if (city) {
          return address.includes(city);
        }
        return true;
      });
    },
    selectDistrict(district) {
      this.district = district;
      this.houseList = originalList.filter(({ address }) => {
        if (district) {
          return address.includes(district);
        }
        return true;
      });
    },
    selectReset() {
      this.city = '縣市';
      this.district = '行政區';
      this.houseList = [...originalList];
    },
  },

  mounted() {
    console.log('mounted');
    fetch(
      'https://gist.githubusercontent.com/vinta/079cb8d4da486f471365c31388ed1b85/raw/c8dc91acc476aea98f5a6f1db59df966e4e3d4c1/%25E5%258F%25B0%25E7%2581%25A3%25E5%2590%2584%25E8%25A1%258C%25E6%2594%25BF%25E5%258D%2580%25E5%2588%2597%25E8%25A1%25A8.py'
    )
      .then((res) => {
        return res.json();
      })
      .then((json) => {
        console.log('json', json);
      });
  },
});
</script>
