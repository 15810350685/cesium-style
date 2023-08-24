

<template>
  <div id="CesiumContainer" class="cesiumContainer"></div>
</template>
<script setup>
import { onMounted } from "vue";
import { Viewer, Ion, Cartesian3, Color } from "cesium";

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
  // 多边形
  const polygon = viewer.entities.add({
    polygon: {
      hierarchy: {
        positions: Cartesian3.fromDegreesArray([120, 25, 121, 25, 121, 25.5]), // 返回笛卡尔坐标数组
      },
      material: Color.RED,
      height: 100000,
      extrudedHeight: 200000,
      outline: true, // 是否显示外线
      outlineColor: Color.WHEAT,
      fill: false, // 是否填充
    }
  })
  // 盒子-立方体
  const Box = viewer.entities.add({
    position: Cartesian3.fromDegrees(119, 30, 3000),
    box: {
      dimensions: new Cartesian3(2000, 1000, 3000),
      material: Color.RED,
    }
  })
  viewer.zoomTo(Box)
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
