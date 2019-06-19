<template>
    <div id="app">
        <!-- <base-label></base-label> -->
        <base-event></base-event>
        <base-canvas-one></base-canvas-one>
        <!-- <base-canvas-two></base-canvas-two> -->
        <!-- <base-geolocation></base-geolocation> -->
        <base-geolocation-two></base-geolocation-two>
		<base-Postmessage></base-Postmessage>
    </div>
</template>

<script>
import baseLabel from '../components/base-label'
import baseEvent from '../components/base-event'
import baseCanvasOne from '../components/base-canvas-one'
import baseCanvasTwo from '../components/base-canvas-two'
import baseCanvasThree from '../components/base-canvas-Three'
import baseGeolocation from '../components/base-geolocation'
import baseGeolocationTwo from '../components/base-geolocation-two'
import basePostmessage from '../components/base-Postmessage'
export default {
    name: 'app',
    components: {
        baseLabel,
        baseEvent,
        baseCanvasOne,
        baseCanvasTwo,
		baseCanvasThree,
		baseGeolocation,
		baseGeolocationTwo,
		basePostmessage
    },
    data() {
        return {
            msg: 'Welcome to Your Vue.js App'
        }
    }
}
</script>

<style>
</style>
