<script lang="ts">
  import { Reactive } from "$lib/reactive.svelte.js"
  
  // class Reactive {
  //   constructor() {
  //     this.text = 'hello'
  //   }
  //   public text: string = $state('')
  // }

  const react = new Reactive()
  let elt: HTMLElement | null = null

  let json = $derived(JSON.stringify({ text: react.text }))

  $effect(() => {
    const newDiv = document.createElement('div')
    newDiv.textContent = react.text
    elt!.appendChild(newDiv)
  })
</script>

<div>homepage</div>
<div>
  <div>{json}</div>
  <input type="text" bind:value={react.text} />
  <div bind:this={elt}></div>
</div>
