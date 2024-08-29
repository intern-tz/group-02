<template>
  <div class="title">
   <h1>Quản Lý Tài Khoản</h1>
    <div class="btn-add">
      <button>
        <router-link :to="{name: 'CreateStudent'}" >
          Thêm Mới +
        </router-link>
      </button>
    </div>
  </div>

  <table v-if="list" >
    <thead>
        <th>ID</th>
        <th>Tên</th>
        <th>Tuổi</th>
        <th>Cập Nhật</th>
    </thead>
    <tbody>
        <tr v-for="student in list" :key="student">
            <td>{{ student.id }}</td>
            <td>{{ student.name }}</td>
            <td>{{ student.age }}</td>
            <td class="action">

                <router-link :to="{name:'StudentUpdate', params: {id: student.id}}">
                    <fa icon="edit" class="btn-edit"/>
                </router-link>
                  <fa icon="trash" @click="openModal(student)" class="btn-delete"/>
            </td>
        </tr>
    </tbody>
  </table>

  <Modal
    @confirm="handleDelete(seletedObject)"
    @close="closeModal"
  >
  </Modal>

</template>

<script setup>
import { onMounted, ref } from 'vue';
import axios from 'axios';
import Modal from '../Modal/Modal.vue';


    let list = ref();
    let seletedObject = ref();
    let myModal;

    onMounted(() => {
        myModal = new bootstrap.Modal(document.getElementById("exampleModal"))
    })

    onMounted(()=> {
        axios.get("http://localhost:3000/student")
        .then(response => (list.value = response.data));
    });

    const  handleDelete= async (data) =>{
        axios.delete(`http://localhost:3000/student/${data.id}`)
        .then(response => (list.value = list.value.filter((item) => item.id !== data.id)));
        myModal.hide()
    }

    const openModal = (student) => {
        seletedObject.value = student;
        myModal.show();
    }

</script>

<style  scoped>

.table {

    width: 100%;
    border-collapse: collapse;
    table-layout: fixed;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    border-radius: 5px;
}

table {
    width: 100%;
    border-collapse: collapse;
}


table th, table td {
    padding: 12px 15px;
    border-bottom: 1px solid #ddd;
    text-align: center;
}

table th {
    background-color: #f4f4f4;
    font-weight: bold;
    color: #2c3e50;
}

table tr:nth-child(even) {
    background-color: #f9f9f9;
}

table tr:hover {
    background-color: #ececec;
}

.title {
  display: flex;
  justify-content: space-between;
  margin: 15px 0;
}

.title h1 {
  text-align: center;
  padding: 15px;
}

.btn-add {
  margin: 10px;
}

.btn-add button {
  outline: none;
  border: none;
  padding: 20px;
  font-weight: bold;
  background-color: #0071c5;
  border-radius: 10px;
}

.btn-add button a {
  color: #fff;
  text-decoration: none;
}

.btn-edit {
  color: #ffc71f;
  margin: 0 15px;
  font-size: 20px;
}

.btn-delete {
  color: #f55549;
  cursor: pointer;
  font-size: 20px;
}





</style>