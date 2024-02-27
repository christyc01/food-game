<main>
  <h1>Food Game</h1>
  <div class="image"></div>
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
  .image {
    position: absolute;
    height: 100%;
    width: 100%;
    top: 0;
    background-image: url("./assets/kitchen.png");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
  }
</style>