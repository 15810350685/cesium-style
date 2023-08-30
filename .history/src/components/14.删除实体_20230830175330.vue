

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Cartesian3, Cartesian2, Color, Label } from "cesium";
// import Color from "cesium/Source/Core/Color";

onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  // viewer 是所有API的开始
  const viewer = new Viewer("CesiumContainer", {});
  console.log("viewer", viewer)
  viewer.entities.add({
    position: Cartesian3.fromDegrees(121, 30),
    point: {
      color: Color.BLUE,
      pixelSize: 20
    }
  })
})
</script>
<style scoped>
* {
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
