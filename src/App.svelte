<script>
  import Window from "./components/Window.svelte";

  // Handle responsive iframes for embeds
  import pym from "pym.js";

  new pym.Child({
    polling: 500,
  });

  function getUrlParameter(name) {
    const params = new URLSearchParams(window.location.search);
    return params.get(name);
  }

  let includeCredit = getUrlParameter("credit") != "false";
</script>

<Window />
<!-- Outer div must have class 'chart-container' don't change -->
<div class="chart-container">
  <h1 class="headline">
    States along the Mississippi River <span class="g-span g-with">with</span>
    and <span class="g-span g-without">without</span> historical nitrate and phosphorus
    baselines
  </h1>
  <p class="dek">
    States along the Mississippi River track nitrate and phosphorus levels using
    direct measurements and modeling to assess water quality and the impact of
    agricultural runoff. Having a historical baseline enables these states to
    monitor changes over time, helping to gauge the effectiveness of pollution
    control measures and guide environmental policy decisions.
  </p>

  <p class="sr-only">
    Two maps of the United States highlighting states along the Mississippi
    River with and without historical nitrate and phosphorus baselines. States
    without nitrogen baselines are Tennessee, Mississippi, and Louisiana. States
    without phosphorus baselines are Tennessee and Mississippi.
  </p>

  <div class="flex">
    <div class="box">
      <h2>Nitrogen</h2>
      <img src="nitrogen.png" />
    </div>

    <div class="box">
      <h2>Phosphorus</h2>
      <img src="phosphorus.png" />
    </div>
  </div>

  {#if includeCredit}
    <div class="credit">
      Data: State agencies; Graphic by Jared Whalen /
      <a target="_blank" href="https://agwaterdesk.org/">Ag & Water Desk</a>
    </div>
  {/if}
</div>

<style lang="scss">
  .chart-container {
    max-width: 800px;
    width: 100%;
    padding: 0.5rem;

    .flex {
      display: flex;
      gap: 1rem;

      .box {
        h2 {
          font-weight: bold;
        }
      }
    }
  }

  .g-span {
    &.g-with {
      color: #6da34d;
    }
    &.g-without {
      color: #f1b82d;
    }
  }
</style>
