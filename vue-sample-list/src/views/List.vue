<template>
  <div id="list" :class="listMode">
    <h2>Country List</h2>
    <div>
      <select v-model="searchRegion">
        <option value="-1">Region</option>
        <option v-for="r in searchRegions" :key="r" :value="r">{{ r }}</option>
      </select>
      <button @click="listMode = 'thb'" :disabled="listMode === 'thb'">
        Thumbnail
      </button>
      <button @click="listMode = 'tbl'" :disabled="listMode === 'tbl'">
        Table
      </button>
    </div>
    <ListThumbnail :listData="filteredData" v-if="listMode === 'thb'" />
    <ListTable :listData="filteredData" v-else />
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
  private searchRegion = "-1";

  private mounted() {
    this.internalData = serviceData;
  }

  private get searchRegions(): string[] {
    return this.internalData
      .map((x) => x.region)
      .filter((v, i, a) => a.indexOf(v) === i)
      .sort();
  }

  private get filteredData(): DataType[] {
    if (this.searchRegion === "-1") {
      return this.internalData;
    }
    return this.internalData.filter(
      (item: DataType) => item.region === this.searchRegion
    );
  }
}
</script>

<style scoped lang="scss">
#list {
  button,
  select {
    font-size: 12pt;
    margin: 5px;
    padding: 5px 20px;
    width: 150px;
  }
}
</style>
