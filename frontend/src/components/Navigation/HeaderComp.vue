<template>
    <div>
        <v-app-bar elevation="0" height="60" color="">
            <div class="d-flex align-center">
                <div class="">
                    <h1 class="LogoFont Logopointer" @click="$router.push('/MianComp')"
                    >
                        Travela
                    </h1>
                </div>
            </div>
            <v-spacer></v-spacer>
            <v-btn  depressed raised class="yellow darken-3 mx-4" @click="$router.push('/LogIn')">
                LOG IN
            </v-btn>
            <v-btn depressed color="" class="yellow darken-3 black--text">
                <v-icon>mdi-magnify</v-icon>
            </v-btn>
        </v-app-bar>
    </div>

</template>