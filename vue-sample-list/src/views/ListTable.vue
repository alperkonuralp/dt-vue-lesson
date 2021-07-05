<template>
  <div class="list table">
    <div class="item header">
      <div class="image">Image</div>
      <div class="code">Code</div>
      <div class="title">Title</div>
      <div class="region">Region</div>
      <div class="subregion">Subregion</div>
    </div>
    <div
      class="item"
      v-for="i in listData"
      :key="i.alpha3Code"
      v-bind:title="getItemTitle(i)"
    >
      <div class="image"><img :src="i.flag" /></div>
      <div class="code">{{ i.alpha3Code }}</div>
      <div class="title">{{ i.name }}</div>
      <div class="region">{{ i.region }}</div>
      <div class="subregion">{{ i.subregion }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import { DataType } from "@/data";

@Component
export default class ListTable extends Vue {
  @Prop({ required: true, type: Array })
  private listData!: DataType[];

  private getItemTitle(item: DataType) {
    return `${item.alpha3Code}\n${item.name}\n${item.region}`;
  }
}
</script>

<style scoped lang="scss">
div.list.table {
  width: 800px;
  margin: 0 auto;
  background-color: #ddd;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;

  div.item {
    flex: 1 1 auto;
    width: 100%;
    display: flex;
    flex-direction: row;
    cursor: pointer;

    div {
      padding: 5px;
    }

    .image {
      flex: 1;
      align-self: center;

      img {
        width: 50px;
      }
    }
    .code {
      text-align: center;
      font-weight: bold;
      flex: 1;
      align-self: center;
    }
    .title {
      text-align: center;
      flex: 1;
      align-self: center;
    }
    .region {
      text-align: center;
      flex: 1;
      align-self: center;
    }
    .subregion {
      text-align: center;
      flex: 1;
      align-self: center;
    }

    &:hover{
      background-color: #bbb;
    }
  }

  .header {
    font-weight: bold;
    background-color: #ccc;
    padding: 10px 0;
  }
}
</style>
