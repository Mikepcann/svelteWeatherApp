<script>
    import WeatherTable from "./WeatherTable.svelte";
    import { onMount } from 'svelte'
    const key = import.meta.env.VITE_WEATHER_API_KEY
    export let city
    const url = `http://api.weatherapi.com/v1/current.json?key=${key}&q=${city}&aqi=no`

    // http://api.weatherapi.com/v1/current.json?key=5daf75056084427bbc9221332222507&q=calgary&aqi=no

    let result 

    onMount(async ()=> {
        try {
            const serverReturn = await fetch(url)
            result = await serverReturn.json()
        } catch (error) {
            console.log("!!!",error.message)
        }
    })
    
</script>



{#if result}
    <h1>The Weather!!</h1>
    <WeatherTable {result}/>
{/if}
