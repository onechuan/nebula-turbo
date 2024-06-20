<template>
  <div id="draw" />
</template>

<script lang='ts' setup>
import * as PIXI from "pixi.js";
import { onMounted } from "vue";

onMounted(() => {
  // 1. 创建 Pixi 应用，自动创建舞台和画布
  const app = new PIXI.Application({
    width: 300, // 画布宽度
    height: 300, // 画布高度
    backgroundColor: 0xcccccc,
  });

  // 2. 将画布添加到 DOM
  document.getElementById("draw")?.appendChild(app.view);

  // 3. 创建精灵
  const sprite = PIXI.Sprite.from("https://pixijs.com/assets/files/sample-747abf529b135a1f549dff3ec846afbc.png");


  // 4. 将精灵添加到舞台，显示精灵
  app.stage.addChild(sprite);

  // 5. 操作精灵
  let elapsed = 0.0;
  app.ticker.add((delta) => {
    // Add the time to our total elapsed time
    elapsed += delta;
    sprite.x = 50.0 + Math.cos(elapsed/50.0) * 100.0;
  });

})
</script>

<style scoped lang='scss'>
#draw {
  width: 500px;
  height: 500px;
}
</style>
