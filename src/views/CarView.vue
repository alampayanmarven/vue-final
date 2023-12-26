<template>
    <div class="everything">
      <div class="perin">
        <h1 class="cust">
          Motor Cycle
        </h1>
      </div>
      <div class="table-customers">
        <table class="table table-bordered table-striped">
          <thead>
            <tr>
              <th>ID</th>
              <th>Brand</th>
              <th>Horse Power</th>
              <th>Delete</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="car in cars" :key="car.id">
              <td>{{ car.id }}</td>
              <td>{{ car.brand }}</td>
              <td>{{ car.horse_power }}</td>
              <td>
                <button @click="deleteCar(car.id)" class="btn btn-danger">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </template>
  
  <style>
  .everything {
    margin: 3.5rem 4rem;
  }
  
  .perin h1 {
    font-size: 45px;
    margin-left: 2px;
    font-weight: 1000;
    letter-spacing: -2px;
    font-family: 'Cavilant';
  }
  
  .perin {
    border-bottom: 1px solid #ff4081; /* Pink border */
    padding-bottom: 10px;
    display: flex;
  }
  
  .table-customers {
    margin-top: 20px;
  }
  
  table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 10px;
    border-radius: 10px;
  }
  
  th, td {
    border: 1px solid #ff4081; /* Pink border */
    padding: 8px;
    text-align: left;
  }
  
  th {
    background-color: #ff4081; /* Pink background for header */
    color: white; /* White text for header */
  }
  
  .cust {
    color: white; /* White color for h1 */
  }
  
  .plus {
    padding: 5px;
    color: #ff4081;
    background-color: white;
    border-radius: 5px;
    font-size: 15px;
    text-decoration: none;
  }
  
  .btn {
    background-color: #dc3545; /* Bootstrap red color */
    color: #ffffff;
    border-radius: 5px;
    padding: 5px 10px;
  }
  </style>
  
  <script setup>
  import { onMounted, ref } from 'vue';
  
  const cars = ref(null);
  
  onMounted(() => {
    fetch('http://localhost:8000/api/cars')
      .then(response => response.json().then(data => (cars.value = data)));
  });
  
  const deleteCar = async (carId) => {
    try {
      const response = await fetch(`http://localhost:8000/api/cars/${carId}`, {
        method: 'DELETE',
      });
  
      if (response.ok) {
        cars.value = cars.value.filter((car) => car.id !== carId);
        alert('car deleted successfully!');
      } else {
        console.error('Failed to delete car:', response.statusText);
      }
    } catch (error) {
      console.error('Error deleting car:', error);
    }
  };
  </script>
  
  