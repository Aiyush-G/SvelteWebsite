<script>
	import { count1 } from './stores.js';

	function increment() {
		count1.update((n) => n + 1);
	}
</script>

<button on:click={increment}>
	+
</button>
