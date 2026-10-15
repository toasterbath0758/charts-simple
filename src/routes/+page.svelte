<script>
  import LineChart from '../lib/components/LineChart.svelte'
  import PieChart from '../lib/components/PieChart.svelte'
  import FakeNavbar from '../lib/components/FakeNavbar.svelte'

  let { data } = $props() // data uit +page.server.js

  // --- Chart 1 ---
  const months = ['January', 'February', 'March', 'April', 'May']
  const originalData1 = [50, 24, 33, 78, 54]
  let staticData1 = $state([...originalData1])
  const loadChart1 = () => {
    staticData1 = [...originalData1]
  }

  // --- Chart 2 ---
  const colors = ['purple', 'blue', 'green', 'orange', 'pink']
  const originalData2 = [50, 100, 33, 78, 54]
  let staticData2 = $state([...originalData2])
  const loadChart2 = () => {
    staticData2 = [...originalData2]
  }

  // --- Chart 3 ---
  const drinks = ['Fanta', 'Cola', 'Apple juice', 'Orange juice', 'Chocolate milk']
  const originalData3 = [25, 70, 50, 20, 70]
  let staticData3 = $state([...originalData3])
  const loadChart3 = () => {
    staticData3 = [...originalData3]
  }

  // --- Chart 4 ---
  const food = ['Sandwich', 'Pasta', 'Burger', 'Steak', 'Salad']
  const originalData4 = [70, 55, 24, 80, 10]
  let staticData4 = $state([...originalData4])
  const loadChart4 = () => {
    staticData4 = [...originalData4]
  }
</script>

<ul class="grid">
  <li class="graphs">
    <LineChart title="Line Chart" chartLabels={months} chartData={staticData1} dataLabel="Data 1" onReload={loadChart1} />
  </li>
  <li class="graphs">
    <PieChart title="Pie Chart" chartLabels={colors} chartData={staticData2} dataLabel="Data 2" onReload={loadChart2} />
  </li>
  <li class="graphs">
    <LineChart title="Line Chart" chartLabels={drinks} chartData={staticData3} dataLabel="Data 3" onReload={loadChart3} />
  </li>
  <li class="graphs">
    <PieChart title="Pie Chart" chartLabels={food} chartData={staticData4} dataLabel="Data 4" onReload={loadChart4} />
  </li>
</ul>

<style>
  :root {
    --background: hsl(247, 82%, 98%);
    --component-background: hsl(253, 46%, 92%);
    --component-outline: hsl(240, 20%, 83%);
    --text-color: hsl(256, 33%, 15%);
  }

  @font-face {
    font-family: 'Poppins-Regular';
    src: url('/src/lib/assets/Poppins/Poppins-Regular.ttf');
  }

  :global(*) {
    padding: 0;
    margin: 0;
    font-family: 'Poppins-Regular', sans-serif;
  }

  :global(body) {
    margin: 0;
    background: var(--background);
  }

  ul.grid {
    display: grid;
    margin: 1em;
    gap: 1em;
    list-style: none;
    justify-items: center;

    li {
      width: 300px;
    }

    @media (min-width: 650px) {
      width: min-content;
      grid-template-columns: 1fr 1fr;
      justify-self: center;
    }

    @media (min-width: 950px) {
      grid-template-columns: 1fr 1fr 1fr;
      justify-self: start;
    }
  }
</style>