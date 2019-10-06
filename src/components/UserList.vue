<template>
    <b-container>
        <b-row class="card-list">
            <b-card
                :title="user.name"
                :img-src="user.url"
                img-alt="Image"
                img-top
                tag="article"
                v-for="user in users"
                :key="user.id"
                class="w-33 p-3 card mx-auto mt-5 card"
                :class="user.added ? 'active' : null">

                <b-button @click="addUser(user.id)" 
                variant="primary" 
                class="mx-auto">
                    {{user.added ? 'Remove user' : 'Add user'}}
                </b-button>
            </b-card>
        </b-row>
        <b-row>
            <b-button @click="showUsers" variant="success" class="mx-auto">Show User</b-button>
        </b-row>
    </b-container>
</template>


<script>
export default {
    data(){
        return {
            users: require('../../data.json'),
            userList : []
        }
    },
    methods: {
        addUser(id){
            const user = this.users.filter(el => el["id"] === id);
            user[0].added = !user[0].added;
            if(user[0].added){
                this.userList.push(user[0].id);
            } else if(!user[0].added){
                const delUser = this.userList.indexOf(id);
                this.userList.splice(delUser, 1);
            }
        },
        showUsers(){
            alert(this.userList);
        }
    }
}
</script>

<style scoped>
    img{
        height: 400px;
        width: 300px;
        border-radius: 5%;
    }
    .active{
        background: rgb(40, 161, 165);
    }
    .card-body{
        text-align: center;
    }
    .card{
        border-radius: 5%;
    }
    .btn{
        margin-top: 20px;
        margin-bottom: 20px;
    }
</style>