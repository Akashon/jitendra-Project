<template>
    <div class="block-categories__item category-card category-card--layout--classic" @click="showModal = true">
        <div class="category-card__body">
            <div class="category-card__content row">
                <div class="category-card__image image image--type--category">
                    <a href="#" class="image__body">
                        <img class="image__tag" style="position: absolute;"
                            src="https://red-parts.html.themeforest.scompiler.ru/themes/red-ltr/images/categories/category-5-160x160.jpg"
                            alt="">
                    </a>
                </div>
                <div class="category-card__info">
                    <div class="category-card__name"><a href="#">Headlights</a></div>
                    <ul class="category-card__children">
                        <li v-for="(item, index) in paddedList" :key="index">
                            <a href="#" class="text-truncate" v-if="item" :href="item.link">{{ item.name }}</a>
                            <span v-else>&nbsp;</span>
                        </li>
                    </ul>
                    <div class="category-card__actions"><span class="category-card__link" @click="showModal = true">Shop
                            All</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Modal -->
    <div class="modal fade" tabindex="-1" role="dialog" :class="{ show: showModal }"
        :style="showModal ? 'display: block; background-color: rgba(0,0,0,0.5)' : 'display: none'">
        <div class="modal-dialog modal-dialog-centered" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <button type="button" class="close" @click="closeModal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    Do you want to see more products? If yes then go to the login page and login and see the details.
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" @click="closeModal">
                        Close
                    </button>
                    <a href="/login" type="button" class="btn btn-danger">Login</a>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    data() {
        return {
            showModal: false,

            // List of category links
            categories: [
                { name: "Headlights", link: "#" },
                { name: "Tail Lights", link: "#" },
                { name: "Fog Lights", link: "#" },
                { name: "Turn Signals", link: "#" },
                { name: "Switches & Relays", link: "#" }
            ]
        };
    },
    methods: {
        closeModal() {
            this.showModal = false;
        },
    },
    computed: {
        // Create a computed property to ensure there are at least 6 items
        paddedList() {
            const minItems = 0;
            const padded = [...this.categories]; // Clone the list
            while (padded.length < minItems) {
                padded.push(null); // Add empty items to pad the list
            }
            return padded;
        }
    }
};
</script>

<!-- Include Bootstrap 4 CSS -->
