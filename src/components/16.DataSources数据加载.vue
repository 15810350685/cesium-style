

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
  <button class="button" @click="toDel">删除</button>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, GeoJsonDataSource, KmlDataSource } from "cesium";
let viewer, dataSources
const toDel = () => {
  // viewer.entities.removeAll()
  viewer.dataSources.remove(dataSources)
}
onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  viewer = new Viewer("CesiumContainer", {});
  // const linestring = turf.lineString([[-24, 63],[-23, 60], [-25, 65],[-20, 69]], {name: 'line 1'});
  // GeoJsonDataSource.load(linestring).then((res) => {
  //   console.log("res", res)
  //   const entity = res.entities.values[0]
  //   viewer.entities.add(entity)
  //   viewer.zoomTo(entity)
  // })

  // const muitiLine = turf.lineString([[0, 0],[4, 4], [6, 6],[10, 10]]);
  // GeoJsonDataSource.load(muitiLine).then((res) => {
  //   console.log("viewer.dataSources", viewer.dataSources)
  //   viewer.dataSources.add(res)
  //   dataSources = res
  // })

  // const polygon = turf.polygon([[[-5, 52], [-4, 56], [-2, 51], [-5, 52]]]);
  // const promise = GeoJsonDataSource.load(polygon)
  // viewer.dataSources.add(promise)
  // viewer.zoomTo(promise)  
  
  // 美国地图显示高亮  
  // const promise = GeoJsonDataSource.load('/src/assets/usa.topojson')
  // viewer.dataSources.add(promise)
  // viewer.zoomTo(promise)  

  // const promise = KmlDataSource.load('/src/assets/gdp2008.kmz')
  // viewer.dataSources(promise)  
})

</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
}
#CesiumContainer {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
.button {
  position: absolute;
  top: 50px;
  left: 50px;
  z-index: 999;
}
</style>
