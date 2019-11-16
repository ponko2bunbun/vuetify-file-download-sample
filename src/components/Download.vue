<template>
    <v-container>
        <v-row>
            <v-col cols="2">
                <v-btn
                    v-on:click="click"
                    color="primary"
                    block
                >
                    Download csv
                </v-btn>
            </v-col>

            <v-col cols="2">
                <v-btn
                    v-on:click="click"
                    color="primary"
                    block
                >
                    Download image
                </v-btn>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    methods: {
        click () {
        }
    }
}
</script>
