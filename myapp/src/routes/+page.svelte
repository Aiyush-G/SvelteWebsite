<script>
    import Nested from "./Nested.svelte"

    let count = 0;
    let numbers = [1,2,3,4,5,6];
    let colours = ["red", "green", "blue"]
    let currentColour = colours[0]
    let m={x:0, y:0}
    let name = "Bob"

    let a = 1;
    let b = 2;


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

   
    /**
     * @param {{ clientX: number; clientY: number; }} event
     */
    function handleMove(event){
        m.x = event.clientX;
        m.y = event.clientY
    }

    
	let numFavouriteColours = 1;
	
	let colourOptions = ["green", "blue"];

	const formatter = new Intl.ListFormat('en', { style: 'long', type: 'conjunction' });

</script>

<h1>Learning Svelte with {name}</h1>
<input type="text" bind:value={name}>

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

<div on:pointermove={handleMove}>
    The pointer is at {m.x} x {m.y}
</div>

<div
on:pointermove={(e)=> {
    m.x = e.clientX;
    m.y = e.clientY
}}
> The pointer is at {m.x} x {m.y}</div>

<button
on:click|once={()=>alert("waaaa")}
>
    This DIV contains so info that, when you click, will display a message once and once only...
</button>
<!-- on:click={()=> currentColour = colour} -->


<label>
	<input type="number" bind:value={a} min="0" max="10" />
	<input type="range" bind:value={a} min="0" max="10" />
</label>

<label>
	<input type="number" bind:value={b} min="0" max="10" />
	<input type="range" bind:value={b} min="0" max="10" />
</label>

<p>{a} + {b} = {a + b}</p>




<h2>Number of Favourite Colours</h2>

{#each [1, 2, 3] as number}
	<label>
		<input
			type="radio"
			name="numFavouriteColours"
			value={number}
			bind:group={numFavouriteColours}
		/>

		{number} {number === 1 ? 'favourite colour' : 'favourite colours'}
	</label>
{/each}

<h2>Colours</h2>

{#each ['GREEN', 'BLUE', 'RED'] as flavour}
	<label>
		<input
			type="checkbox"
			name="colourOptions"
			value={flavour}
			bind:group={colourOptions}
		/>

		{flavour}
	</label>
{/each}

{#if colourOptions.length === 0}
	<p>Please select at least one colour</p>
{:else if colourOptions.length > numFavouriteColours}
	<p>Can't have more colours optiosn than number of colours you have favourited!</p>
{:else}
	<p>
		You have {numFavouriteColours} {numFavouriteColours === 1 ? 'as a favourite colour' : 'as your favourite colours'}
		of {formatter.format(colourOptions)}
	</p>
{/if}