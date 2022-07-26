<script>
  import DisplayWeather from './lib/DisplayWeather.svelte'
  const key = import.meta.env.VITE_WEATHER_API_KEY
  let city
  let loading = true
  let cityWeather

  function submitCity(){
    if (city ==''  || city ==null)
     return  alert('Enter a City!')
    loading = !loading
    cityWeather = city
    city = ''

  }

</script>


<h1>Check your weather!</h1>
<h4>Please enter your city and Province</h4>
<label for="city">City: </label>
<input bind:value={city} type="text">
<button on:click={submitCity}>Check Weather</button>


{#if !loading}
  <DisplayWeather city={cityWeather}/>
{/if}
