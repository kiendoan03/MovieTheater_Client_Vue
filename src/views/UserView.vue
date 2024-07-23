<script setup>
import axios from 'axios';
import { RouterLink } from 'vue-router';
import router from '@/router';
import { library } from '@fortawesome/fontawesome-svg-core'
    import { fas } from '@fortawesome/free-solid-svg-icons'
    import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

    library.add(fas)

</script>
<template>
    <section style="margin-top: 5%;">
            <div class="row mt-5">
                <div class="col-3">
                    <div class="card border-0 rounded-3 p-2" style="background-color:rgb(63, 63, 63);">
                        <div class="text-center my-3 rounded-3">
                            <div class=" position-relative mx-auto" style="width: 9vmax; ">
                                <img :src="baseUrl + user.image" style="border-radius: 50%;object-fit: cover; overflow: hidden; height: 8vmax; width: 8vmax;" alt=" ">
                            </div>
                        </div>
                        <div class="card-body ">
                            <p class="text-light fw-bold mb-1 d-inline " style="font-size: 1.5vmax; ">{{ user.name }}</p>
                            <div class="mt-5 ">
                                <div>
                                    <span class="text-light " style="font-size: 0.8vmax; ">Purchased tickets</span>
                                    <span class="text-light " style="float: right; font-size: 0.8vmax; ">{{ticketBought}}</span>
                                </div>
                            </div>
                            <div class="action my-5 text-center ">
                                <a  @click="logout" class="border-0 p-3 text-center text-light text-decoration-none" style="background-color: rgb(94, 94, 94) ;border-radius: 50vmax; font-size: 0.8vmax; width: 6vmax; ">Sign Out</a>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="col-9 ">
                    <section>
                        <div class="row ">
                            <div class="col-5 ">
                                <div class="text-light d-inline " style="font-size: 1.5vmax; ">Account</div>
                                <div class="d-inline " style="float: right" @click="toggleEditMode()">
                                    <font-awesome-icon :icon="['fas', 'pen-to-square']" style="color: #ffffff; font-size: 1.2vmax; cursor: pointer;" />
                                </div>
                                <p class="text-light mt-3 ">Here you can edit public information about yourself. The changes will be display within 5 minutes.</p>
                            </div>
                            <div class="col-7 ">
                                <div class="row mx-3 " style="background-color:rgb(63, 63, 63); border-radius: 1vmax; ">
                                    <div class="mx-2 my-2 p-3">
                                            <div class="mb-3 row ">
                                                <label class="col-sm-2 col-form-label text-light ">Display name</label>
                                                <div class="col-sm-10 ">
                                                    <input type="text" :readonly="!isEditMode" name="cus_name" class="form-control-plaintext text-light " v-model="user.name">
                                                </div>
                                            </div>
                                            <div class="mb-3 row ">
                                                <label class="col-sm-2 col-form-label text-light ">Username</label>
                                                <div class="col-sm-10 ">
                                                    <input type="text " :readonly="!isEditMode" name="cus_username" class="form-control-plaintext text-light " v-model="user.username">
                                                </div>
                                            </div>
                                            <div class="mb-3 row ">
                                                <label for="staticEmail " class="col-sm-2 col-form-label text-light ">Email</label>
                                                <div class="col-sm-10 ">
                                                    <input type="text " :readonly="!isEditMode" name="cus_email" class="form-control-plaintext text-light " id="staticEmail " v-model="user.email">
                                                </div>
                                            </div>
                                            <div class="mb-3 row ">
                                                <label class="col-sm-2 col-form-label text-light ">Date of birth</label>
                                                <div class="col-sm-10 ">
                                                    <input type="date" :readonly="!isEditMode" name="cus_dateOfBirth" class="form-control-plaintext text-light " v-model="formattedDob" >
                                                </div>
                                            </div>
                                            <div class="mb-3 row ">
                                                <label class="col-sm-2 col-form-label text-light ">Address</label>
                                                <div class="col-sm-10 ">
                                                    <input type="text " :readonly="!isEditMode" name="cus_address" class="form-control-plaintext text-light " v-model="user.address">
                                                </div>
                                            </div>
                                            <div class="mb-3 row ">
                                                <label class="col-sm-2 col-form-label text-light ">Phone</label>
                                                <div class="col-sm-10 ">
                                                    <input type="text " :readonly="!isEditMode" name="cus_phone" class="form-control-plaintext text-light " v-model="user.phoneNumber">
                                                </div>
                                            </div>
                                            <div v-show="isEditMode">
                                               <div class="mb-3 row " id="input-pass" >
                                                <label class="col-sm-2 col-form-label text-light ">Password</label>
                                                <div class="col-sm-10 ">
                                                    <input type="password " name="cus_password" class="form-control-plaintext border-0 border-bottom text-light" v-model="new_password">
                                                </div>
                                                </div>
                                                <div class="mb-3 row " id="input-repass" >
                                                    <label class="col-sm-2 col-form-label text-light ">Re-Password</label>
                                                    <div class="col-sm-10 ">
                                                        <input type="password " name="cus_repass" class="form-control-plaintext border-0 border-bottom  text-light " v-model="re_password">
                                                    </div>
                                                </div> 
                                            </div>
                                            
                                            <div v-show="isEditMode">
                                                <button type="submit" class="btn btn-danger mb-3" @click="saveChanges()" style="font-size: 0.8vmax; width: 6vmax; border-radius: 50vmax">OK</button>
                                            </div>
                                    </div>

                                </div>

                            </div>
                        </div>
                    </section>

                    <section class="mt-5 mb-5">
                        <div class="row">
                            <div class="col-5">
                                <div class="text-light d-inline" style="font-size: 1.5vmax;">Purchased tickets</div>
                                <div class="d-inline">
                                    <i class="fa-regular fa-pen-to-square" style="color: #ffffff; font-size: 1.2vmax; float: right;"></i>
                                </div>
                            </div>
                            <div class="col-7">
                                <div class="row mx-3" style="background-color:rgb(63, 63, 63); border-radius: 1vmax;">
                                    <div class=" my-2" >
                                        <table class="table table-dark table-hover my-3 text-light" >
                                            <thead>
                                                <tr>
                                                    <th scope="col">No.</th>
                                                    <th scope="col">Movie</th>
                                                    <th scope="col">Room</th>
                                                    <th scope="col">Date</th>
                                                    <th scope="col">Start time</th>
                                                    <th scope="col">End time</th>
                                                    <th scope="col">Seat</th>
                                                    <th scope="col">Price</th>
                                                </tr>
                                            </thead>
                                            <tbody>
                                                <tr v-for="(ticket, index) in paginatedTickets">
                                                    <th scope="row" class="col-1">{{ index + 1 + (currentPage - 1) * pageSize }}</th>
                                                    <td class="col-2">{{ticket.schedules.movie.movieName}}</td>
                                                    <td class="col-2">{{ getRoomNameById(ticket.schedules.roomId)}}</td>
                                                    <td class="col-2">{{ticket.schedules.scheduleDate}}</td>
                                                    <td class="col-2">{{ticket.schedules.startTime}}</td>
                                                    <td class="col-2">{{ticket.schedules.endTime}}</td>
                                                    <td class="col-1">{{ convertSeat(ticket.seats.row, ticket.seats.column) }}</td>
                                                    <td class="col-2">{{ ticket.finalPrice.toLocaleString('vi-VN', { style: 'currency', currency: 'VND' })  }}</td>
                                                </tr>
                                            </tbody>
                                        </table>
                                        <div class="pagination">
                                            <button @click="changePage(currentPage - 1)" :disabled="currentPage === 1">Previous</button>
                                            <span>Page {{ currentPage }} of {{ totalPages }}</span>
                                            <button @click="changePage(currentPage + 1)" :disabled="currentPage === totalPages">Next</button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>

                </div>
            </div>
        </section>
  </template>
  
  <script>

  export default {
    data() {
      return {
        imageUrl: '',
        isEditMode: false,
        user: {},
        userId: localStorage.getItem('id_cus'),
        baseUrl: 'https://localhost:7071',
        re_password:'',
        new_password: '',
        ticketBought: 0,
        tickets: [],
        currentPage: 1,
        pageSize: 5,
        totalPages: 1,
        rooms:[]
      };
    },
    created() {
      this.getUserById(this.userId);
      this.countTicketBought(this.userId);
      this.getTicketsByCustomer(this.userId);
      this.getRooms();
    },
    computed: {
        formattedDob: {
            get() {
                if (!this.user.dob) return '';
                const [month, day, year] = this.user.dob.split('/');
                return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`;
            },
            set(newValue) {
                if (!newValue) {
                this.user.dob = '';
                return;
                }
                const [year, month, day] = newValue.split('-');
                this.user.dob = `${month}/${day}/${year}`;
            }
        },
        paginatedTickets() {
            const start = (this.currentPage - 1) * this.pageSize;
            const end = start + this.pageSize;
            return this.tickets.slice(start, end);
        }
    },
   
    methods: {
        getUserById(id){
            axios.get(`https://localhost:7071/api/Customers/${id}`,{
                headers: {
                    Authorization: `Bearer ${localStorage.getItem('token_cus')}`
                }
            }).then(response => {
                this.user = response.data;
                console.log(this.user);
                this.imageUrl = this.baseUrl + this.user.image;
            }).catch(error => {
                console.log(error);
            })
        },
        getRooms() {
            axios.get(`https://localhost:7071/api/Rooms`, {
                headers: {
                Authorization: `Bearer ${localStorage.getItem('token_cus')}`
                }
            }).then(response => {
                this.rooms = response.data;
            }).catch(error => {
                console.error('Error fetching rooms:', error);
            });
        },
        getRoomNameById(roomId) {
            const room = this.rooms.find(r => r.id === roomId);
            return room ? room.roomName : 'Unknown Room';
        },
        countTicketBought(id) {
            axios.get(`https://localhost:7071/api/Customers/count-tickets-bought?cusId=${id}`, {
                headers: {
                    Authorization: `Bearer ${localStorage.getItem('token_cus')}`
                }
            }).then(response => {
                this.ticketBought = response.data;
            }).catch(error => {
                console.error('Error fetching tickets:', error);
            });
        },
        getTicketsByCustomer(id){
            axios.get(`https://localhost:7071/api/Tickets/get-tickets-by-customer?cusId=${id}`, {
                headers: {
                    Authorization: `Bearer ${localStorage.getItem('token_cus')}`
                }
            }).then(response => {
                this.tickets = response.data;
                this.totalPages = Math.ceil(this.tickets.length / this.pageSize);
                console.log('ticket',this.tickets);
            }).catch(error => {
                console.error('Error fetching tickets:', error);
            });
        },
      toggleEditMode() {
        this.isEditMode = !this.isEditMode; 
      },
      saveChanges() {
        if (this.new_password !== this.re_password) {
            alert('Passwords do not match');
            return;
        }
        const formData = new FormData();
        formData.append('name', this.user.name);
        formData.append('username', this.user.username);
        formData.append('email', this.user.email);
        formData.append('dob', this.user.dob);
        formData.append('address', this.user.address);
        formData.append('phoneNumber', this.user.phoneNumber);
        formData.append('passwordHash', this.new_password);
        formData.append('id', this.user.id);
        axios.put(`https://localhost:7071/api/Customers/${this.userId}`, formData, {
            headers: {
                Authorization: `Bearer ${localStorage.getItem('token_cus')}`
            }
        }).then(response => {
            alert('Update successfully');
            this.isEditMode = false;
        }).catch(error => {
            console.log(error);
        })
        
        this.isEditMode = false;
      },
      logout() {
            localStorage.removeItem('token_cus');
            localStorage.removeItem('role_cus');
            localStorage.removeItem('id_cus');
            localStorage.removeItem('email_cus');
            localStorage.removeItem('name_cus');
            // this.$router.push('/');
            window.location.href = '/';
        },
    changePage(page) {
      if (page > 0 && page <= this.totalPages) {
        this.currentPage = page;
      }
    },
    convertSeat(row, column) {
      const rowChar = String.fromCharCode(64 + row); // Convert row number to letter (A, B, C, ...)
      return `${rowChar}${column}`;
    }
    },
  };
  </script>
  
<style scoped>
.pagination {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

.pagination button {
  background-color: #343a40;
  color: white;
  border: 1px solid #6c757d;
  padding: 5px 10px;
  margin: 0 5px;
  cursor: pointer;
  border-radius: 5px;
}

.pagination button:disabled {
  background-color: #6c757d;
  cursor: not-allowed;
}

.pagination span {
  margin: 0 10px;
  color: white;
}
</style>

  