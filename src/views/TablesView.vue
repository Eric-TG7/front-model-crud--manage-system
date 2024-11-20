<template>
  <div>
    <title-bar :title-stack="titleStack" />
    <hero-bar>
      Tables
      <router-link
        slot="right"
        to="/"
        class="button"
      >
        Dashboard
      </router-link>
    </hero-bar>
    <section class="section is-main-section">
      <notification-bar class="is-info">
        <div>
          <b-icon
            icon="buffer"
            custom-size="default"
          />
          <b>Sorted and paginated table.</b>&nbsp;Based on Buefy's table.
        </div>
      </notification-bar>

      <card-component
        class="has-table has-mobile-sort-spaced"
        title="Category"
        icon="account-multiple"
      >
        <clients-table-sample
          checkable
        />
      </card-component>

      <hr>

      <notification-bar class="is-info">
        <div>
          <b-icon
            icon="buffer"
            custom-size="default"
          />
          <b>Tightly wrapped</b> &mdash; table header becomes card header
        </div>
      </notification-bar>

      <card-component 
  class="has-table has-mobile-sort-spaced"
  title="Customer"
      >
        <clients-table-sample-customer
          checkable
        />
      </card-component>

      <hr>

      <notification-bar class="is-info">
        <div>
          <b-icon
            icon="buffer"
            custom-size="default"
          />
          <b>Empty table.</b> When there's nothing to show
        </div>
      </notification-bar>

      <card-component
        title="Employee">
        <clients-table-sample-employee />
      </card-component>
      <card-component
        title="Shipper">
        <clients-table-sample-shipper />
      </card-component>
      <card-component
        title="Supplier">
        <clients-table-sample-supplier />
      </card-component>
       <card-component
        class="has-table has-mobile-sort-spaced"
        title="Category"
        icon="account-multiple"
      >
        <clients-table-sample
          checkable
        />
      </card-component>
    </section>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import NotificationBar from '@/components/NotificationBar.vue'
import ClientsTableSample from '@/components/ClientsTableSample.vue'
import CardComponent from '@/components/CardComponent.vue'
import TitleBar from '@/components/TitleBar.vue'
import HeroBar from '@/components/HeroBar.vue'
import ClientsTableSampleCustomer from '@/components/ClientsTableSampleCustomer.vue'
import ClientsTableSampleEmployee from '@/components/ClientsTableSampleEmployee.vue'
import ClientsTableSampleShipper from '@/components/ClientsTableSampleShipper.vue'
import ClientsTableSampleSupplier from '@/components/ClientsTableSampleSupplier.vue'

export default defineComponent({
  name: 'TablesView',
  components: {
    HeroBar,
    TitleBar,
    CardComponent,
    ClientsTableSample,
    ClientsTableSampleEmployee,
    NotificationBar,
    ClientsTableSampleCustomer,
    ClientsTableSampleShipper,
    ClientsTableSampleSupplier
  },
  data () {
    return {
      titleStack: ['Admin', 'Tables']
    }
  }
})
</script>
