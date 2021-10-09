<script>
  let count = 1;
  //problem
    // let double = count*2;
    // let qara = double *2;
  //solve

  // $: console.log('count', count);
  $: double = count * 2;
  $: console.log("double", double);
  $: qara = double * 2;
  $: console.log("qara", qara);
  
  const increment = () => {
    count++;
    // double = count*2;
  };
  const decrement = () => {
    count--;
    // double = count*2;
  };
  const multiply = () => {
    count = count * count;
    // double = count*2;
  };
  const divide = () => {
    count = count / count;
    // double = count*2;
  };
  const free = () => {
    //not update state
    console.log('double: ',double);
    console.log('qara: ',qara);
  };
</script>

<button on:click={decrement}>-</button>
{count}*2={count * 2} *2 ={qara}
<button on:click={increment}>+</button>
<button on:click={multiply}>x</button>
<button on:click={divide}>:</button>
<button on:click={free}>Click me !</button>
