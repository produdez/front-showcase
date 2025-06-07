<script>
  import { onMount } from 'svelte';

  let greeting = $state('Hello');
  let name = $state('Welcome to test-page');
  let isVisible = $state(false);

  onMount(() => {
    setTimeout(() => {
      isVisible = true;
    }, 500);
  });
</script>

<main>
  <div class="welcome-container" class:visible={isVisible}>
    <div class="welcome-card">
      <div class="avatar">
        <div class="face">
          <div class="eyes">
            <div class="eye"></div>
            <div class="eye"></div>
          </div>
          <div class="mouth"></div>
        </div>
      </div>

      <h1>{greeting}</h1>
      <h2>{name}</h2>

      <div class="buttons">
        <button onclick={() => greeting = 'Hi there!'}>Say Hi</button>
        <button onclick={() => greeting = 'Welcome!'}>Welcome</button>
        <button onclick={() => greeting = 'Hello'}>Reset</button>
      </div>
    </div>
  </div>
</main>

<style>
  main {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background-color: #f9f7ff;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  .welcome-container {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.8s ease, transform 0.8s ease;
  }

  .visible {
    opacity: 1;
    transform: translateY(0);
  }

  .welcome-card {
    background-color: white;
    border-radius: 20px;
    padding: 2rem;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
    text-align: center;
    max-width: 500px;
    width: 100%;
  }

  h1 {
    color: #7c5cff;
    margin-bottom: 0.5rem;
    font-size: 2.5rem;
  }

  h2 {
    color: #666;
    font-weight: 400;
    margin-top: 0;
    margin-bottom: 2rem;
  }

  .buttons {
    display: flex;
    gap: 1rem;
    justify-content: center;
    margin-top: 2rem;
  }

  button {
    background-color: #7c5cff;
    color: white;
    border: none;
    padding: 0.75rem 1.5rem;
    border-radius: 50px;
    cursor: pointer;
    font-weight: 600;
    transition: transform 0.2s, background-color 0.2s;
  }

  button:hover {
    background-color: #6a4aee;
    transform: translateY(-2px);
  }

  button:active {
    transform: translateY(0);
  }

  .avatar {
    width: 100px;
    height: 100px;
    background-color: #ffde59;
    border-radius: 50%;
    margin: 0 auto 2rem;
    position: relative;
    box-shadow: 0 5px 15px rgba(255, 222, 89, 0.4);
  }

  .face {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 60%;
    height: 60%;
  }

  .eyes {
    display: flex;
    justify-content: space-between;
    margin-top: 10px;
  }

  .eye {
    width: 12px;
    height: 12px;
    background-color: #333;
    border-radius: 50%;
  }

  .mouth {
    width: 30px;
    height: 10px;
    background-color: #333;
    border-radius: 0 0 20px 20px;
    margin: 10px auto 0;
  }
</style>
