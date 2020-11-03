<template>
    <v-app>
        <v-content class="fill-height">
                <v-card width="800" class="mx-auto mt-12">
                    <v-card-title class="justify-center green">SENTINEL. Health Management Panel</v-card-title>
                    <v-form @submit.prevent="submit" @submit="submitRegister" class="pa-10">
                        <v-text-field
                            v-model="form.username"
                            :counter="15"
                            label="Username"
                            required
                        ></v-text-field>
                        <v-text-field
                            v-model="form.email"
                            label="Email"
                            required
                        ></v-text-field>
                        <v-text-field
                            v-model="form.password"
                            label="Password"
                            type="password"
                            required
                        ></v-text-field>
                        <v-card-actions>
                            <v-btn color='info' type="submit">Register</v-btn>
<!--                            <v-btn color='success' type="submit">Login</v-btn>-->
                        </v-card-actions>
                    </v-form>
                </v-card>
        </v-content>
    </v-app>
</template>

<script>

export default {
    metaInfo: {title: 'Login'},
    props: {
        errors: Object,
    },
    data() {
        return {
            sending: false,
            form: {
                username: null,
                email: null,
                password: null,
            },
        };
    },
    methods: {
        submitRegister() {
            console.log('registering');
            this.sending = true;
            this.$inertia.post('/register', this.form)
                .then(() => this.sending = false);
        },
    },
};
</script>
