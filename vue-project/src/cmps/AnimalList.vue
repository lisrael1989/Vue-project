<template>
  <table>
    <thead>
      <tr>
        <th>Type</th>
        <th>Count</th>
        <th>Search</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="animal in animalInfos" :key="animal.type">
        <td>{{ animal.type }}</td>
        <td>{{ animal.count }}</td>
        <td>
          <a :href="`https://www.google.com/search?q=${animal.type}`" target="_blank">Link</a>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  data() {
    return {
      animalInfos: [
        { type: "Malayan Tiger", count: 787 },
        { type: "Mountain Gorilla", count: 212 },
        { type: "Fin Whale", count: 28 },
      ],
    }
  },
}
</script>

<style lang="scss">
table {
  width: 300px;
  margin: auto;
  border-collapse: collapse;
  background-color: white;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  font-family: Arial, Helvetica, sans-serif;

  th,
  td {
    padding: 10px;
    text-align: left;
    border-bottom: 1px solid #ddd;
  }
  th {
    background-color: #4caf50;
    color: white;
  }
  tr:hover {
    background-color: #f1f1f1;
  }
  a {
    color: #4caf50;
    text-decoration: none;
  }
  a:hover {
    text-decoration: underline;
  }
}

h1 {
  text-align: center;
}
</style>
