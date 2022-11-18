<script>
import LineChart from './LineChart.vue'
import DayList from './DayList.vue'
import WeatherData from './WeatherData.vue'
import axios from 'axios'

export default ({
    name: "Widget",
    components: {
        LineChart,
        DayList,
        WeatherData
    },
    // provide() {
    //     return { dailyMax: this.daily }
    // },
    methods: {
        changeDay(d) {
            this.$on('changeDay', () => { console.log("ghannged day") })
        }
    },
    data() {
        return {
            data: {},
            current: {},
            daily: {},
            maxDaily: []
        }
    },
    mounted() {
        axios
            .get(`https://api.openweathermap.org/data/2.5/onecall?lat=40.58725980318928&lon=22.948223362612612&exclude=hourly,minutely&appid=11b0499bd13ab56063de7565a440eb97&units=metric`)
            .then(response => {
                this.data = response.data;
                this.daily = response.data.daily;
                this.current = response.data.current;
                var x = [];
                for (var i = 0; i < response.data.daily.length; i++) {
                    x.push(response.data.daily[i].temp.max)
                }
                this.maxDaily = x;
                console.log(this.maxDaily)
            })
    }
})

</script>

<template>
    <div class="widget">
        <div class="innerwidget">

            <WeatherData :weather="current" />

            <div>
                <h3>Latest 7 Days Max Temperatures</h3>
                <LineChart :dailyMax="maxDaily" />

            </div>
        </div>
        <DayList :days="daily" />
    </div>
</template>
  

<style scoped>
.widget {
    background-color: rgba(240, 240, 240, 0.5);
    box-shadow: rgba(255, 255, 255, 0.76) 0px 22px 70px 4px;
    border-radius: 2rem;
    padding: 5rem 2rem;
    margin: 5rem 5rem;
    display: flex;
    flex-direction: column;
    /* justify-content: space-around;
    align-items: center; */
}

.innerwidget {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;

}

h1,
h3,
label {
    color: navy;
}

.temperature {
    font-size: 5vw;
}

.weatherInfo {
    display: flex;
    flex-direction: column;
    justify-self: center;
    align-items: center;
}

.weatherDetails {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 2em;
}

.details {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 1em 1em;
    padding: 1em;
    background-color: rgba(240, 240, 240, 0.5);
    box-shadow: rgba(255, 255, 255, 0.76) 0px 22px 70px 4px;
    border-radius: 1rem;
}

.details h3 {
    font-weight: bold;
}

@media (max-width: 1024px) {
    h3 {
        text-align: center;
    }

    .innerwidget {
        flex-direction: column;
    }
}
</style>
  