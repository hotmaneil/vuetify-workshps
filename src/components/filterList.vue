<template>
  <h4>62家身心障礙福利機構及團體(庇護工廠)快速查詢</h4>
  <p>主要是方便大家依照所在地或附近的縣市去快速查詢並超連結網站與撥打電話訂購</p>
  <v-select label="縣市" :items="cityList" @update:model-value="selectChange"> </v-select>

  <v-card title="搜尋名稱" flat>
    <template v-slot:text>
      <v-text-field
        v-model="search"
        label="Search"
        prepend-inner-icon="mdi-magnify"
        variant="outlined"
        hide-details
        single-line
      ></v-text-field>
    </template>
    <v-data-table :headers="headers" :items="dataList" :search="search">
      <template #item.name="{ item }">
        <a v-if="item.url" :href="item.url" target="_blank" rel="noopener noreferrer">
          {{ item.name }}
        </a>
        <span v-else>{{ item.name }}</span>
      </template>
      <template #item.phoneNumber="{ item }">
        <a :href="`tel:${item.phoneNumber}`">{{ item.phoneNumber }}</a>
      </template>
    </v-data-table>
  </v-card>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { dataList as sourceDataList } from './dataList';

const headers = [
  { key: 'name', title: '名稱' },
  { key: 'phoneNumber', title: '電話' },
];

const cityList = ref([
  '全部',
  '台北市',
  '新北市',
  '基隆市',
  '桃園市',
  '新竹市',
  '新竹縣',
  '苗栗縣',
  '台中市',
  '彰化縣',
  '南投縣',
  '雲林縣',
  '嘉義市',
  '嘉義縣',
  '台南市',
  '高雄市',
  '屏東縣',
  '宜蘭縣',
  '花蓮縣',
  '台東縣',
  '澎湖縣',
  '金門縣',
  '連江縣',
]);
const dataList = ref(sourceDataList);

const search = ref();

function selectChange(cityName: string | null) {
  dataList.value =
    !cityName || cityName === '全部'
      ? sourceDataList
      : sourceDataList.filter((item) => item.cityName === cityName);
}
</script>
