<template>
  <div id="list" class="thumbnail">
    <h2>Country List</h2>
    <div :class="listClass">
      <div class="item" v-for="i in internalData" :key="i.alpha3Code" v-bind:title="getItemTitle(i)">
        <div class="item-container">
          <img :src="i.flag" />
          <div class="code">{{ i.alpha3Code }}</div>
          <div class="title">{{ i.name }}</div>
          <div class="region">{{ i.region }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import { DataType, default as serviceData } from "@/data";

interface RegionType {
  id: number;
  name: string;
}

@Component
export default class List extends Vue {
  // private pageData: DataType[] = allData;
  private listClass: string[] = ["list"];
  private internalData: DataType[] = [];

  private mounted() {
    this.internalData = serviceData;
  }

  private getItemTitle(item: DataType){
      return `${item.alpha3Code}\n${item.name}\n${item.region}`;
  }
}
</script>

<style scoped lang="scss">
#list.thumbnail {
  * {
    font-family: "Roboto";
  }
  div.list {
    display: flex;
    // flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    justify-content: space-between;
    // align-content: flex-start;
    background-color: #ddd;

    div.item {
      position: relative;
      border: 1px solid white;
      background-color: #bbb;
      width: 100px;
      height: 150px;
      padding: 5px;
      margin: 2px;
      transition: all 0.2s ease-in-out;
      cursor: pointer;
      overflow: hidden;

      img {
        width: 100px;
      }

      .code {
        text-align: center;
        font-weight: bold;
      }
      .title {
        text-align: center;
      }
      .region {
        text-align: center;
        font-style: italic;
      }

      &:hover {
        transform: scale(1.3);
        z-index: 1;
      }
    }
  }
}
</style>
