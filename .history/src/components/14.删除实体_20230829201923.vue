

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
  const viewer = new Viewer("CesiumContainer", {
    timeline: false, // 时间轴控件
    animation: false, // 动画控件
    geocoder: false, // 搜索按钮
    homeButton: false, // 主页按钮
    sceneModePicker: false, // 投影方式按钮
    baseLayerPicker: false, // 图层选择按钮
    navigationHelpButton: false, // 帮助手册按钮
    fullscreenButton: false, // 全屏按钮
    infoBox: false, // 右侧信息框
    selectionIndicator: false, // 隐藏选中状态
  });
  
  const billboard = viewer.entities.add({
    position: Cartesian3.fromDegrees(120, 30, 100),
    billboard: {
      image: "/src/assets/map.png",
      scale: 0.3,
      color: Color.RED
    },
    label: {
      id: 'my label',
      text: 'English text',
      font: "100px",
      fillColor: Color.RED,
      pixelOffset: new Cartesian2(0, -20)
    },
  })
  const line = viewer.entities.add({
    polyline: {
      positions: Cartesian3.fromDegreesArrayHeights([120,30,0, 120,30,100]),
      material: Color.AQUA
    }
  })
  viewer.zoomTo(billboard)
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
