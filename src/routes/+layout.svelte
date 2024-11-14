<script lang="ts">
	import '../app.css';
	import { goto } from '$app/navigation';
	let { children } = $props();
	let selectedCharacter = null;
	const characters = [
		'워로드',
		'디스트로이어',
		'버서커',
		'홀리나이트',
		'슬레이어',
		'스트라이커',
		'브레이커',
		'기공사',
		'배틀마스터',
		'인파이터',
		'창술사',
		'아르카나',
		'소서리스',
		'서머너',
		'바드',
		'스카우터',
		'블래스터',
		'데빌헌터',
		'호크아이',
		'건슬링어',
		'데모닉',
		'블레이드',
		'리퍼',
		'소울이터',
		'기상술사',
		'도화가'
	];
	const characterCodes = {
		워로드: 'gl',
		디스트로이어: 'dt',
		버서커: 'bk',
		홀리나이트: 'hk',
		슬레이어: 'bkf',
		스트라이커: 'bmm',
		브레이커: 'ifm',
		기공사: 'so',
		배틀마스터: 'bm',
		인파이터: 'if',
		창술사: 'lm',
		아르카나: 'ac',
		소서리스: 'scs',
		서머너: 'sm',
		바드: 'bd',
		스카우터: 'sc',
		블래스터: 'bs',
		데빌헌터: 'dh',
		호크아이: 'he',
		건슬링어: 'dhf',
		데모닉: 'dm',
		블레이드: 'bl',
		리퍼: 'rp',
		소울이터: 'se',
		기상술사: 'wa',
		도화가: 'yy'
	};

	let isSidebarOpen = true;

	function toggleSidebar() {
		isSidebarOpen = !isSidebarOpen;
	}

	function navigateToCharacterPage(character, option) {
		const characterCode = characterCodes[character];
		if (characterCode) {
			const url = option
				? `/characters/${characterCode}?option=${option}`
				: `/characters/${characterCode}`;
			goto(url);
		}
	}
</script>

