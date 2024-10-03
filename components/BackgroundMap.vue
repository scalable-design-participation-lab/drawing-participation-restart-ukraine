<template>
  <div>
    <ClientOnly>
      <MapboxMap map-id="1" :options="mapOptions" @map-load="onMapLoaded" />
    </ClientOnly>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useMapUIStore } from '@/stores/mapUI'
import mapboxgl from 'mapbox-gl'
import MapboxDraw from '@mapbox/mapbox-gl-draw'
import '@mapbox/mapbox-gl-draw/dist/mapbox-gl-draw.css'

const mapUIStore = useMapUIStore()

const mapOptions = ref({
  style: 'mapbox://styles/mapbox/light-v11',
  center: [28.48097, 49.23278],
  zoom: 12,
  attributionControl: false,
})

const draw = ref(null)

const onMapLoaded = (map) => {
  draw.value = new MapboxDraw({
    displayControlsDefault: false,
    controls: {
      point: false,
      line_string: false,
      polygon: false,
      trash: true,
    },
  })

  map.addControl(draw.value)
  mapUIStore.initializeMap(map, draw.value)
}

onMounted(() => {})
</script>

<style lang="postcss" scoped>
.mapboxgl-map {
  width: 100%;
  min-height: 100vh;
  margin: 0;
}
</style>
