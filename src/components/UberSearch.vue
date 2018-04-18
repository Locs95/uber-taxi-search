<template>
  <div class="UberSearch">
    <div class="container uber-search-wrap" ng-app="uberapp"><!-- uber auto search -->
      <div class="row">
        <div class="col-sm-12">
          <table class="table table-responsive table-hover table-striped">
            <thead>
              <tr>
                <th scope="col" class="text-center">Марка и модель автомобиля</th>
                <th scope="col" colspan="3" class="text-center">
                  Минимальный год подключения
                </th>
              </tr>
              <tr>
                <th><input type="text" v-model="searchUber" placeholder="Введите марку или модель автомобиля" class="form-control"></th>
                <th class="text-center">UberX</th>
                <th class="text-center">UberSELECT</th>
                <th class="text-center">UberBLACK</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in filteredItems">
                  <td>{{ item.name }}</td>
                <td class="text-center">{{ item.uberx }}</td>
                <td class="text-center">{{ item.uberselect }}</td>
                <td class="text-center">{{ item.uberblack }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div><!-- uber auto search -->
  </div>
</template>

<script>
import uberauto from '../uberauto.json'

export default {
  name: 'UberSearch',
  data () {
    return {
      searchUber: '',
      data: uberauto
    }
  },
  computed: {
    filteredItems() {
       return this.data.filter(item => {
           return item.name.toLowerCase().match(this.searchUber.toLowerCase())
       })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.uber-search-wrap {
  min-height: 100vh;
  border: 1px solid #ddd;
}
.table tbody > tr:hover {
  background-color: #FFC000;
}
</style>
