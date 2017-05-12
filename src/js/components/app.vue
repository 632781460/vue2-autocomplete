
<template>
  <div>
    <autocomplete
      url="https://maps.googleapis.com/maps/api/geocode/json?address="
      :custom-params="{ token: 'dev' }"
      anchor="formatted_address"
      label="formatted_address"
      loading-text="加载中..."
      no-data-text="暂无数据"
      :process="processJSON"
      :on-select="getData" >
        <template slot="suggestRow" scope="scope">
          <span @click.prevent="scope.selectList(scope.data)"
            @mousemove="scope.mousemove(scope.index)"
          >{{ scope.data.formatted_address}}</span>
        </template>
    </autocomplete>
  </div>
</template>

<script>

  import Autocomplete from './vue-autocomplete.vue';
  require("../../../dist/style/vue2-autocomplete.css")

  export default {
    components: { Autocomplete },

    methods: {
      processJSON(json) {
        return json.results;
      },
      getData(data) {
        console.log(data);
      }
    }
  };

</script>
