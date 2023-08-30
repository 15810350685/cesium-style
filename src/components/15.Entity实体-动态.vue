

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
  <button class="button" @click="toDel">删除</button>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Cartesian3, Cartesian2, Color, Label } from "cesium";
import CallbackProperty from "cesium/Source/DataSources/CallbackProperty";
const toDel = () => {
}
onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  let lon, lat, num = 0
  const viewer = new Viewer("CesiumContainer", {});
  const lint = viewer.entities.add({
    // polyline: {
    //   positions: Cartesian3.fromDegreesArray([120,30, 121,31]),
    //   width: 5,
    //   material: Color.YELLOW
    // }
    polyline: {
      positions: new CallbackProperty(() => {
        num += 0.005
        lon = 120 + num
        lat = 30 + num
        if (lon < 121) {
          return Cartesian3.fromDegreesArray([120,30, lon,lat])
        } else {
          // 给positions 赋值一个新的对象，要不然会一直循环
          lint.polyline.positions = Cartesian3.fromDegreesArray([120,30, 121,31])
        }
      }, false), // 传false，不传动不起来
      width: 5,
      material: Color.YELLOW
    }
  })
  viewer.zoomTo(lint)
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
