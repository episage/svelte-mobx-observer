## Svelte MobX Observer

### Example

```svelte
<script>
  import { observable } from "mobx";
  import Observer from "svelte-mobx-observer";

  let foo = observable({ // standard, MobX observable
    deeply: {
      nested: {
        counter: 1
      }
    }
  });

  let counterVisible = true; // works with conditionals as well

  window.foo = foo; // you can use the "foo" observable everywhere, it works from window and **nested components** AS WELL
</script>

<Observer>
  <main on:click={() => foo.deeply.nested.counter++}>
	<div on:click={()=> counterVisible = !counterVisible}>Counting up... click me to toggle</div>
	{#if counterVisible}
		<h1>{foo.deeply.nested.counter}</h1>	
	{/if}
  </main>
</Observer>

<style>
main {
	cursor: pointer;
}
</style>
```

### Installation

```
yarn add svelte-mobx-observer
```

### Motivation

Svelte subscription system lacks possibility to observe nested objects.

### Method

This is a hand crafted component on a basis of Svelte generated code.

### Requirements

 - MobX `^5.15.4`
 - Svelte `^3.24.0`


