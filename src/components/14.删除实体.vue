

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
  <button class="button" @click="toDel">删除</button>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Cartesian3, Cartesian2, Color, Label } from "cesium";
// import Color from "cesium/Source/Core/Color";
let viewer, point_01, point_02, point_03, point_list = []
const toDel = () => {
  // viewer.entities.remove(point_01) // 删除一个
  // viewer.entities.removeAll() // 删除全部
  // viewer.entities.removeById("point"), // 通过ID删除
  point_list.forEach(item => {
    viewer.entities.remove(item)
  })
  point_list = []
}
onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  // viewer 是所有API的开始
  viewer = new Viewer("CesiumContainer", {});
  console.log("viewer", viewer)
  point_01 = viewer.entities.add({
    id: "point",
    position: Cartesian3.fromDegrees(121.0001, 30),
    point: {
      color: Color.BLUE,
      pixelSize: 20
    }
  })
  point_list.push(point_01)
  point_02 = viewer.entities.add({
    position: Cartesian3.fromDegrees(121.0002, 30),
    point: {
      color: Color.BLUE,
      pixelSize: 20
    }
  })
  point_list.push(point_02)
  point_03 = viewer.entities.add({
    position: Cartesian3.fromDegrees(121.0003, 30),
    point: {
      color: Color.RED,
      pixelSize: 20
    }
  })
  point_list.push(point_03)
  viewer.zoomTo(point_01)
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
