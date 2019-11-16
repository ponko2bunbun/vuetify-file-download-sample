<template>
    <v-app>
        <v-content>
            <Download/>
        </v-content>
    </v-app>
</template>

<script>
import Download from './components/Download'

export default {
    name: 'App',

    components: {
        Download
    },

    data: () => ({
    //
    }),
};
</script>
