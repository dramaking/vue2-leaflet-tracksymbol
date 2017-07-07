# vue2-leaflet-tracksymbol

This is a [tracksymbol plugin](https://github.com/lethexa/leaflet-tracksymbol) extension for [vue2-leaflet package](https://github.com/KoRiGaN/Vue2Leaflet)

Thanks to [Julián Perelli](https://jperelli.com.ar/) of [markercluster plugin](https://github.com/Leaflet/Leaflet.markercluster) extension for providing the basis to build this plugin

## Install

    npm install --save vue2-leaflet-tracksymbol

## Usage

### on &lt;template&gt; add

something like this

    <v-map :zoom=10 :center="initialLocation">
      <v-tilelayer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></v-tilelayer>
      <v-ais :latlng="[50.013220, -2.119482]" :options="options"></v-ais>
    </v-map>

### on &lt;script&gt; add

#### option 1 - Component locally

In the same template file, at `<script>` part, this will make the component available only to the template in this file

    import Vue2LeafletTracksymbol from 'vue2-leaflet-tracksymbol'
    ...
    export default {
      ...
      components: {
        'v-ais': Vue2LeafletTracksymbol
        ...
      },
      ...
    }

#### option 2 - Component globally

At main Vue configuration, this will make the component available to all templates in your app

    import Vue from 'vue'
    import Vue2LeafletTracksymbol from 'vue2-leaflet-tracksymbol'
    ...
    Vue.component('v-ais', Vue2LeafletTracksymbol)

#### Add To data()

    ...
    data () {
      return {
        options: {
          trackId: 123,
          fill: true,
          fillColor: '#00ffff',
          fillOpacity: 1.0,
          stroke: true,
          color: '#000000',
          opacity: 1.0,
          weight: 1.0,
          speed: 30, // meter per second
          course: 1.0, // radians
          heading: 1.0, // radians
          size: 24,
          defaultSymbol: [0.75, 0, 0.5, 0.3, -0.5, 0.3, -0.25, 0, -0.5, -0.3, 0.5, -0.3],
          data: { name: 'Boat 2', custom: 'other info' }
        }
      }
    }
    ...

## Develop and build

    npm install
    npm run build

## Author

[Aaron Gong](http://www.charterme.co/)

## License

MIT

## Changes

* 1.0.7
  * update vue2-leaflet to 0.0.51
* 1.0.7
  * update vue2-leaflet to 0.0.50
* 1.0.6
  * add size, no heading shape and silhoutte shape options
* 1.0.5
  * add optional data field for user custom data
* 1.0.4
  * fix error in tracksymbol default options
* 1.0.3
  * updated default options and vue2-leaflet version
* 1.0.2
* 1.0.1
* 1.0.0