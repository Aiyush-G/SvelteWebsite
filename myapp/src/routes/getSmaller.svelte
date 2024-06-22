<script>
	import { count1 } from './stores.js';

	function decrement() {
		count1.update((n) => n - 1);
	}
</script>

<button on:click={decrement}>
	-
</button>