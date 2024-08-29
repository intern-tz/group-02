<template>
  <form @submit.prevent="handleSubmit">
    <div class="form-container">
      <div class="list-item">
        <div class="row">
          <div class="item">
            <label>Họ và Tên</label>
            <input v-model="form.name"/>
          </div>
          <div class="item">
            <label>Tuoi</label>
            <input v-model="form.age"/>
          </div>
        </div>
        <div class="row">
          <div class="item">
            <label>Họ và Tên</label>
            <input v-model="form.name"/>
          </div>
          <div class="item">
            <label>Tuoi</label>
            <input v-model="form.age"/>
          </div>
        </div>
      <button type="submit">submit</button>
      </div>
      </div>
  </form>
</template>

<script setup>
import { reactive, ref } from "vue";
import { useRouter } from "vue-router";
import axios from 'axios';
import { toast } from 'vue3-toastify';

const router = useRouter();
const form = reactive({
  name: "",
  age: "",
});

const handleSubmit = async () => {
     const res= await axios.post("http://localhost:3000/student",form);
     if(res.status === 201) {
     router.push("/");
     toast.success("Create success !",{
       autoClose: 1000
      });
    } else{
        toast.error("Create success 11!");

  const res = await axios.post("http://localhost:3000/student", form);
  if (res.status === 201) {
    router.push("/").then(() => {
      toast.success("Create success !", {
        autoClose: 2000
      });
    });
  } else {
    toast.error("Create success 11!");
  }

}
}



</script>

<style scoped>

.content {
  background-color: #eee;
}
.form-container {
  width: 100%;
  height: 60vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.form-container .list-item {
  width: 100%;
  max-width: 900px;
  padding: 20px;
  background-color: #fff;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.form-container .list-item .row {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}

.form-container .list-item .item {
  width: 48%;
  display: flex;
  flex-direction: column;
}

.form-container .list-item .item label {
  font-size: 0.9rem;
  color: #333;
  margin-bottom: 5px;
  font-weight: bold;
}

.form-container .list-item .item input {
  width: 100%;
  padding: 8px;
  border-radius: 8px;
  font-size: 0.9rem;
  border: 1px solid #ddd;
  box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: border-color 0.3s, box-shadow 0.3s;
}

.form-container .list-item .item input:focus {
  border-color: #0071c5;
  box-shadow: 0 0 8px rgba(0, 113, 197, 0.5);
  outline: none;
}

.form-container .list-item button {
  width: 100%;
  padding: 12px;
  font-size: 1rem;
  background-color: #0071c5;
  border: 1px solid #0071c5;
  color: #fff;
  border-radius: 8px;
  cursor: pointer;
  margin-top: 20px;
}

.form-container .list-item button:hover {
  background-color: #005fa3;
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 113, 197, 0.2);
  opacity: 0.9;
}



</style>
=======
<style></style>
>>>>>>> d0f2035f174c9d8de8e9854da85766e128c42a26
