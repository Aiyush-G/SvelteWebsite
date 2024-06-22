<script>
    import { createEventDispatcher } from 'svelte';
  
    const dispatch = createEventDispatcher();
  
    let name = '';
    let email = '';
  
    /**
     * @param {{ preventDefault: () => void; }} event
     */
    function handleSubmit(event) {
      event.preventDefault();
      dispatch('submit', { name, email });
    }
  </script>
  
  <form on:submit={handleSubmit}>
    <label>
      Name:
      <input type="text" bind:value={name} />
    </label>
    <br />
    <label>
      Email:
      <input type="email" bind:value={email} />
    </label>
    <br />
    <button type="submit">Submit</button>
  </form>
  