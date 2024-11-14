<script>
	// 캐릭터 목록

	let activeTab = '진화';

	function selectTab(tab) {
		activeTab = tab;
	}

	const validNumbers = [
		{ num: 1, tooltip: '치명' },
		{ num: 2, tooltip: '특화' },
		{ num: 3, tooltip: '제압' },
		{ num: 4, tooltip: '신속' },
		{ num: 5, tooltip: '인내' },
		{ num: 6, tooltip: '숙련' },
		{ num: 16, tooltip: '끝없는 마나' },
		{ num: 12, tooltip: '금단의주문' },
		{ num: 29, tooltip: '예리한감각' },
		{ num: 34, tooltip: '한계돌파' },
		{ num: 22, tooltip: '최적화훈련' },
		{ num: 19, tooltip: '축복의여신' },
		{ num: 14, tooltip: '무한한마력' },
		{ num: 27, tooltip: '혼신의강타' },
		{ num: 32, tooltip: '일격' },
		{ num: 35, tooltip: '파괴전차' },
		{ num: 23, tooltip: '타이밍 지배' },
		{ num: 33, tooltip: '정열의 춤사위' },
		{ num: 20, tooltip: '뭉툭한 가시' },
		{ num: 21, tooltip: '음속 돌파' },
		{ num: 38, tooltip: '인파이팅' },
		{ num: 18, tooltip: '입식타격가' },
		{ num: 24, tooltip: '마나용광로' },
		{ num: 25, tooltip: '안정된관리자' }
	];
</script>

<div class="tabs">
	<button on:click={() => selectTab('진화')} class:active={activeTab === '진화'}>진화</button>
	<button on:click={() => selectTab('깨달음')} class:active={activeTab === '깨달음'}>깨달음</button>
	<button on:click={() => selectTab('공용깨달음')} class:active={activeTab === '공용깨달음'}
		>공용깨달음</button
	>
	<button on:click={() => selectTab('도약')} class:active={activeTab === '도약'}>도약</button>
</div>

<div class="content">
	{#if activeTab === '진화'}
		<div class="grid">
			{#each validNumbers as item}
				<div class="tooltip">
					<img
						src={`https://cdn-lostark.game.onstove.com/efui_iconatlas/ark_passive_evolution/ark_passive_evolution_${item.num}.png`}
						on:error={(event) => (event.target.style.display = 'none')}
					/>
					<span class="tooltiptext">
						{item.tooltip}
					</span>
				</div>
			{/each}
		</div>
	{:else if activeTab === '깨달음'}
		<div class="grid">
			{#each Array.from({ length: 100 }, (_, i) => i + 1) as num}
				<div class="tooltip">
					<img
						src={`https://cdn-lostark.game.onstove.com/efui_iconatlas/ark_passive_${characterCodes[selectedCharacter] || 'default'}/ark_passive_${characterCodes[selectedCharacter] || 'default'}_${num}.png`}
						on:error={(event) => (event.target.style.display = 'none')}
					/>
					<span class="tooltiptext">
						{num}
					</span>
				</div>
			{/each}
		</div>
	{:else if activeTab === '공용깨달음'}
		<div class="grid">
			{#each Array.from({ length: 100 }, (_, i) => i + 1) as num}
				<div class="tooltip">
					<img
						src={`https://cdn-lostark.game.onstove.com/efui_iconatlas/ark_passive_01/ark_passive_01_${num}.png`}
						on:error={(event) => (event.target.style.display = 'none')}
					/>
					<span class="tooltiptext">
						{num}
					</span>
				</div>
			{/each}
		</div>
	{:else if activeTab === '도약'}
		<div class="grid">
			{#each Array.from({ length: 100 }, (_, i) => i + 1) as num}
				<div class="tooltip">
					<img
						src={`https://cdn-lostark.game.onstove.com/efui_iconatlas/ark_passive_02/ark_passive_02_${num}.png`}
						on:error={(event) => (event.target.style.display = 'none')}
					/>
					<span class="tooltiptext">
						{num}
					</span>
				</div>
			{/each}
		</div>
	{/if}
</div>

<style>
	.tabs {
		display: flex;
		justify-content: center;
		margin-bottom: 20px;
	}

	button {
		padding: 10px 20px;
		margin: 0 5px;
		cursor: pointer;
		border: none;
		background-color: #f0f0f0;
	}

	.active {
		background-color: #007bff;
		color: white;
	}

	.content {
		text-align: center;
		justify-content: center;
		display: flex;
	}

	.grid {
		display: grid;
		grid-template-columns: repeat(6, minmax(0, 1fr));
		gap: 10px;
		width: 100%;
	}

	.tooltip {
		position: relative;
		width: 100%;
		box-sizing: border-box;
	}

	.tooltiptext {
		display: none;
		position: absolute;
		background-color: #555;
		color: #fff;
		text-align: center;
		padding: 5px 0;
		border-radius: 6px;
		bottom: 125%;
		left: 50%;
		transform: translateX(-50%);
		z-index: 1;
		opacity: 0;
		transition: opacity 0.3s;
	}

	.tooltip:hover .tooltiptext {
		display: block;
		opacity: 1;
	}
</style>
