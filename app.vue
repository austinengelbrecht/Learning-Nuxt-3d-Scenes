<template>
  <TresCanvas window-size clear-color="#82dbc5">
    <TresMesh ref="boxRef" :rotation="[Math.PI / 4, Math.PI / 2, 0]">
      <TresBoxGeometry />
      <TresMeshNormalMaterial />
    </TresMesh>
  </TresCanvas>
</template>

<script setup>
const boxRef = ref();

const { onLoop } = useRenderLoop();

onLoop(({ delta, elapsed, clock, dt }) => {
  // I will run at every frame ~ 60FPS (depending of your monitor)
  if (boxRef.value) {
    boxRef.value.rotation.y += delta;
    boxRef.value.rotation.z = elapsed * 0.2;
  }
});
</script>
