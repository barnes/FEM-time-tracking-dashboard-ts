<script lang="ts">
  import { timeframe } from "../stores/timeframe";
  import ellipsis from "../assets/icon-ellipsis.svg";
  import exercise from "../assets/icon-exercise.svg";
  import play from "../assets/icon-play.svg";
  import selfcare from "../assets/icon-self-care.svg";
  import social from "../assets/icon-social.svg";
  import study from "../assets/icon-study.svg";
  import work from "../assets/icon-work.svg";
  import { fade } from "svelte/transition";
  export let data;
  let currentTimeframe: string;
  timeframe.subscribe((value) => {
    currentTimeframe = value;
  });

  let icon = data.title.toLowerCase().split(" ").join("-");
  let style;
</script>

<div class="card">
  <div class="header-image" style="background-color:var(--{icon})">
    <img src={`/src/assets/icon-${icon}.svg`} alt="" class="icon" />
  </div>
  <div class="content">
    <div class="top">
      <h1 class="title">{data.title}</h1>
      <img src={ellipsis} alt="ellipsis icon" class="icon-ellipsis" />
    </div>
    <!-- 
    How do I inject the currentTimeframe variable value into this query?
    <h1 class="time">{data.timeframes.currentTimeframe.current}</h1>
  -->
    <div class="time-report">
      {#if currentTimeframe === "daily"}
        <h1 class="time" in:fade={{ delay: 0, duration: 300 }}>
          {data.timeframes.daily.current}hrs
        </h1>
        <h2 class="prevTime" in:fade={{ delay: 0, duration: 300 }}>
          Last Day - {data.timeframes.daily.previous}hrs
        </h2>
      {:else if currentTimeframe == "monthly"}
        <h1 class="time" in:fade={{ delay: 0, duration: 300 }}>
          {data.timeframes.monthly.current}hrs
        </h1>
        <h2 class="prevTime" in:fade={{ delay: 0, duration: 300 }}>
          Last Month - {data.timeframes.monthly.previous}hrs
        </h2>
      {:else if currentTimeframe === "weekly"}
        <h1 class="time" in:fade={{ delay: 0, duration: 300 }}>
          {data.timeframes.weekly.current}hrs
        </h1>
        <h2 class="prevTime" in:fade={{ delay: 0, duration: 300 }}>
          Last Week - {data.timeframes.weekly.previous}hrs
        </h2>
      {/if}
    </div>
  </div>
</div>

<style>
  @media (min-width: 1100px) {
    .card {
      position: relative;
      border-radius: 1rem;
      background-color: var(--darkblue);
    }
    .content {
      position: absolute;
      background-color: var(--darkblue);
      top: 15%;
      padding: 2rem;
      border-radius: 1rem;
      width: 100%;
    }
    .icon {
      margin-left: 50%;
    }
    .time {
      font-size: 52px;
      font-weight: 300;
      margin: 1rem 0 1rem 0;
    }
    .prevTime {
      font-size: 16px;
      font-weight: 400;
      margin-bottom: 1rem;
      color: var(--paleblue);
    }
    .title {
      margin-bottom: 1rem;
      font-size: 20px;
      font-weight: 500;
    }
  }
  @media (max-width: 1100px) {
    .card {
      position: relative;
      border-radius: 1rem;
      background-color: var(--darkblue);
      height: 160px;
      margin-bottom: 6rem;
    }
    .content {
      position: absolute;
      background-color: var(--darkblue);
      top: 40%;
      padding: 2rem;
      border-radius: 1rem;
      width: 100%;
    }
    .icon {
      margin-left: 70%;
    }
    .time-report {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .time {
      font-size: 48px;
      font-weight: 300;
      margin: 0;
    }
    .prevTime {
      font-size: 16px;
      font-weight: 400;
      color: var(--paleblue);
    }
    .title {
      margin-bottom: 0.75rem;
      font-size: 20px;
      font-weight: 500;
    }
  }

  .header-image {
    border-radius: 1rem 1rem 0 0;
  }
  .top {
    display: flex;
    justify-content: space-between;
  }
  .icon-ellipsis {
    height: 50%;
  }
</style>
