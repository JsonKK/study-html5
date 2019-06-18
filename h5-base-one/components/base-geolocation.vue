<template>
    <div id>
        <template v-if="normalData && normalData.coords">
            <h5>经纬度获取</h5>
            <p>获取到的精度是：{{normalData.coords.longitude}},纬度是：{{normalData.coords.latitude}},精确值偏移：{{normalData.coords.accuracy}}</p>
            <p>获取数据的时间：{{normalData.timestampStr}}</p>
        </template>

        <template v-if="watchData && watchData.coords">
            <h5 class="watch">经纬度监听</h5>
            <p
                class="watch"
            >获取到的精度是：{{watchData.coords.longitude}},纬度是：{{watchData.coords.latitude}},精确值偏移：{{watchData.coords.accuracy}}</p>
            <p class="watch">获取数据的时间：{{watchData.timestampStr}}</p>
        </template>
    </div>
</template>
 
<script>
export default {
    name: '',
    props: {},
    components: {},
    data() {
        return {
            normalData: {
                coords: {
                    // 精确偏移值(单位m)
                    accuracy: 58,
                    // 海拔(单位M)
                    altitude: 0,
                    // 海拔精准度（单位m）
                    altitudeAccuracy: 0,
                    // 相对于北面的行进方向
                    heading: null,
                    latitude: 24.876605859200428,
                    longitude: 118.63189624417473,
                    // 地面速度
                    speed: null
                }
            },
            watchData: {}
        }
    },
    mounted() {
        this.initPosition();
    },
    computed: {},
    methods: {
        initPosition() {
            let nvaga = navigator.geolocation;
            nvaga.getCurrentPosition((res) => {
                if (res) {
                    res.timestampStr = this.changeTime(res.timestamp);
                    this.normalData = res;
                }
            }, (res) => {

                let r = res;
            });

            let watchId = nvaga.watchPosition((res) => {
                if (res) {
                    res.timestampStr = this.changeTime(res.timestamp);
                    this.watchData = res;
                }

            });

        },
        // 转时间戳
        changeTime(time) {
            if (!time) {
                return time;
            }
            let date = new Date(time);
            let Y = date.getFullYear() + '-';
            let M = (date.getMonth() + 1 < 10 ? '0' + (date.getMonth() + 1) : date.getMonth() + 1) + '-';
            let D = date.getDate() + ' ';
            let h = date.getHours() + ':';
            let m = date.getMinutes() + ':';
            let s = date.getSeconds();
            return (Y + M + D + h + m + s);
        }
    },
    watch: {},
    filters: {}
}
</script>
 
<style>
.watch {
    color: #888;
}
</style>
 