

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Entity, Cartesian3, Color } from "cesium";

onMounted(() => {
  Ion.defaultAccessToken = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiI3OWQ0OWFlMi1jNmE3LTQ2NTUtYmQ3ZC1kMzA2MGNjYWIxMjQiLCJpZCI6MTYxOTExLCJpYXQiOjE2OTI3MDM2MzF9.-AxJTCmapUmGuGWsxa5KpLxpdctsZdwnJxK7baeoG1k"
  // viewer 是所有API的开始
  const viewer = new Viewer("CesiumContainer", {
    timeline: false, // 时间轴控件
    animation: false, // 动画控件
    geocoder: false, // 搜索按钮
    homeButton: false, // 主页按钮
    sceneModePicker: false, // 投影方式按钮
    baseLayerPicker: false, // 图层选择按钮
    navigationHelpButton: false, // 帮助手册按钮
    fullscreenButton: false, // 全屏按钮
  });
  // 实体 entity
  // 写法一
  // const point = new Entity({
  //   position: Cartesian3.fromDegrees(120, 30), // 笛卡尔坐标
  //   point: {
  //     pixelSize: 20, // 像素大小
  //     color: Color.BLUE
  //   }
  // })
  // viewer.entities.add(point)
  // viewer.zoomTo(point)
  // 写法二
  const point = viewer.entities.add({
    id: "point",
    position: Cartesian3.fromDegrees(121, 30),
    point: {
      pixelSize: 20, // 像素大小
      color: Color.BLUE
    }
  })
  console.log("point", point)
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
