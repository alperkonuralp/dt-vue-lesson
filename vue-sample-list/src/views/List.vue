<template>
  <div id="list" :class="listMode">
    <h2>Country List</h2>
    <div>
      <button @click="listMode = 'thb'" :disabled="listMode === 'thb'">
        Thumbnail
      </button>
      <button @click="listMode = 'tbl'" :disabled="listMode === 'tbl'">
        Table
      </button>
    </div>
    <ListThumbnail :listData="internalData" v-if="listMode === 'thb'" />
    <ListTable :listData="internalData" v-else />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import { DataType, default as serviceData } from "@/data";

import ListThumbnail from "./ListThumbnail.vue";
import ListTable from "./ListTable.vue";

@Component({
  components: { ListThumbnail, ListTable },
})
export default class List extends Vue {
  private internalData: DataType[] = [];
  private listMode = "thb";

  private mounted() {
    this.internalData = serviceData;
  }

  private getItemTitle(item: DataType) {
    return `${item.alpha3Code}\n${item.name}\n${item.region}`;
  }
}
</script>

<style scoped lang="scss">
#list {
  button {
      font-size: 12pt;
      margin: 5px;
      padding: 5px 20px;
      width: 150px;
  }
}
</style>
