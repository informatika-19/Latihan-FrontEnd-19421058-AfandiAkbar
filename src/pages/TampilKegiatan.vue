<template>
  <div class="q-pa-md">
    <q-table
      title="List Kegiatan"
      :data="data"
      :columns="columns"
      row-key="name"
    >
      <template v-slot:body="props">
        <q-tr :props="props">
          <q-td key="namaKegiatan" :props="props">
            {{ props.row.namaKegiatan }}
          </q-td>
        </q-tr>
      </template>
    </q-table>
  </div>
</template>
<script>
export default {
  data () {
    return {
      columns: [
        {
          name: 'namaKegiatan',
          label: 'Nama Kegiatan',
          field: 'namaKegiatan',
          align: 'center',
          sortable: true
        },
        { name: 'aksi', label: 'Aksi', field: 'aksi', align: 'center' }
      ],
      data: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$axios.get('Kegiatan/getall').then(res => {
        if (res.data.status) {
          this.data = res.data.data
        }
      })
    }
  }
}
</script>
