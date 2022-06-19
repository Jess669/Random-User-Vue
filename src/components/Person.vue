<template>
    <section class="person" :class="(persons.gender == 'male' ? 'male' : 'female')">
        <ul>
            <li>
                <img :src="persons.image" alt="profile image" :class="(persons.gender == 'male' ? 'male' : 'female')">
                <p>Name:</p>
                <h2>{{ persons.first }} {{ persons.last }}</h2>
                <p>Email:</p>
                <h3>{{persons.email}}</h3>
            </li>
        </ul>
        <button type="button" @click="$emit('fetchUser')">Get Random User!</button>
    </section>
</template>

<script>
export default {
    name : 'Person',
    props : {
        persons : Object,
        gender: String
    }
}
</script>

<style scoped>

.person {
    max-width: 350px;
    border-radius: 5px;
    margin: auto;
    display: flex;
    flex-flow: column wrap;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.person img {
    border-radius: 50%;
    display: block;
    margin:auto;
}

.person ul {
    list-style: none;
}

.person h3 {
    word-break: break-all;
}

.person button {
    padding: 10px;
    background-color: rgb(91, 155, 72);
    cursor: pointer;
    border: 0;
    border-radius: 5px;
    margin-top: 30px;
}

.person button:hover {
    background-color: rgb(107, 179, 85);
}

.male {
    border: 5px solid rgb(49, 49, 49) !important;
}

.female {
    border: 5px solid rgb(235, 168, 23) !important;
}

</style>
