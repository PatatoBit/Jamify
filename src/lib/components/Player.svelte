<script>
	import Youtube, { PlayerState } from 'svelte-youtube';

	export let src;

	let last = src.substring(src.lastIndexOf('/') + 1, src.length);

	console.log(last, src);

	const options = {
		height: '390',
		width: '640',
		playerVars: {
			// https://developers.google.com/youtube/player_parameters
			autoplay: 1
		}
	};

	function onStateChange(event) {
		console.table(event.detail.data);
		if (event.detail.data === PlayerState.ENDED) alert('video ended');
	}
</script>

<Youtube videoId={last} {options} on:stateChange={(event) => onStateChange(event)} />
