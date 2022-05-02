<template>
  <div>
    <h1>WanderJaunt Org Chart</h1>

    <section v-if="error">
      <p>
        There is a problem getting information
      </p>
    </section>

    <section v-else>
      <div v-if="loading">Loading...</div>

      <div>
           <ul>
               <EmployeeTree v-for="item in employees" :key="item.id" :node="item" data-test="employees"/>
           </ul>
      </div>
    </section>
  </div>
</template>


<script>
import axios from "axios";
import EmployeeTree from "@/components/EmployeeTree.vue"

export default {
  name: "EmployeeList",
  components: {
      EmployeeTree
  },
  data() {
    return {
      error: false,
      loading: true,
      employees: [],
    };
  },
  mounted() {
    axios
      .get(
        "https://gist.githubusercontent.com/chancock09/6d2a5a4436dcd488b8287f3e3e4fc73d/raw/fa47d64c6d5fc860fabd3033a1a4e3c59336324e/employees.json"
      )
      .then((response) => {
          this.items = response.data
        this.parseEmployees(response.data);
      })
      .catch((error) => {
        console.log(error);
        this.error = true;
      })
      .finally(() => (this.loading = false));
  },
  methods: {
    parseEmployees(employees_list) {
      let employee_parents = {};
      employees_list.forEach((employee) => {
        if (employee_parents[employee.manager_id] === undefined) {
          employee_parents[employee.manager_id] = [];
        }
        let add_first = true;
        for (const idx in employee_parents[employee.manager_id]) {
          const last_name =
            employee_parents[employee.manager_id][idx].name.split(" ")[1];
          const new_last_name = employee.name.split(" ")[1];
          if (new_last_name < last_name) {
            employee_parents[employee.manager_id].splice(idx, 0, employee);
            add_first = false;
            break;
          }
        }
        if (add_first) {
          employee_parents[employee.manager_id].push(employee);
        }
      });
      console.log(employee_parents);
      this.employees = this.employeesDataTree(employee_parents);
    },
    employeesDataTree(employee_parents, root = null) {
      let employees_branch = employee_parents[root];
      let employees = [];
      if (employees_branch == undefined) return [];
      employees_branch.forEach((employee) => {
        employees.push({
          id: employee.id,
          name: employee.name,
          title: employee.title,
          children: this.employeesDataTree(employee_parents, employee.id),
        });
      });
      return employees;
    },
  },
};
</script>

