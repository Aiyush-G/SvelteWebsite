<script>
	import { count1 } from './stores.js';

	function reset() {
		count1.set(0);
	}
</script>

<button on:click={reset}>
	reset
</button>
