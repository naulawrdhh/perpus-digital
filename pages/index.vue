<template>
    <div>
        <table border="1" width="100%">
            <thead>
                <tr>
                    <th>#</th>
                    <th>TGL</th>
                    <th>nama</th>
                    <th>anggota</th>
                    <th>keperluan</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="pengunjung in visitors" :key="pengunjung.id">
                    <td>{{ pengunjung.id }}</td>
                    <td>{{ pengunjung.tgl }}</td>
                    <td>{{ pengunjung.nama }}</td>
                    <td>{{ pengunjung.anggota }}</td>
                    <td>{{ pengunjung.keperluan }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const visitors = ref([])

async function getData() {
const { data, error } = await supabase
    .from('pengunjung')
    .select()
if(data) visitors.value = data
}
onMounted(() => {
getData()
})
</script>
