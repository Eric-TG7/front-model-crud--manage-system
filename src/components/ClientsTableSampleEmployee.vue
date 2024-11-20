<template>
  <div>
    <modal-box
      :is-active="isModalActive"
      :trash-object-name="trashObject ? trashObject.name : null "
      @confirm="trashConfirm"
      @cancel="trashCancel"
    />
    <b-table
      :checked-rows.sync="checkedRows"
      :paginated="paginated"
      :per-page="perPage"
      :data="ally"
      default-sort="name"
      striped
      hoverable
    >
      <b-table-column
        v-slot="props"
        label="Full Name"
        field="categoryName"
        sortable
      >
        {{ props.row.firstName }}
        {{ props.row.lastName }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Title"
        field="company"
        sortable
      >
        {{ props.row.title }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="City"
        field="city"
        sortable
      >
        {{ props.row.city }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="title Courtesy"
        field="city"
        sortable
      >
        {{ props.row.titleOfCourtesy }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Birth Date"
        field="city"
        sortable
      >
        {{ props.row.birthDate }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Hire Date"
        field="city"
        sortable
      >
        {{ props.row.hireDate }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Adress"
        field="city"
        sortable
      >
        {{ props.row.address }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Region"
        field="city"
        sortable
      >
        {{ props.row.region }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Postal Code"
        field="city"
        sortable
      >
        {{ props.row.postalCode }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Country"
        field="city"
        sortable
      >
        {{ props.row.country }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Home Phone"
        field="city"
        sortable
      >
        {{ props.row.homePhone }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Extension"
        field="city"
        sortable
      >
        {{ props.row.extension }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Photo"
        field="city"
        sortable
      >
        {{ props.row.photo }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Notes"
        field="city"
        sortable
      >
        {{ props.row.notes }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        label="Reports"
        field="city"
        sortable
      >
        {{ props.row.reportsTo }}
      </b-table-column>
      <b-table-column
        v-slot="props"
        custom-key="actions"
        cell-class="is-actions-cell"
      >
        <div class="buttons is-right no-wrap">
          <router-link
            :to="{name:'client.edit', params: {id: props.row.id}}"
            class="button is-small is-info"
          >
            <b-icon
              icon="account-edit"
              size="is-small"
            />
          </router-link>
          <b-button
            type="is-danger"
            size="is-small"
            @click.prevent="trashModalOpen(props.row)"
          >
            <b-icon
              icon="trash-can"
              size="is-small"
            />
          </b-button>
        </div>
      </b-table-column>

      <section
        slot="empty"
        class="section"
      >
        <div class="content has-text-grey has-text-centered">
          <p>
            <b-icon
              icon="emoticon-sad"
              size="is-large"
            />
          </p>
          <p>Nothing's here&hellip;</p>
        </div>
      </section>
    </b-table>
  </div>
</template>
<script>
import { defineComponent } from 'vue'
import { mapState } from 'vuex'
import ModalBox from '@/components/ModalBox.vue'
import axios from 'axios'
import TitleBar from '@/components/TitleBar.vue';
export default defineComponent({
  name: 'ClientsTableSample',
  components: { ModalBox },
  props: {
    checkable: Boolean,
    isEmpty: Boolean,
    perPage: {
      type: Number,
      default: 10
    }
  },
  data () {
    return {
      checkedRows: [],
      isModalActive: false,
      trashObject: null,
      names: null,
      description: null,
      pict: null,
      ally: []
    }
  },
  computed: {
    paginated () {
      return this.clients.length > this.perPage
    },
    ...mapState([
      'clients'
    ])
  },
  async mounted () {
    try {
      const response = await axios.get('http://localhost:8080/api/employee2')
      this.ally = response.data
      console.log(this.ally)
    } catch (error) {
      console.error('Error fetching variable:', error)
    }
  },

  methods: {
    trashModalOpen (obj) {
      this.trashObject = obj
      this.isModalActive = true
    },
    trashConfirm () {
      this.isModalActive = false

      this.$buefy.snackbar.open({
        message: 'Confirmed',
        queue: false
      })
    },
    trashCancel () {
      this.isModalActive = false
    }
  }
})
</script>
