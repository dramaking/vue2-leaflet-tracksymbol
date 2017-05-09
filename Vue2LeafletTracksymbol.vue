<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
import L from 'leaflet'
import 'leaflet-tracksymbol'

/*
const props = {
  visible: {
    type: Boolean,
    custom: true,
    default: true
  }
}
*/


import eventsBinder from './eventsBinder.js';
import propsBinder from './propsBinder.js';
const events = [
  'click',
  'dblclick',
  'mousedown',
  'mouseover',
  'mouseout',
  'contextmenu',
  'add',
  'remove',
  'popupopen',
  'popupclose',
  'tooltipopen',
  'tooltipclose'
];

const props = {
  latlng: {
    type: [Object, Array]
	// custom: false
  },
  options: {
    type: Object
	// custom: false
  },
  visible: {
    type: Boolean,
    custom: true,
    default: true
  }
}

export default {
  props: props,
  mounted () {
    // console.log(this.options)
    if (!this.options) this.options = {
    	trackId: 0,
   		fill: true,
    	fillColor: '#0000ff',
    	fillOpacity: 1.0,
    	stroke: true,
    	color: '#000000',
   		opacity: 1.0,
   		weight: 1.0,
    	speed: 0,
    	course: 0,
    	heading: 0
    }
    this.mapObject = L.trackSymbol(this.latlng, this.options)
    eventsBinder(this, this.mapObject, events)
    propsBinder(this, this.mapObject, props)
    if (this.$parent._isMounted) {
      this.deferredMountedTo(this.$parent.mapObject)
    }
  },
  beforeDestroy () {
    this.setVisible(false)
  },
  methods: {
    deferredMountedTo (parent) {
      this.parent = parent
      var that = this.mapObject
      for (var i = 0; i < this.$children.length; i++) {
        this.$children[i].deferredMountedTo(that)
      }
      if (this.visible) {
        this.mapObject.addTo(parent)
      }
    },
    setVisible (newVal, oldVal) {
      if (newVal === oldVal) return
      if (this.mapObject) {
        if (newVal) {
          this.mapObject.addTo(this.parent)
        }
        else {
          this.parent.removeLayer(this.mapObject)
        }
      }
    }
  }
}
</script>
