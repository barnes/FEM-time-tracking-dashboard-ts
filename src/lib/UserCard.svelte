<script lang="ts">
  import { timeframe } from "../stores/timeframe";
  export let user;
  let currentTimeframe: string;
  timeframe.subscribe((value) => {
    currentTimeframe = value;
  });
</script>

<div class="card">
  <div class="top-section">
    <img src={user.avatar_URL} alt="{user.name} Avatar" />
    <div class="name">
      <h3>Report for</h3>
      <h1>{user.name}</h1>
    </div>
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
  @media (max-width: 1100px) {
    .card {
      border-radius: 1rem;
      background-color: var(--darkblue);
    }
    .top-section {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-radius: 1rem;
      background-color: var(--blue);
      padding: 2rem;
    }
    img {
      border: 4px solid white;
      border-radius: 100%;
      width: 20%;
      height: 20%;
    }
    .bottom-section {
      background-color: var(--darkblue);
      padding: 2rem 2rem 1rem 2rem;
      color: white;
      text-decoration: none;
      border-radius: 0 0 1rem 1rem;
    }
    h1 {
      font-weight: 300;
      font-size: 2rem;
    }
    h3 {
      font-size: 1rem;
      font-weight: 500;
      color: var(--paleblue);
    }
    .bottom-section {
      display: flex;
      justify-content: space-between;
    }
    a {
      margin-bottom: 1rem;
      color: var(--paleblue);
      font-size: 1.25rem;
      text-decoration: none;
    }
  }
  @media (min-width: 1100px) {
    .card {
      border-radius: 1rem;
      background-color: var(--darkblue);
    }
    .top-section {
      border-radius: 1rem;
      background-color: var(--blue);
      padding: 3rem;
    }
    .bottom-section {
      background-color: var(--darkblue);
      padding: 2rem 2rem 1rem 2rem;
      color: white;
      text-decoration: none;
      border-radius: 0 0 1rem 1rem;
    }
    img {
      border: 4px solid white;
      border-radius: 100%;
      width: 40%;
      margin-bottom: 3rem;
    }
    h1 {
      font-weight: 300;
      font-size: 3rem;
      margin-bottom: 2rem;
    }
    h3 {
      font-weight: 400;
      color: var(--paleblue);
    }
    a {
      display: block;
      margin-bottom: 1rem;
      color: var(--paleblue);
      font-size: 1.25rem;
      text-decoration: none;
    }
  }

  .active {
    color: white;
  }
</style>
