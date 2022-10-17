<script lang="ts">
  import { onMount } from 'svelte';

  import AnswerDialog from '../components/AnswerDialog.svelte';

  const columns = [0,1,2,3,4,5,6,7,8,9,10,11,12];
  const rows = [1,2,3,4,5,6,7,8,9,10,11,12];
  let x: string;
  let y: string;

  let answerDialog: HTMLDialogElement;
  onMount(() => {
    answerDialog = document.getElementById('answerDialog') as HTMLDialogElement;
  })

  const testAnswer = (firstNum: string, secondNum: string) => {
    x = firstNum;
    y = secondNum;
    answerDialog.showModal();
  }
</script>

<main>
  <AnswerDialog x={x} y={y}/>
  {#each columns as column}
		<div>{column}</div>
	{/each}
  {#each rows as row}
    <div>{row}</div>
    <button on:click={() => testAnswer(row, columns[row - row + 1])}><span class="hide">{row * columns[row - row + 1]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 2])}><span class="hide">{row * columns[row - row + 2]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 3])}><span class="hide">{row * columns[row - row + 3]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 4])}><span class="hide">{row * columns[row - row + 4]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 5])}><span class="hide">{row * columns[row - row + 5]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 6])}><span class="hide">{row * columns[row - row + 6]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 7])}><span class="hide">{row * columns[row - row + 7]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 8])}><span class="hide">{row * columns[row - row + 8]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 9])}><span class="hide">{row * columns[row - row + 9]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 10])}><span class="hide">{row * columns[row - row + 10]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 11])}><span class="hide">{row * columns[row - row + 11]}</span></button>
    <button on:click={() => testAnswer(row, columns[row - row + 12])}><span class="hide">{row * columns[row - row + 12]}</span></button>
  {/each}
</main>

<style>
  main {
    display: grid;
    grid-template-columns: repeat(13, 1fr);
    gap: 5px;
  }
  div {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0;
    border: 1px solid black;
    border-radius: 2px;
    font-size: 18px;
    width: 50px;
    height: 50px;
  }
  button {
    width: 50px;
    height: 50px;
    border: 1px solid black;
    border-radius: 2px;
    margin: 0;
    font-size: 18px;
    background-color: #fff;
  }
  span.hide {
    visibility: hidden;
  }
</style>
