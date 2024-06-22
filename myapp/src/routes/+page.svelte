<script>
    import Nested from "./Nested.svelte"

    let count = 0;
    let numbers = [1,2,3,4,5,6];
    let colours = ["red", "green", "blue"]
    let currentColour = colours[0]


    $: doubled = count*2;
    // $: console.log(`the count is ${count}`);
    $: console.log(`${numbers}`);

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

    function addNumber(){
        //numbers.push(numbers.length + 1);
        //numbers = numbers;

        numbers = [...numbers, numbers.length + 1]
        
    }

    
    /**
     * @param {string} colour
     */
    function updateColour(colour){
        currentColour = colour
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
{#if count > 15}
    <p>If count gets to 20 it will RESET</p>
{:else if count < 3}
    <p>Count is tiny!! Add some extra numbers to it!!</p>
{:else}
    <p>Count is at a healthy number</p>
{/if}


<button on:click={addNumber}>Add a Number!!</button>

<Nested answer={"3"} />

<h1 style="color: {currentColour};">Select the theme colour below, current is {currentColour}</h1>
{#each colours as colour}
    <button
    style="background-color: {colour}"
    on:click={()=> updateColour(colour)}
    
    
    ></button>
{/each}



<!-- on:click={()=> currentColour = colour} -->