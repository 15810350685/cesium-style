

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Cartesian3, Cartographic, Math } from "cesium";

onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  // viewer 是所有API的开始
  new Viewer("CesiumContainer", {
    timeline: false, // 时间轴控件
    animation: false, // 动画控件
    geocoder: false, // 搜索按钮
    homeButton: false, // 主页按钮
    sceneModePicker: false, // 投影方式按钮
    baseLayerPicker: false, // 图层选择按钮
    navigationHelpButton: false, // 帮助手册按钮
    fullscreenButton: false, // 全屏按钮
  });
  
  // 经纬度转笛卡尔
  // 返回的是笛卡尔坐标 z!=高度
  const cartesian1 = Cartesian3.fromDegrees(110, 20, 20) // 经度 维度 高度
  const cartesian2 = Cartesian3.fromDegrees(110, 20, 30) // 经度 维度 高度
  console.log("cartesian1", cartesian1)
  console.log("cartesian2", cartesian2)

  // 笛卡尔转弧度坐标
  const Cartographic1 = Cartographic.fromCartesian(cartesian1)
  console.log("Cartographic1", Cartographic1)

  // 弧度转角度 => 不是正规的转法
  const lon = 180 / Math.PI * Cartographic1.longitude
  const lat = 180 / Math.PI * Cartographic1.latitude
  console.log("lon", lon)
  console.log("lat", lat)

  // 弧度转角度 => 正规的转法
  const lon1 = Math.toDegrees(Cartographic1.longitude)
  const lat1 = Math.toDegrees(Cartographic1.latitude)
  console.log("lon1", lon1)
  console.log("lat1", lat1)
  console.log("height1", Cartographic1.height)
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
