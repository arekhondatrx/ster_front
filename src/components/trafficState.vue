<template>
  <div id="ts">
    <table>
      <thead>
      <tr>
        <th>HOST URL</th>
        <th>ID</th>
        <th>STATE</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="row in signaler">
        <td>{{row.url}}</td>
        <td>{{row.id}}</td>
        <td id="state">
            <div>
              {{row.state}}
              <canvas width="20" height="20" v-bind:style="{
                                                            'background-color': row.state,
                                                             marginLeft: 3 + 'px',
                                                             marginTop: 5 + 'px'
                                                             }"></canvas>
            </div>
        </td>
      </tr>
      </tbody>
    </table>
    <p></p>
  </div>
</template>

<script>

export default {
  name: 'trafficState',
  props: {
      signaler: {
        type: Object,
        required: true
      }
  }
}
</script>

<style>
  #ts {
      background-color: inherit;
  }

  #state {
      width: 160px;
      text-align: center;
  }

  table {
      font-family: 'Open Sans', sans-serif;
      width: auto;
      margin: 10px auto;
      border-collapse: collapse;
      border: 3px solid #44475C;
      font-size: 25px;
      background-color: #e6f7ef;
  }

  table th {
    text-align: center;
    background: #44475C;
    color: #FFF;
    padding: 8px;
    min-width: 30px;
  }

  table td {
    text-align: center;
    padding: 8px;
    border-right: 2px solid #7D82A8;
  }

  table tr {
    border-bottom: 2px solid #7D82A8;
  }
  table td:last-child {
    border-right: none;
  }
  /*table tbody tr:nth-child(2n) td {*/
  /*  background: #D4D8F9;*/
  /*}*/
</style>
