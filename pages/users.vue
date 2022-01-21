<template>
    <v-layout
        column
        justify-center
        align-center
    >
        <v-card v-if="users">
            <v-card-title>
                User List
                <v-spacer />
                <v-text-field
                    v-model="search"
                    append-icon="mdi-magnify"
                    label="search"
                    single-line
                />
            </v-card-title>
            <v-data-table
                :headers="headers"
                :items="users"
                :items-per-page="5"
                :search="search"
                sort-by="id"
                :sort-desc="true"
                class="elevation-1"
            >
            </v-data-table>
        </v-card>
    </v-layout>
</template>

<script>
export default {
    data() {
        return {
            search: '',
            headers: [
                { text: 'ID', value: 'id' },
                { text: 'MailAddress', value: 'email' },
                { text: 'Name', value: 'name' },
                { text: 'Memo', value: 'memo' },
            ]
        }
    },
}
</script>