<script lang="ts">
  import { onMount } from 'svelte';
  import { handleClickOutside } from '../helpers';
  export let x: string;
  export let y: string;

  let answerDialog: HTMLDialogElement;
  onMount(() => {
    answerDialog = document.getElementById('answerDialog') as HTMLDialogElement;
  })

  const checkAnswer = (e: Event) => {
    const answer = parseInt(x) * parseInt(y);
    if (answer === parseInt(e?.target?.value)) {
      console.log('correct');
      answerDialog.close()
    } else {
      console.log('incorrect');
      answerDialog.close();
    }
  }
</script>

<dialog id="answerDialog" on:click={(e) => handleClickOutside(e, answerDialog)}>
  <div>
    <p>{x} x {y} = </p>
    <form on:submit={checkAnswer}>
      <input type="text" on:blur={checkAnswer}>
    </form>
  </div>
</dialog>

<style>
  dialog {
    padding: 20px 25px;
  }
  div {
    display: flex;
  }
  p {
    margin: 0;
    font-size: 24px;
  }
  form {
    margin-left: 10px;
  }
</style>