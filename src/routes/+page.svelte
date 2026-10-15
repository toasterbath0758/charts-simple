<script lang="ts">
    import LineChart from '../lib/components/LineChart.svelte'
    import PieChart from '../lib/components/PieChart.svelte'
    import FakeNavbar from '../lib/components/FakeNavbar.svelte'
    // import { invalidateAll } from '$app/navigation'
    // import { onMount } from "svelte"

    let { data } = $props() // data from server.ts

    const months = ['January', 'February', 'March', 'April', 'May']
    // Vaste dataset
    const originalData1: number[] = [50, 24, 33, 78, 54, 90]

    let staticData1: number[] = $state([...originalData1])

    // Ververst alleen de grafiek, geen page reload
    const loadChart1 = () => {
      staticData1 = [...originalData1]
    }

    // --------------------------------------------

    const colors = ['purple', 'blue', 'green', 'orange', 'pink']

     // Vaste dataset
    const originalData2: number[] = [50, 100, 33, 78, 54]

    let staticData2: number[] = $state([...originalData2])


        const loadChart2 = () => {
      staticData2 = [...originalData2]
    }
    
    // --------------------------------------------

        const drinks = ['Fanta', 'Cola', 'Apple juice', 'Orange juice', 'Chocolate milk']
    // Vaste dataset
    const originalData3: number[] = [25, 70, 50, 20, 70, 90]

    let staticData3: number[] = $state([...originalData3])

    // Ververst alleen de grafiek, geen page reload
    const loadChart3 = () => {
      staticData3 = [...originalData3]
    }

    // --------------------------------------------

    const food = ['Sandwich', 'Pasta', 'Burger', 'Steak', 'Salad']

     // Vaste dataset
    const originalData4: number[] = [70, 55, 24, 80, 10]

    let staticData4: number[] = $state([...originalData4])


        const loadChart4 = () => {
      staticData4 = [...originalData4]
    }
    
    // --------------------------------------------


</script>

<!-- <FakeNavbar></FakeNavbar> -->
<ul class="grid">
    <li class="graphs">
        <!-- chartlabels months is gelinkt aan de const months -->
        <LineChart title="Line Chart" chartLabels={months} chartData={staticData1} dataLabel="Data 1" onReload={loadChart1}/>
    </li>
    <li class="graphs">
        <!-- chartlabels colors is gelinkt aan de const colors -->
        <PieChart title="Pie Chart" chartLabels={colors} chartData={staticData2} dataLabel="Data 2" onReload={loadChart2}/>
    </li>
        <li class="graphs">
        <!-- chartlabels drinks is gelinkt aan de const drinks -->
        <LineChart title="Line Chart" chartLabels={drinks} chartData={staticData3} dataLabel="Data 3" onReload={loadChart3}/>
    </li>
    <li class="graphs">
        <!-- chartlabels food is gelinkt aan de const food -->
        <PieChart title="Pie Chart" chartLabels={food} chartData={staticData4} dataLabel="Data 4" onReload={loadChart4}/>
    </li>
</ul>


<style>

:root {
    --background:hsl(247, 82%, 98%);
    --component-background: hsl(253, 46%, 92%);
    --component-outline: hsl(240, 20%, 83%); 
    --text-color: hsl(256, 33%, 15%);

    
    --chart-1: hsl(257, 89%, 74% | 100%);
}

@font-face {
  font-family: "Poppins-Regular";
  src: url("/src/lib/assets/Poppins/Poppins-Regular.ttf");
}

* {
    padding: 0;
    margin: 0;
    font-family:'Poppins-Regular'
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
        display: grid;
        width: min-content;
        grid-template-columns: 1fr 1fr;
        justify-items: center;
        justify-self: center;
    }

    @media (min-width: 950px) {
        grid-template-columns: 1fr 1fr 1fr;
        justify-self: start;
    }

}


</style>