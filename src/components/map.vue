<template>
  <l-map style="height: 92vh;width: 99vw" :zoom="zoom" :center="center">
    <l-tile-layer :url="baseLayer.url" :attribution="baseLayer.attribution"></l-tile-layer>
    <l-wms-tile-layer
        :key="wmsLayer.name"
        :base-url="wmsLayer.url"
        :layers="wmsLayer.layers"
        :visible="wmsLayer.visible"
        :name="wmsLayer.name"
        :attribution="wmsLayer.attribution"
        :transparent="true"
        format="image/png"
        layer-type="base">
    </l-wms-tile-layer>
  </l-map>
</template>

<script>
import {LMap, LTileLayer, LWMSTileLayer } from 'vue2-leaflet';

export default {
  components: {
    LMap,
    LTileLayer,
    'l-wms-tile-layer': LWMSTileLayer
  },
  data () {
    return {
      zoom: 4,
      center: [39.833333, -98.583333],
      baseLayer: {
        url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
        attribution:
            '&copy; <a target="_blank" href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      },
      wmsLayer: {
        url: 'http://mesonet.agron.iastate.edu/cgi-bin/wms/nexrad/n0r.cgi',
        name: 'Weather Data',
        visible: true,
        format: 'image/png',
        layers: 'nexrad-n0r-900913',
        transparent: true,
        attribution: 'Weather data &copy; 2012 <a href="https://mesonet.agron.iastate.edu/docs/nexrad_mosaic/">IEM Nexrad</a>',
      }
    };
  }
}
</script>
