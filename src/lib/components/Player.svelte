<script>
	import Youtube, { PlayerState } from 'svelte-youtube';

	export let id;
	export let nextVideo;

	console.log(id);

	const options = {
		height: '390',
		width: '640',
		playerVars: {
			// https://developers.google.com/youtube/player_parameters
			autoplay: 1
		}
	};
</script>

<Youtube videoId={id} {options} on:end={(event) => nextVideo(event)} />
