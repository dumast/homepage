<script>
    import * as configure from '../configure.json';

    const weather = {
        temperature: {
            unit: '',
            value: 0,
        },
        description: '',
        iconId: '',
    };

    weather.temperature.unit = `${configure.default.unit}`;

    let tempUnit = `${configure.default.tempUnit}`;
    const KELVIN = 273.15;
    // Use your own key for the Weather, Get it here: https://openweathermap.org/

    const key = __myapp.env.API_KEY // get the key from the .env file you set up
    // Set Position function
    setPosition();


    function getWeather() {
    let api = `https://api.openweathermap.org/data/2.5/weather?q=${configure.default.city}&appid=${key}`;
    fetch(api)
        .then(function (response) {
        let data = response.json();
        return data;
        })
        .then(function (data) {
        let celsius = Math.floor(data.main.temp - KELVIN);
        weather.temperature.value =
            tempUnit == 'C' ? celsius : Math.floor((celsius * 9) / 5 + 32);
        weather.description = data.weather[0].description;
        weather.iconId = data.weather[0].icon;
        })}

    function setPosition() {
        getWeather();
    }
</script>

<style>
    .container{
        display: inline-block;
        position: relative;
        width: 400px;
        height: 1000px;
    }
    .icon {
        width: 100%;
    }
    .city{
        color: var(--time);
    }
    .temperature{
        font-size: 1.4em;
        bottom: 100px;
        position: absolute;
        color: var(--temperature);
    }
</style>

<div class="container">
    <div><img class = "icon" src = "/Icons/{weather.iconId}.png" alt = {weather.description}></div>
    <div class="city">{configure.default.city}</div>
    <div class="temperature">{weather.temperature.value} °{tempUnit}</div>
</div>