<!-- <template>
    <div class="site__body ">
        <div class="block-space block-space--layout--after-header"></div>
        <div class="block">
            <div class="container container--max--xl">
                <div class="row">
                    <DasSideMenu />
                    <div class="col-12 col-lg-9 mt-4 mt-lg-0">
                        <div class="card">
                            <div class="card-header">
                                <h5>Order History</h5>
                            </div>
                            <div class="card-divider"></div>
                            <div class="card-table">
                                <div class="table-responsive-sm">
                                    <table>
                                        <thead>
                                            <tr>
                                                <th>Order</th>
                                                <th>Date</th>
                                                <th>Status</th>
                                                <th>Total</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <tr>
                                                <td><a href="/dashboard/order-detail" style="color: #cb1818;">#8132</a>
                                                </td>
                                                <td>02 April, 2019</td>
                                                <td>Pending</td>
                                                <td>12,719.00 for 5 item(s)</td>
                                            </tr>
                                            <tr>
                                                <td><a href="/dashboard/order-detail" style="color: #cb1818;">#7592</a>
                                                </td>
                                                <td>28 March, 2019</td>
                                                <td>Pending</td>
                                                <td>1374.00 for 3 item(s)</td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                            <div class="card-divider"></div>
                            <div class="card-footer">
                                <ul class="pagination">
                                    <li class="page-item disabled"><a class="page-link page-link--with-arrow" href="#"
                                            aria-label="Previous"><span class="page-link__arrow page-link__arrow--left"
                                                aria-hidden="true"><i class="fa fa-chevron-left"></i></span></a></li>
                                    <li class="page-item"><a class="page-link" href="#">1</a></li>
                                    <li class="page-item active" aria-current="page"><span class="page-link">2 <span
                                                class="sr-only">(current)</span></span></li>
                                    <li class="page-item"><a class="page-link" href="#">3</a></li>
                                    <li class="page-item"><a class="page-link" href="#">4</a></li>
                                    <li class="page-item page-item--dots">
                                        <div class="pagination__dots"></div>
                                    </li>
                                    <li class="page-item"><a class="page-link" href="#">9</a></li>
                                    <li class="page-item"><a class="page-link page-link--with-arrow" href="#"
                                            aria-label="Next"><span class="page-link__arrow page-link__arrow--right"
                                                aria-hidden="true"><i class="fa fa-chevron-right"></i></span></a></li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="block-space block-space--layout--before-footer"></div>
    </div>
</template> -->

<template>
    <div class="site__body">
        <div class="block-space block-space--layout--after-header"></div>
        <div class="block">
            <div class="container container--max--xl">
                <div class="row">
                    <DasSideMenu />
                    <div class="col-12 col-lg-9 mt-4 mt-lg-0">
                        <div class="card">
                            <div class="card-header">
                                <h5>Order History</h5>
                            </div>
                            <div class="card-divider"></div>
                            <div class="card-table">
                                <div class="table-responsive-sm">
                                    <table class="table table-bordered">
                                        <thead>
                                            <tr>
                                                <th>Order</th>
                                                <th>Date</th>
                                                <th>Status</th>
                                                <th>Total</th>
                                            </tr>
                                        </thead>
                                        <tbody>
                                            <tr v-for="order in paginatedOrders" :key="order.id">
                                                <td>
                                                    <a :href="'/dashboard/order-detail/' + order.id"
                                                        style="color: #cb1818;">#{{ order.id }}</a>
                                                </td>
                                                <td>{{ order.date }}</td>
                                                <td>{{ order.status }}</td>
                                                <td>{{ order.total }}</td>
                                            </tr>
                                            <tr v-if="paginatedOrders.length === 0">
                                                <td colspan="4" class="text-center">No orders found.</td>
                                            </tr>
                                        </tbody>
                                    </table>
                                </div>
                            </div>
                            <div class="card-divider"></div>
                            <div class="card-footer">
                                <ul class="pagination">
                                    <li class="page-item" :class="{ disabled: currentPage === 1 }">
                                        <a class="page-link" href="#" @click.prevent="changePage(currentPage - 1)">
                                            <i class="fa fa-chevron-left"></i>
                                        </a>
                                    </li>

                                    <li class="page-item" v-for="page in totalPages" :key="page"
                                        :class="{ active: currentPage === page }">
                                        <a class="page-link" href="#" @click.prevent="changePage(page)">
                                            {{ page }}
                                        </a>
                                    </li>

                                    <li class="page-item" :class="{ disabled: currentPage === totalPages }">
                                        <a class="page-link" href="#" @click.prevent="changePage(currentPage + 1)">
                                            <i class="fa fa-chevron-right"></i>
                                        </a>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="block-space block-space--layout--before-footer"></div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const orders = ref([
    { id: 8132, date: '02 April, 2019', status: 'Pending', total: '12,719.00 for 5 item(s)' },
    { id: 7592, date: '28 March, 2019', status: 'Pending', total: '1,374.00 for 3 item(s)' },
    { id: 7521, date: '25 March, 2019', status: 'Delivered', total: '2,148.00 for 2 item(s)' },
    { id: 7463, date: '22 March, 2019', status: 'Cancelled', total: '4,000.00 for 4 item(s)' },
    { id: 7301, date: '18 March, 2019', status: 'Delivered', total: '920.00 for 1 item(s)' },
    { id: 7280, date: '15 March, 2019', status: 'Pending', total: '3,200.00 for 3 item(s)' },
    { id: 7102, date: '10 March, 2019', status: 'Delivered', total: '1,800.00 for 2 item(s)' },
    { id: 6900, date: '05 March, 2019', status: 'Delivered', total: '1,500.00 for 1 item(s)' },
    { id: 6821, date: '01 March, 2019', status: 'Returned', total: '2,400.00 for 2 item(s)' },
    { id: 6700, date: '28 Feb, 2019', status: 'Delivered', total: '1,800.00 for 2 item(s)' },
])

const currentPage = ref(1)
const perPage = 6

const totalPages = computed(() => Math.ceil(orders.value.length / perPage))

const paginatedOrders = computed(() => {
    const start = (currentPage.value - 1) * perPage
    return orders.value.slice(start, start + perPage)
})

function changePage(page) {
    if (page > 0 && page <= totalPages.value) {
        currentPage.value = page
    }
}
</script>

<style scoped>
.pagination {
    margin-bottom: 0;
}

.card-table {
    padding: 1rem;
}

.card-divider {
    border-top: 1px solid #dee2e6;
}
</style>