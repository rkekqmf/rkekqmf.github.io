<script lang="ts">
	// 2자리 알파벳 조합 생성 함수
	function generateTwoLetterCombinations() {
		const alphabet = 'abcdefghijklmnopqrstuvwxyz';
		let combinations = [];

		for (let i = 0; i < alphabet.length; i++) {
			for (let j = 0; j < alphabet.length; j++) {
				combinations.push(alphabet[i] + alphabet[j]);
			}
		}

		return combinations;
	}

	// 3자리 알파벳 조합 생성 함수
	function generateThreeLetterCombinations() {
		const alphabet = 'abcdefghijklmnopqrstuvwxyz';
		let combinations = [];

		for (let i = 0; i < alphabet.length; i++) {
			for (let j = 0; j < alphabet.length; j++) {
				for (let k = 0; k < alphabet.length; k++) {
					combinations.push(alphabet[i] + alphabet[j] + alphabet[k]);
				}
			}
		}

		return combinations;
	}

	let twoLetterCombinations = generateTwoLetterCombinations();
	let threeLetterCombinations = generateThreeLetterCombinations();

	// 이미지 URL 생성 함수
	function generateImageUrls(characterCodes: string) {
		let urls = [];
		for (let num = 1; num <= 5; num++) {
			urls.push(
				`https://cdn-lostark.game.onstove.com/efui_iconatlas/ark_passive_${characterCodes}/ark_passive_${characterCodes}_${num}.png`
			);
		}
		return urls;
	}
</script>

<div class="flex h-screen flex-col items-center justify-center">
	<div class="grid">
		{#each twoLetterCombinations as 조합}
			{#each generateImageUrls(조합) as url}
				<img
					src={url}
					alt={조합}
					title={조합}
					class="hidden"
					on:load={(event) =>
						(event.target as HTMLImageElement).classList.replace('hidden', 'visible')}
					on:error={(event) => console.log('Error loading image:', url)}
				/>ㅇㅇㅇ
			{/each}
		{/each}

		{#each threeLetterCombinations as 조합}
			{#each generateImageUrls(조합) as url}
				<img
					src={url}
					alt={조합}
					title={조합}
					class="hidden"
					on:load={(event) =>
						(event.target as HTMLImageElement).classList.replace('hidden', 'visible')}
					on:error={(event) => console.log('Error loading image:', url)}
				/>
			{/each}
		{/each}
	</div>
</div>

<style>
	.grid {
		display: grid;
		grid-template-columns: repeat(10, minmax(0, 1fr));
		gap: 10px;
		width: 100%;
	}
	.hidden {
		display: none;
	}
	.visible {
		display: block;
	}
</style>
