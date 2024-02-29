<script>
  let count = 0;
  let sliderPointer;

  const handleClickA = () => {
    count += 10;
  }
  const handleClickB = () => {
    count -= 10;
  }

  $: {
    if (sliderPointer) { 
      sliderPointer.style.bottom = `${count}%`; 
    }
  }
</script>

<main>
  <div class="screen">
    <div class="dashboard">
      <p class="dollars-saved">${count}</p>
      <p class="dollars-saved-subtext">saved this month</p>
      <div class="slide-container">
        <input type="range" min="1" max="100" value={count} class="slider" id="myRange">
        <div class="slider-pointer" bind:this={sliderPointer}></div>
      </div>
    </div>
    <div class="image">
      <div class="popup-question">
        <h2>Question 1</h2>
        <p>What even is food?</p>
        <div class="buttons">
          <button on:click={handleClickA}>Something to eat</button>
          <button on:click={handleClickB}>Something to post pictures of on Instagram</button>
        </div>
      </div>
    </div>
  </div>
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    background-color: #FEFBDA;
    z-index: -2;
  }
  main {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index: 1;
  }
  button {
    flex-grow: 1;
    background-color: #C4D6D3;
    flex-basis: 0;
  }
  .buttons {
    display: flex;
    gap: 10px;
  }
  .dashboard {
    width: 355px;
    background-color: #485676;
  }
  .dollars-saved {
    color: #FF7C58;
    font-size: 50px;
    font-weight: 800;
    margin: 50px 0px 0px 0px;
  }
  .dollars-saved-subtext {
    color: #FEFBDA;
    font-size: 15px;
    margin: 0px 0px 50px 0px;
  }
  .image {
    height: 100%;
    width: 100%;
    background-image: url("./assets/kitchen.png");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .popup-question {
    position: absolute;
    background-color: #FFA68A;
    opacity: 0.95;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
  }
  .screen {
    display: flex;
    position: absolute;
    height: 100%;
    width: 100%;
    top: 0;
  }
  .slide-container {
    position: relative;
    display: flex;
    justify-content: center;
    height: 200px;
  }
  input[type="range"] {
    position: absolute;
    top: 75px;
    transform: rotate(270deg);
    height: 5px;
  }
  .slider {
    -webkit-appearance: none;
    width: 200px;
    height: 25px;
    background: #FF7C58;
    outline: none;
  }

  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
  }

  .slider::-moz-range-thumb {
    appearance: none;
  }

  .slider-pointer {
    position: absolute;
    width: 0px;
    height: 0px;
    border-left: 25px solid #FEFBDA;
    border-bottom: 20px solid transparent;
    border-right: 25px solid transparent;
    border-top: 20px solid transparent;
    margin-right: 10px;
  }

</style>