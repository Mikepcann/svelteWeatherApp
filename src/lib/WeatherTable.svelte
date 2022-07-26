<script>
    import { fade, fly } from 'svelte/transition';
    export let result
    
    let isCelcius = true
    function convert(){
        isCelcius = !isCelcius
    }

</script>

<table in:fly="{{x: 700, duration: 1000}}" out:fade>
    <th>City</th>
    <th>Region</th>
    <th>Country</th>
    <th>Current Temp</th>
    <tr>
        <td>{result.location.name}</td>
        <td>{result.location.region}</td>
        <td>{result.location.country}</td>
       {#if isCelcius}
            <td> {result.current.temp_c} &#176;C  </td>
            {:else}
            <td>{result.current.temp_f} &#176;F</td>
        {/if}
        
</tr>
</table>
<button on:click={convert}>Convert C/F</button>

<style>
    table, th, td{
        border: 1px solid black;
        border-collapse: collapse;
        padding: 10px 25px;
        text-align: left;
        margin:10px;
    }
</style>
