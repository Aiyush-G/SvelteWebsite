<script>
    let count = 0;
    let numbers = [1,2,3,4,5,6];


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
</script>

<h1>Learning Svelte!</h1>

<button on:click={increment}>
    Clicked {count}
</button>

<button on:click={reset}>
    Reset the count to 0 
</button>
<p>Count Doubled is {doubled}</p>

<button on:click={addNumber}>Add a Number!!</button>