<div class="sidebar" class:is-open={isSidebarOpen}>
	<button onclick={toggleSidebar} class="toggle-button">
		{isSidebarOpen ? '접기' : '펼치기'}
	</button>
	<div class="character-tabs">
		{#each characters as character}
			<div class="character-button">
				<button class="w-full bg-red-300">
					{character}
				</button>
				<div class="hover-options">
					{#if character === '워로드'}
						<button onclick={() => navigateToCharacterPage('워로드', 1)}>고기</button>
						<button onclick={() => navigateToCharacterPage('워로드', 2)}>전태</button>
					{:else if character === '디스트로이어'}
						<button onclick={() => navigateToCharacterPage('디스트로이어', 1)}>분망</button>
						<button onclick={() => navigateToCharacterPage('디스트로이어', 2)}>중수</button>
					{:else if character === '버서커'}
						<button onclick={() => navigateToCharacterPage('버서커', 1)}>광기</button>
						<button onclick={() => navigateToCharacterPage('버서커', 2)}>비기</button>
					{:else if character === '홀리나이트'}
						<button onclick={() => navigateToCharacterPage('홀리나이트', 1)}>축오</button>
						<button onclick={() => navigateToCharacterPage('홀리나이트', 2)}>심판</button>
					{:else if character === '슬레이어'}
						<button onclick={() => navigateToCharacterPage('슬레이어', 1)}>처단</button>
						<button onclick={() => navigateToCharacterPage('슬레이어', 2)}>포식</button>
					{:else if character === '스트라이커'}
						<button onclick={() => navigateToCharacterPage('스트라이커', 1)}>일격</button>
						<button onclick={() => navigateToCharacterPage('스트라이커', 2)}>오의</button>
					{:else if character === '브레이커'}
						<button onclick={() => navigateToCharacterPage('브레이커', 1)}>수라</button>
						<button onclick={() => navigateToCharacterPage('브레이커', 2)}>권왕</button>
					{:else if character === '기공사'}
						<button onclick={() => navigateToCharacterPage('기공사', 1)}>역천</button>
						<button onclick={() => navigateToCharacterPage('기공사', 2)}>세맥</button>
					{:else if character === '배틀마스터'}
						<button onclick={() => navigateToCharacterPage('배틀마스터', 1)}>오의</button>
						<button onclick={() => navigateToCharacterPage('배틀마스터', 2)}>체술</button>
					{:else if character === '인파이터'}
						<button onclick={() => navigateToCharacterPage('인파이터', 1)}>체술</button>
						<button onclick={() => navigateToCharacterPage('인파이터', 2)}>충단</button>
					{:else if character === '창술사'}
						<button onclick={() => navigateToCharacterPage('창술사', 1)}>절제</button>
						<button onclick={() => navigateToCharacterPage('창술사', 2)}>절정</button>
					{:else if character === '아르카나'}
						<button onclick={() => navigateToCharacterPage('아르카나', 1)}>황후</button>
						<button onclick={() => navigateToCharacterPage('아르카나', 2)}>황제</button>
					{:else if character === '소서리스'}
						<button onclick={() => navigateToCharacterPage('소서리스', 1)}>점화</button>
						<button onclick={() => navigateToCharacterPage('소서리스', 2)}>환류</button>
					{:else if character === '서머너'}
						<button onclick={() => navigateToCharacterPage('서머너', 1)}>상소</button>
						<button onclick={() => navigateToCharacterPage('서머너', 2)}>교감</button>
					{:else if character === '바드'}
						<button onclick={() => navigateToCharacterPage('바드', 1)}>용맹</button>
						<button onclick={() => navigateToCharacterPage('바드', 2)}>절구</button>
					{:else if character === '스카우터'}
						<button onclick={() => navigateToCharacterPage('스카우터', 1)}>변신</button>
						<button onclick={() => navigateToCharacterPage('스카우터', 2)}>기술</button>
					{:else if character === '블래스터'}
						<button onclick={() => navigateToCharacterPage('블래스터', 1)}>포격</button>
						<button onclick={() => navigateToCharacterPage('블래스터', 2)}>화강</button>
					{:else if character === '데빌헌터'}
						<button onclick={() => navigateToCharacterPage('데빌헌터', 1)}>강무</button>
						<button onclick={() => navigateToCharacterPage('데빌헌터', 2)}>모름</button>
					{:else if character === '호크아이'}
						<button onclick={() => navigateToCharacterPage('호크아이', 1)}>죽습</button>
						<button onclick={() => navigateToCharacterPage('호크아이', 2)}>두동</button>
					{:else if character === '건슬링어'}
						<button onclick={() => navigateToCharacterPage('건슬링어', 1)}>피메</button>
						<button onclick={() => navigateToCharacterPage('건슬링어', 2)}>사시</button>
					{:else if character === '데모닉'}
						<button onclick={() => navigateToCharacterPage('데모닉', 1)}>충</button>
						<button onclick={() => navigateToCharacterPage('데모닉', 2)}>억제</button>
					{:else if character === '블레이드'}
						<button onclick={() => navigateToCharacterPage('블레이드', 1)}>잔재</button>
						<button onclick={() => navigateToCharacterPage('블레이드', 2)}>버스트</button>
					{:else if character === '리퍼'}
						<button onclick={() => navigateToCharacterPage('리퍼', 1)}>달소</button>
						<button onclick={() => navigateToCharacterPage('리퍼', 2)}>갈증</button>
					{:else if character === '소울이터'}
						<button onclick={() => navigateToCharacterPage('소울이터', 1)}>만월</button>
						<button onclick={() => navigateToCharacterPage('소울이터', 2)}>모름</button>
					{:else if character === '기상술사'}
						<button onclick={() => navigateToCharacterPage('기상술사', 1)}>이슬비</button>
						<button onclick={() => navigateToCharacterPage('기상술사', 2)}>질풍</button>
					{:else if character === '도화가'}
						<button onclick={() => navigateToCharacterPage('도화가', 1)}>만개</button>
						<button onclick={() => navigateToCharacterPage('도화가', 2)}>저달</button>
					{/if}
				</div>
			</div>
		{/each}
	</div>
</div>

<div class="content">
	<p>선택된 캐릭터: {selectedCharacter}</p>
	{@render children()}
</div>

<style>
	.sidebar {
		position: fixed;
		left: 0;
		top: 0;
		bottom: 0;
		width: 250px;
		background-color: #f8f8f8;
		overflow-y: auto;
		transition: transform 0.3s ease;
		transform: translateX(-100%);
	}

	.sidebar.is-open {
		transform: translateX(0);
	}

	.toggle-button {
		position: absolute;
		top: 10px;
		right: -50px;
		transform: rotate(90deg);
		border: none;
		cursor: pointer;
		padding: 5px 10px;
	}

	.content {
		margin-left: 250px;
		padding: 20px;
		transition: margin-left 0.3s ease;
	}

	.sidebar:not(.is-open) + .content {
		margin-left: 0;
	}

	.character-tabs {
		display: flex;
		flex-direction: column;
	}

	.character-button {
		position: relative;
		margin: 5px;
	}

	.character-button button {
		padding: 20px 10px;
		cursor: pointer;
		border: none;
		border-radius: 8px;
	}

	.hover-options {
		display: none;
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		justify-content: space-between;
		align-items: center;
	}

	.character-button:hover .hover-options {
		display: flex;
	}

	.hover-options button {
		flex: 1;
		height: 100%;
		margin: 0;
		padding: 5px 0;
		cursor: pointer;
		border: none;
		background-color: rgb(225, 116, 116);
		border-radius: 8px;
	}
</style>
