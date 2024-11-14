<script>
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	let character;
	let numbers = [];

	// 반응형으로 설정
	$: character = $page.params.character;
	$: option = $page.url.searchParams.get('option');

	$: {
		numbers = getNumbers();
		console.log('zzzz');
		console.log(option);
	}

	function getNumbers() {
		if (Number(option) === 2) {
			return Array.from({ length: 100 }, (_, i) => 100 - i); // 100~1
		} else {
			return Array.from({ length: 100 }, (_, i) => i + 1); // 1~100
		}
	}

	onMount(() => {
		// 페이지가 처음 로드될 때 character와 option 값을 설정
		character = $page.params.character;
		option = $page.url.searchParams.get('option');
	});
</script>

<div class="align-center flex h-lvh flex-wrap justify-center">
	{#each numbers as num}
		<div class="tooltip">
			<img
				src={`https://cdn-lostark.game.onstove.com/efui_iconatlas/ark_passive_${character}/ark_passive_${character}_${num}.png`}
				style="display: none;"
				on:load={(event) => (event.target.style.display = 'block')}
				on:error={(event) => (event.target.style.display = 'none')}
				title={num}
			/>
		</div>
	{/each}
</div>
