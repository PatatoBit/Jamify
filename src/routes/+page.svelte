<script lang="ts">
	import Player from '../lib/components/Player.svelte';

	const videos = [
		'https://youtu.be/Sm-Bpkf0ndA',
		'https://youtu.be/LWVIXezoIIo',
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

<Player {id} {nextVideo} />
