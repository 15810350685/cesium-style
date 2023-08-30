

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
  <button class="button" @click="toDel">删除</button>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Cartesian3, Cartesian2, Color, Label } from "cesium";
// import Color from "cesium/Source/Core/Color";
let viewer, point_01, point_02
const toDel = () => {
  // viewer.entities.remove(point_01)
  viewer.entities.removeAll()
}
onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  // viewer 是所有API的开始
  viewer = new Viewer("CesiumContainer", {});
  console.log("viewer", viewer)
  point_01 = viewer.entities.add({
    position: Cartesian3.fromDegrees(121, 30),
    point: {
      color: Color.BLUE,
      pixelSize: 20
    }
  })
  point_02 = viewer.entities.add({
    position: Cartesian3.fromDegrees(121.001, 30),
    point: {
      color: Color.BLUE,
      pixelSize: 20
    }
  })
  viewer.zoomTo(point)
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
.button {
  position: absolute;
  top: 50px;
  left: 50px;
  z-index: 999;
}
</style>
