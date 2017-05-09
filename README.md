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
          heading: 1.0 // radians
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
