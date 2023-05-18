<script lang="ts">
	import Player from '../lib/components/Player.svelte';

	const videos = [
		'https://youtu.be/LWVIXezoIIo',
		'https://youtu.be/Sm-Bpkf0ndA',
		'https://youtu.be/dJ9uVVNWClk',

		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk',

		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk',
		'https://youtu.be/dJ9uVVNWClk'
	];

	let i: number = 0;
	let id = videos[i].substring(videos[i].lastIndexOf('/') + 1);

	function nextVideo(event) {
		i++;
		id = videos[i].substring(videos[i].lastIndexOf('/') + 1);
		console.log('Next video: ', videos[i]);
		console.log(id, i);

		event.detail.target.loadVideoById(id);
	}
</script>

<div class="fullflex">
	<h3>join now at jam.patato.live/<span class="title">XYZA</span></h3>

	<div class="content">
		<div class="side">
			<Player {id} {nextVideo} />
			<button class="add">Add a song!</button>
		</div>

		<div class="side">
			<div class="songs">
				{#each videos as video}
					<!-- content here -->
					<a href={`#${videos.indexOf(video)}`} class="song">
						<h2 id={videos[video]}>{video}</h2>
					</a>
				{/each}
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	h3 {
		margin-bottom: 3rem;
	}

	.content {
		position: relative;
		max-width: 75rem;
		gap: 2rem;
		padding: 0.5rem;

		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: center;
		/* align-items: center; */

		/* border: 1px solid red; */
	}

	.side {
		display: flex;
		flex-direction: column;
		flex: 1 1 0%;
		width: 100%;
		height: 30rem;
		align-items: center;
		/* justify-content: center; */
	}

	.add {
		font-size: 2rem;
		padding: 1.5rem;
		font-family: 'Jetbrains Mono', sans-serif;
		border: 2px solid black;
		background-color: #209c20;
	}

	.songs {
		display: inline-block;
		width: 100%;
		max-height: 100%;
		overflow-y: auto;

		display: flex;
		flex-direction: column;
		padding: 1rem;
		gap: 0.5rem;
		/* justify-content: center; */
		border: 2px solid black;
		.song {
			padding: 1rem;
			border: 1px solid rgb(196, 196, 196);
		}
	}
</style>
