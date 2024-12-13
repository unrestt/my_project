<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';

const rates = ref([])

const getDataFromNBP = async () => {
    const res = await fetch("https://api.nbp.pl/api/exchangerates/tables/A/?format=json");

    const jsonData = await res.json();
    console.log(jsonData);
    rates.value =  jsonData[0].rates;


  };



  getDataFromNBP();
// -------------------Testowe zmienne---------------------------
// let greeting = ref('');
// let counter = ref(0);
// let input = ref("");

// async function handleSubmit(e) {
//   e.preventDefault();
//   const target = e.target;
//   const name = target.querySelector('#name').value;
//   await my_project_backend.greet(name).then((response) => {
//     greeting.value = response;
//   });
// }

</script>

<template>
  <main>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    {{ rates }}
    
    <table>
      <tr>
        <th>Company</th>
        <th>Contact</th>
        <th>Country</th>
      </tr>
      <tr>
        <td>Alfreds Futterkiste</td>
        <td>Maria Anders</td>
        <td>Germany</td>
      </tr>

    </table>



    <!-- ----------------Testowe teksty------------------ -->

      <!-- {{ counter }}
      <button @click = "counter++">Podbij</button> -->

      <!-- <input v-model="input" type="text"/>
      {{ input }} -->


    <!-- <form action="#" @submit="handleSubmit">
      <label for="name">Enter your name: &nbsp;</label>
      <input id="name" alt="Name" type="text" />
      <button type="submit">Click Me!</button>
    </form>
    <section id="greeting">{{ greeting }}</section> -->

  </main>
</template>
