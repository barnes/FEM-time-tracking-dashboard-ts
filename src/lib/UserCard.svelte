<script>
  import { timeframe } from "../stores/timeframe";
  export let user;
  let currentTimeframe;
  timeframe.subscribe((value) => {
    currentTimeframe = value;
  });
</script>

<div class="card">
  <div class="top-section">
    <img src={user.avatar_URL} alt="{user.name} Avatar" />
    <h3>Report for</h3>
    <h1>{user.name}</h1>
  </div>
  <div class="bottom-section">
    <a
      href="#"
      on:click={() => {
        timeframe.set("daily");
      }}
      class:active={currentTimeframe === "daily"}>Daily</a
    >
    <a
      href="#"
      on:click={() => {
        timeframe.set("weekly");
      }}
      class:active={currentTimeframe === "weekly"}>Weekly</a
    >
    <a
      href="#"
      on:click={() => {
        timeframe.set("monthly");
      }}
      class:active={currentTimeframe === "monthly"}>Monthly</a
    >
  </div>
</div>

<style>
  .top-section {
    border-radius: 1rem;
    background-color: var(--blue);
    padding: 3rem;
  }
  .card {
    margin: 0 3rem 0 3rem;
    border-radius: 1rem;
    background-color: var(--darkblue);
    width: 33%;
  }
  .bottom-section {
    background-color: var(--darkblue);
    padding: 3rem;
    color: white;
    text-decoration: none;
    border-radius: 0 0 1rem 1rem;
  }
  .bottom-section:visited {
    color: white;
  }
  img {
    border: 4px solid white;
    border-radius: 100%;
    width: 40%;
    margin-bottom: 3rem;
  }
  h3 {
    font-weight: 200;
  }
  h1 {
    font-weight: 300;
    font-size: 3rem;
    margin-bottom: 3rem;
  }
  a {
    display: block;
    margin-bottom: 1rem;
    color: var(--paleblue);
    font-size: 1.25rem;
    text-decoration: none;
  }
  .active {
    color: white;
  }
</style>
