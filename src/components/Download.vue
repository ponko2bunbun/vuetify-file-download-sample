<template>
    <v-container>
        <v-row>
            <v-col cols="2">
                <v-btn
                    v-on:click="click('sample.csv')"
                    color="primary"
                    block
                >
                    Download csv
                </v-btn>
            </v-col>

            <v-col cols="2">
                <v-btn
                    v-on:click="click('sample.png')"
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
import axios from 'axios'
import urljoin from 'url-join'
import { saveAs } from 'file-saver'

export default {
    methods: {
        async click (fileName) {
            const response = await axios.get(urljoin('http://localhost:3000/api/download'), {
                responseType: 'blob',
                params: {
                    'file': fileName
                }
            }).catch((error) => {
                console.log(error)
            })

            if (response && (200 == response.status)) {
                const contentDisposition = response.headers["content-disposition"]
                const contentDispositions = contentDisposition.split(';')
                const fileNames = contentDispositions[contentDispositions.length - 1].split('=')
                fileName = fileNames[fileNames.length - 1]
                saveAs(response.data, fileName)
            }
        }
    }
}
</script>
