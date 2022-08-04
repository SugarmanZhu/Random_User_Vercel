<script>
export default {
    name: 'Generator',
    data() {
        return {
            title: 'Mr',
            name: 'Random User',
            gender: 'male',
            email: 'random@user.com',
            picture: 'https://randomuser.me/api/portraits/men/1.jpg',
            address: 'Gusev, Mars',
            phone: '(012)-345-6789'
        }
  },
  methods: {
    async getUser() {
        const res = await fetch('https://randomuser.me/api')
        const { results } = await res.json()
        const result = results[0]
        
        this.title = result.name.title
        this.name = [result.name.first, result.name.last].join(' ');
        this.gender = result.gender
        this.email = result.email
        this.picture = result.picture.large
        this.address = [result.location.city, result.location.country].join(', ');
        this.phone = result.phone
    },
  },
}
</script>

<template>
    <img :src="picture" :alt="`${name}`" :class="gender"/>
    <h1>{{title}}. {{name}}</h1>
    <h3>Phone: {{phone}}</h3>
    <h3>Email: {{email}}</h3>
    <h3>Address: {{address}}</h3>
    <button :class="gender" @click="getUser()">Get Random User</button>
</template>