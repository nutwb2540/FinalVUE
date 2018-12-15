<template>
    <div>
        <h1>Employees</h1>
 <b-table striped hover :items="products" :fields="fields" :per-page="pagesize" :current-page="pageindex"></b-table>
  <b-pagination size="lg" :total-rows="products.length" v-model="pageindex" :per-page="pagesize">  </b-pagination>
    </div>
</template>
<script>
import axios from "axios";
export default {
  name: "employees",
  components: {},
  data() {
    return {
      message: "FinalVUE",
      products: [],
      pagesize:5,
      pageindex:1,
      fields: [
        { key: "EmployeeID", sortable: true },
        { key: "LastName", sortable: true },
        { key: "FirstName", sortable: true },
        { key: "Title", sortable: true },
        { key: "TitleOfCourtesy", sortable: true },
        { key: "BirthDate", sortable: true },
        { key: "HireDate", sortable: true },
        { key: "Address", sortable: true },
        { key: "City", sortable: true },
        { key: "Region", sortable: true },
        { key: "PostalCode", sortable: true},
        { key: "Country", sortable: true},
        { key: "HomePhone", sortable:true},
        { key: "Extension", sortable:true},
        { key: "Photo", sortable:true},
        { key: "Notes", sortable:true}, 
        { key: "ReportsTo", sortable:true},
        { key: "PhotoPath", sortable:true}
      ]
    };
  },
  mounted() {
    var instace = this;
    axios
      .get("https://fsfinal050.herokuapp.com/api/employees/")
      .then(function(response) {
        console.log(response.data);
        instace.products = response.data.data;
      });
  }
};
</script>