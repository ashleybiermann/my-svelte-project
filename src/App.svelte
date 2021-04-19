<script>
  import Child from './components/Child.svelte';
	import ObjectProps from './components/ObjectProps.svelte';
	import Each from './components/Each.svelte';
	import KeyedEach from './components/KeyedEach.svelte';

  export let name; // name is a prop that will get passed in by parent
  let count = 0;
  $: doubled = count * 2; // $: needs to be computed from other parts, is a reactive declaration

  $: if (count >= 10) {
    console.log(`that count was WAY too high`);
    alert(`count is dangerously high! It will be reset to 0 now`);
    count = 0;
  }
  function handleClick() {
    count += 1;
  }

  let numbers = [1, 2, 3, 4];
  $: sum = numbers.reduce((t, n) => t + n, 0);
  function addNumber() {
    // name of the variable to be updated must appear on left of = operator
    numbers = [...numbers, numbers.length + 1];
  }

	const pkgOfProps = {
		name: 'Callie',
		age: 7,
		color: 'fawn',
		pet: 'dog'
	};

	let user = { loggedIn: false }
	function toggle() {
		user.loggedIn = !user.loggedIn;
	}

	$: console.log('logged in status: ', user.loggedIn);

</script>

<main>
  <h1>Hello {name}!</h1>
  <button on:click={handleClick}>
    Clicked {count}
    {count === 1 ? "time" : "times"}
  </button>
  <p>{count} doubled is {doubled}</p>

  <hr/>

  <button on:click={addNumber}> Add next number in sequence </button>
  <p>{numbers.join(" + ")} = {sum}</p>

  <hr/>

  <Child answer={42} />

	<hr/>

	<ObjectProps {...pkgOfProps} />

	<hr/>

	{#if user.loggedIn}
	<button on:click={toggle}>
		Log out
	</button>

	{:else}
	<button on:click={toggle}>
		Log in
	</button>
	{/if}

	<hr/>

	<Each />

</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
