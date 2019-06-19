<template>
    <div id>
        <h2>HTML5 Geolocation Distance</h2>
        <p>当前位置：</p>
        <table border="1">
            <tr>
                <th width="40" scope="col">纬度</th>
                <td width="114">{{watchData.coords?watchData.coords.latitude : '?'}}</td>
            </tr>
            <tr>
                <th width="40" scope="col">经度</th>
                <td width="114">{{watchData.coords?watchData.coords.longitude : '?'}}</td>
            </tr>
            <tr>
                <th width="40" scope="col">偏移距离</th>
                <td width="114">{{watchData.coords?watchData.coords.accuracy : '?'}}</td>
            </tr>
            <tr>
                <th width="40" scope="col">更新时间</th>
                <td width="114">{{watchData.coords?watchData.timestampStr : '?'}}</td>
            </tr>
        </table>
        <h5>加载了{{total}}次</h5>
        <h5 >执行了{{timestampStr}}毫秒</h5>
        <!-- <h5 v-else>执行了0毫秒</h5> -->
        <h4>当前运动距离：{{currentDistance || '0.0'}}km</h4>
        <h4>总共运动距离：{{totalDistance || '0.0'}}km</h4>
    </div>
</template>

<script>
export default {
    name: '',
    props: {},
    components: {},
    data() {
        return {
            watchData: {},
            currentDistance: '',
            totalDistance: 0,
            oldData: {
                lastLat: '',
                lastLong: ''
            },
            total: 0,
            timestamp:null,
            timestampStr : ''
        }
    },
    mounted() {
        Number.prototype.toRadians = function () {
            return this * Math.PI / 180;
        }
        this.initTimestamp();
        this.initPosition();
    },
    computed: {},
    methods: {
        initTimestamp(){
            let {timestamp} = this;
            if(timestamp>0){
                this.timestampStr = (new Date().getTime() - timestamp).toString();
            }
            else{
                this.timestamp = new Date().getTime();
                this.timestampStr = new Date().getTime().toString();
            }
            
            
        },
        // latitude:纬度，longitude：经度
        distance(latitude1, longitude1, latitude2, longitude2) {
            //R是地球的半径，以KM为单位
            let R = 6371;
            let deltaLatitude = (latitude2 - latitude1).toRadians();
            let deltaLongitude = (longitude2 - longitude1).toRadians();
            latitude1 = latitude1.toRadians(), latitude2 = latitude2.toRadians();

            let a = Math.sin(deltaLatitude / 2) * Math.sin(deltaLatitude / 2) + Math.cos(latitude1) * Math.cos(latitude2) * Math.sin(deltaLongitude / 2) * Math.sin(deltaLongitude / 2);
            let c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
            let d = R * c;
            return d.toFixed(4);
        },
        initPosition() {
            let nvaga = navigator.geolocation;
            let watchId = nvaga.watchPosition((res) => {
                let watchData = this.watchData;
                if(watchData && watchData.timestamp){
                    if(res.timestamp - watchData.timestamp <= 800){
                        return;
                    }
                }
                this.total += 1;
                this.initTimestamp();
                if (res) {
                    let latitude = res.coords.latitude;
                    let longitude = res.coords.longitude;
                    let accuracy = res.coords.accuracy;
                    let {lastLat,lastLong} = this.oldData;
                    res.timestampStr = this.changeTime(res.timestamp);
                    this.watchData = res;
                    if(lastLat !== '' && lastLong !== ''){
                        if(this.distance(latitude,longitude,lastLat,lastLong)>accuracy/1000){
                            this.currentDistance = (this.distance(latitude,longitude,lastLat,lastLong)*1000-accuracy)/1000;
                        }
                        else{
                            this.currentDistance = this.distance(latitude,longitude,lastLat,lastLong);
                        }
                        this.totalDistance = (this.totalDistance*10000 + this.currentDistance*10000)/10000;
                    }
                    this.oldData.lastLat = latitude;
                    this.oldData.lastLong = longitude;
                }

            },(res)=>{},{maximumAge:0,timeout:1000});

            // setInterval(() => {
            //     nvaga.getCurrentPosition((res) => {
            //         this.total += 1;

            //         if (res) {
            //             let latitude = res.coords.latitude;
            //             let longitude = res.coords.longitude;
            //             let accuracy = res.coords.accuracy;
            //             let { lastLat, lastLong } = this.oldData;
            //             res.timestampStr = this.changeTime(res.timestamp);
            //             this.watchData = res;
            //             if (lastLat !== '' && lastLong !== '') {
            //                 this.currentDistance = this.distance(latitude, longitude, lastLat, lastLong);
            //                 this.totalDistance = (this.totalDistance * 10000 + this.currentDistance * 10000) / 10000;
            //             }
            //             this.oldData.lastLat = latitude;
            //             this.oldData.lastLong = longitude;
            //         }

            //     }, (res) => { }, { maximumAge: 0, timeout: 1000 })
            // }, 2000);

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
 
<style></style>
 