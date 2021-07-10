<script>
	export let initialCounter = 0;
    export let maxCounter = 9;
	let contador = initialCounter;

	function handleClic (){
		contador++
	}

    $: isEvenOrOdd = contador % 2 == 0 ? 'Is Even' : 'Is Odd'
    $: {
        if (contador > maxCounter){
            contador= maxCounter
        }
    }
</script>

<main>
	<button on:click={handleClic}>Cambiar nombre</button>
	<span>{contador}</span>
    <span>{isEvenOrOdd}</span>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	span {
		color: #09f;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>