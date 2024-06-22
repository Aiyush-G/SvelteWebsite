<script>
    let count = 0;
    $: doubled = count*2;
    $: console.log(`the count is ${count}`);

    $: if (count >= 20){
        alert("THE COUNT IS SUPER HIGH, gonna reset it now");
        count = 0;
    }
    
    function increment(){
        count+= 1;
    }

    function reset(){
        count = 0;
    }
</script>

<h1>Learning Svelte!</h1>

<button on:click={increment}>
    Clicked {count}
</button>
<button on:click={reset}>
    Reset the count to 0 
</button>

<p>Count Doubled is {doubled}</p>
