<script lang="ts">
    import {MapLibre, GeoJSON, FillLayer, type LayerClickInfo} from "svelte-maplibre"
    import type { Feature } from "geojson";

    let feature1: Feature = {
        type:"Feature",
        properties: {  },
        geometry: {
            
                    type: 'LineString',
                    coordinates: [[0,0],[10,0],[10,10],[0,10], [0,0]],
        }
    }

    function clickFeature1(event: CustomEvent<LayerClickInfo>) {
        // event.stopImmediatePropagation()
        // event.stopPropagation()
        // event.preventDefault()
        // event.detail.event.originalEvent.stopImmediatePropagation()
        // event.detail.event.originalEvent.stopPropagation()
        console.log("Click on feature 1")
        // console.log(event)
    }
    
    let feature2: Feature = {
        type:"Feature",
        properties: {  },
        geometry: {
            
                    type: 'LineString',
                    coordinates: [[5,5],[15,5],[15,15],[5,15], [5,5]],
        }
    }

    function clickFeature2(event: CustomEvent<LayerClickInfo>) {
        // event.stopImmediatePropagation()
        // event.stopPropagation()
        // event.preventDefault()
        // event.detail.event.originalEvent.stopImmediatePropagation()
        // event.detail.event.originalEvent.stopPropagation()
        console.log("Click on feature 2")
        // console.log(event)
    }
    

</script>

<MapLibre
  style="https://basemaps.cartocdn.com/gl/positron-gl-style/style.json"
  class="map"
  standardControls
>
<GeoJSON id="feature1" data={feature1}>
      <FillLayer
        id="layer1"
        paint={{
          'fill-color': "green",
          'fill-opacity': 1,
        }}
        on:click={clickFeature1}
        />
    </GeoJSON>
    <GeoJSON id="feature2" data={feature2} >
      <FillLayer
        id="layer2"
        paint={{
          'fill-color': "red",
          'fill-opacity': 1,
        }}
        on:click={clickFeature2}
      />
  </GeoJSON>
</MapLibre>

<style>

    :global(.map) {
        height: 1000px;
        width: 1500px;
    }
</style>