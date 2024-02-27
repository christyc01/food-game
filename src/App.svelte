<script>
  const handleClickA = () => {
    alert('Correct! Food is something to eat.');
  }
  const handleClickB = () => {
    alert('Incorrect! Food is something to eat.');
  }
</script>

<main>
  <div class="screen">
    <div class="dashboard">
      <p class="dollars-saved">$21.00</p>
      <p class="dollars-saved-subtext">saved this month</p>
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
</style>