## Svelte MobX Observer

### Motivation

Svelte subscription system lacks possibility to observe values in deeply nested objects. This Svelte component lets you listen on MobX observable changes and update accordingly.

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

  window.foo = foo; // you can use the "foo" observable anyywhere, it works at window and inside **nested components** AS WELL
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

### Starter project

[GitHub: Svelte - MobX Starter](https://github.com/episage/svelte-mobx-observer-starter)

### Installation

```
yarn add svelte-mobx-observer
```

### Method

This is a hand crafted component on a basis of Svelte generated code.

 - `stage1` - dir with Svelte generated files from `Component.svelte`
 - `stage2` - dist dir with hand modified files from `stage1`

### Requirements

 - MobX `^5.15.4`
 - Svelte `^3.24.0`


