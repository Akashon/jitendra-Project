<template>
    <div class="site__body">
        <div class="block-space block-space--layout--after-header"></div>
        <div class="block">
            <div class="container container--max--xl">
                <div class="row">
                    <DashSideMenu />
                    <div class="col-12 col-lg-9 mt-4 mt-lg-0">
                        <div class="dashboard">
                            <div class="dashboard__profile card profile-card">
                                <div class="card-body profile-card__body">
                                    <div class="profile-card__avatar"><img
                                            src="https://images.unsplash.com/photo-1633332755192-727a05c4013d?q=80&w=2080&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
                                            alt="">
                                    </div>
                                    <div class="profile-card__name">Mr.Rocky</div>
                                    <div class="profile-card__email">rocky@example.com</div>
                                    <div class="profile-card__edit"><a href="account-profile.html"
                                        class="btn btn-secondary btn-sm">Edit Profile</a>
                                    </div>

                                    <!-- <button class="btn btn-light "
                                        style="color: #E52727; border-color: #E52727; font-weight: 400;">Edit
                                        Profile</button> -->
                                </div>
                            </div>
                            <div class="dashboard__address card address-card address-card--featured">
                                <div class="address-card__badge tag-badge tag-badge--theme">Default</div>
                                <div class="address-card__body">
                                    <div class="address-card__name">Mr.Rocky</div>
                                    <div class="address-card__row">Random Federation<br>115302, Moscow<br>ul.
                                        Varshavskaya, 15-2-178</div>
                                    <div class="address-card__row">
                                        <div class="address-card__row-title">Phone Number</div>
                                        <div class="address-card__row-content">38 972 588-42-36</div>
                                    </div>
                                    <div class="address-card__row">
                                        <div class="address-card__row-title">Email Address</div>
                                        <div class="address-card__row-content">helena@example.com</div>
                                    </div>
                                </div>
                            </div>
                            <div class="dashboard__orders card">
                                <div class="card-header">
                                    <h5>Recent Orders</h5>
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
                                                    <td><a href="/dashboard/order-detail"
                                                            style="color: #cb1818;">#8132</a></td>
                                                    <td>02 April, 2023</td>
                                                    <td>Pending</td>
                                                    <td>12,719.00 for 5 item(s)</td>
                                                </tr>
                                            </tbody>
                                        </table>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="block-space block-space--layout--before-footer"></div>
    </div><!-- site__body / end --><!-- site__footer -->
</template>