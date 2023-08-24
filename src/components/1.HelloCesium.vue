

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
</template>
<script setup>
import { onMounted } from "vue";
import { ref } from 'vue'
import { Viewer, Ion, ArcGisMapServerImageryProvider, createWorldTerrain } from "cesium";

onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  // ArcGIS 影像图层
  const esri = new ArcGisMapServerImageryProvider({
    url: "https://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer",
    enablePickFeatures: false, 
  })
  // viewer 是所有API的开始
  const viewer = new Viewer("CesiumContainer", {
    imageryProvider: esri, // 自定义影像图层。默认是谷歌影像图层
    terrainProvider: createWorldTerrain({
      requestWaterMask: true, // 水面特效
    }) // 地形图层
  });
  console.log("viewer", viewer)
})
</script>
<style scoped>
*{
  margin: 0;
  padding: 0;
}
.read-the-docs {
  color: #888;
}
#CesiumContainer {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
