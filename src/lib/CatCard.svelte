<script>
  import { timeframe } from "../stores/timeframe";
  export let data;
  let currentTimeframe;
  timeframe.subscribe((value) => {
    currentTimeframe = value;
  });

  let icon = data.title.toLowerCase().split(" ").join("-");
  let style;
</script>

<div class="card" style="background-color:var(--{icon})">
  <div class="header-image">
    <img src={`/src/assets/icon-${icon}.svg`} alt="" class="icon" />
  </div>
  <div class="content">
    <div class="top">
      <h1>{data.title}</h1>
      <a href="#">...</a>
    </div>
    <!-- 
    How do I inject the currentTimeframe variable value into this query?
    <h1 class="time">{data.timeframes.currentTimeframe.current}</h1>
  -->

    {#if currentTimeframe === "daily"}
      <h1 class="time">{data.timeframes.daily.current}hrs</h1>
      <h2 class="prevTime">
        Last day - {data.timeframes.daily.previous}hrs
      </h2>
    {:else if currentTimeframe == "monthly"}
      <h1 class="time">{data.timeframes.monthly.current}</h1>
      <h2 class="prevTime">
        Last month - {data.timeframes.monthly.previous}hrs
      </h2>
    {:else if currentTimeframe === "weekly"}
      <h1 class="time">{data.timeframes.weekly.current}</h1>
      <h2 class="prevTime">
        Last week - {data.timeframes.weekly.previous}hrs
      </h2>
    {/if}
  </div>
</div>

<style>
  img {
    margin-left: 50%;
  }
  .header-image {
  }
  .card {
    border-radius: 1rem;
  }
  .content {
    padding: 1rem;
    background-color: var(--darkblue);
    border-radius: 1rem;
  }
</style>
