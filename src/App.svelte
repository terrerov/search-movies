<script>
import Counter from './Counnter.svelte'
import Input from './Input.svelte'

const commonProps = {maxCounter : 5}

let hereKitty = false;

const handleMouseenter = () => hereKitty = true;
const handleMouseleave = () => hereKitty = false;

</script>
<style>
	h1{
		font-size: 32px;

	}
	section{
		align-items: center;
		display: flex;
		flex-direction: column;
	}
	img {
		position: absolute;
		left: 0;
		bottom: -60px;
		transform: translate(-80%, 0) rotate(-30deg);
		transform-origin: 100% 100%;
		transition: transform 0.4s;
	}

	.curious {
		transform: translate(-15%, 0) rotate(0deg);
	}

	:global(body) {
		overflow: hidden;
	}
</style>
<section>
 <h1>Search Movies 🍿</h1>
 <Input />
</section>

<svelte:body
	on:mouseenter={handleMouseenter}
	on:mouseleave={handleMouseleave}
/>

<!-- creative commons BY-NC http://www.pngall.com/kitten-png/download/7247 -->
<img
	class:curious={hereKitty}
	alt="Kitten wants to know what's going on"
	src="http://www.pngall.com/wp-content/uploads/2016/05/Kitten-Free-PNG-Image.png"
>
