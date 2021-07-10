<script>
    import Movie from './Movie.svelte'
    let value = ''
    let response = []

    const handleInput = (event) => 
    value = event.target.value
    
    $: if(value.length > 2){
        response = fetch(`https://www.omdbapi.com/?s=${value}&apikey=f895cb62`)
        //.then(res => !res.ok() && Error('Algo pasó mientras buscaba la película'))
        .then(res => res.json())
        .then(apiResponse => apiResponse.Search || [])
    }
</script>
<input placeholder="Search movies" value = {value} on:input={handleInput} />
{#await response}
    <strong>loading...</strong>
        {:then movies}
        {#each movies as {Title, Poster, Year}}
         <Movie
            title={Title}
            poster={Poster}
            year={Year}
        />         
        {:else}
        <strong>no hay resultados :(</strong>
        {/each}

{/await}


