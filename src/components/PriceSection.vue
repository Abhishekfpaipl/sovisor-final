<template>
    <div class="my-3 py-3">
        <div class="container">
            <h1 class="text-center text-capitalize">Services</h1>
            <small>No hidden charges only pay what you see</small>

            <div class="my-3">
                <ul class="nav nav-pills justify-content-center sticky-container" id="pills-tab" role="tablist">
                    <div class="d-flex border p-2 px-3 rounded shadow " style="">
                        <li class="nav-item" role="presentation" v-for="(price, index) in pricing" :key="index">
                            <button class="nav-link text-muted" :class="{ 'active': index === 0 }" :id="'tab-' + index"
                                data-bs-toggle="pill" :data-bs-target="'#content-' + index" type="button" role="tab"
                                :aria-controls="'content-' + index" :aria-selected="index === 0">{{ price.name
                                }}</button>
                        </li>
                    </div>
                </ul>
                <div class="tab-content mt-2 pt-4" id="pills-tabContent">
                    <div class="tab-pane fade" :class="{ 'show active': index === 0 }" v-for="(price, index) in pricing"
                        :key="index" :id="'content-' + index" role="tabpanel" :aria-labelledby="'tab-' + index"
                        tabindex="0">
                        <div class="d-md-flex justify-content-center gap-3">
                            <div v-for="(plan, index) in price.plans" :key="index"
                                class="card mb-3 px-3 bg-light rounded-0" :class="{ 'recommended': index === 1 }">

                                <div v-if="index === 1" class="position-absolute top-0 start-0 m-2 ms-0"
                                    style="font-size: 12px;">
                                    <span class='text-dark fw-bold bg-warning p-1 px-2 rounded-end-3'>Recommended</span>
                                </div>

                                <div class="py-2 border-bottom fw-bold">{{
                                    plan.name }}</div>
                                <div class="card-body text-center">
                                    <p v-if="plan.price" class="mb-0 card-title fs-3">₹ <span class="fw-bold">{{
                                        plan.price }} </span></p>
                                    <p v-else class="mb-0 card-title fs-3 fw-bold">Custom</p>
                                    <p v-if="plan.price"><small class="text-capitalize">{{ plan.tag
                                            }}</small></p>
                                    <p v-else>Price, as per requirement</p>
                                    <div v-if="plan.price" class="d-flex justify-content-center align-items-center">
                                        <p class="fw-light d-inline-block px-4 rounded-3"
                                            style="background-color: var(--brand-color)">
                                            <span class="text-decoration-line-through text-white">{{ plan.mrp }}</span>
                                            <span class="text-white"> ({{ getDiscount(plan) }}% discount)</span>
                                        </p>
                                    </div>
                                    <p v-else class="fw-light d-inline-block px-4 rounded-3 text-white"
                                        style="background-color: var(--brand-color)"> No discount available</p>

                                    <ul v-if="plan.features" class="list-group">
                                        <small class="text-start text-uppercase fw-bold my-2 text-primary">{{ plan.key
                                            }}</small>
                                        <li v-for="(feature, featureIndex) in plan.features" :key="featureIndex"
                                            class="px-0 d-flex justify-content-between list-group-item text-start text-capitalize border-0">
                                            <div class="">
                                                <i class="bi bi-check-circle text-success"></i>
                                                <span class="px-2">
                                                    {{ feature.text }}
                                                </span>
                                            </div>
                                            <i class="bi bi-info-circle" data-bs-toggle="tooltip"
                                                data-bs-placement="top" data-bs-custom-class="custom-tooltip"
                                                :data-bs-title="feature.tooltip"></i>
                                        </li>
                                    </ul>
                                </div>
                                <div class="card-footer bg-light p-0 border-top pt-2">
                                    <p class="card-text text-capitalize">{{ plan.description }}</p>
                                    <div class="btn-group d-flex justify-content-center my-3">
                                        <router-link :to="plan.link + plan.price"
                                            class="btn btn-light w-100 border">Know more</router-link>
                                        <button class="btn btn-warning w-100"><i class="bi bi-whatsapp me-2"></i>
                                            Enquiry</button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "PriceSection",
    data() {
        return {
            pricing: [
                {
                    id: 2,
                    name: "Digital Marketing",
                    description: "This is a basic plan",
                    plans: [
                        {
                            id: 1,
                            name: "Starter",
                            price: "500",
                            mrp: "5,000",
                            link: "/digital-marketing/",
                            tag: "/user/yearly/billed yearly",
                            description: "Start with our starter plan and upgrade only when you need additional features.",
                            button: "Get Started",
                            key: "key features",
                            features: [
                                {
                                    text: "single Pipelines",
                                    tooltip: "get a quick summary fo your customer-facing process and manage opportunities across different stages."
                                },
                                {
                                    text: "500 Records",
                                    tooltip: "Each row of data you enter in pipelines, contacts, companies, activities and notes are called records in saleswik."
                                },
                                {
                                    text: "Automations (3)",
                                    tooltip: "Automate repetitive actions by setting up triggers and specifying the conditions to be met for the execution of the actions."
                                },
                                {
                                    text: "telephony",
                                    tooltip: "Make and receive phone calls, record them , set up automated voice responses, and use call routing--dicrectly in saleswik."
                                },
                            ]
                        },
                        {
                            id: 2,
                            name: "Enterprise",
                            price: "1000",
                            mrp: "10,000",
                            link: "/digital-marketing/",
                            tag: "/user/yearly/billed yearly",
                            description: "Choose the right set of features you need to begin your  journey.",
                            button: "Get Started",
                            button2: "Buy now",
                            key: "key features",
                            features: [
                                {
                                    text: "Team Pipelines (3)",
                                    tooltip: "Create distinct pipelines for every team and unify all your customer-facing operations."
                                },
                                {
                                    text: "500000 Records",
                                    tooltip: "Each row of data you enter in pipelines, contacts, companies, activities adn notes are called records in saleswik. You can purchase additional records if you need to store more than 50000 records."
                                },
                                {
                                    text: "Automations (30)",
                                    tooltip: "Automate a wider range of instant actions to further reduce the time, effort, and errors that go into doing mundane tasks."
                                },
                                {
                                    text: "Email & WhatsApp Business Integration",
                                    tooltip: "Connect all major services to your saleswik account with IMAP, send mass emails, and get email open/click notifications."
                                },
                            ]
                        },
                        {
                            id: 3,
                            name: "Business",
                            // price: "5,000",
                            // mrp: "50,000",
                            link: "/digital-marketing/",
                            tag: "/user/yearly/billed yearly",
                            description: "Enjoy our advanced offering for fast-growing businesses and startups.",
                            button: "Get Started",
                            button2: "Buy now",
                            key: "key features",
                            features: [
                                {
                                    text: "Team Pipelines",
                                    tooltip: "Get aquick summary of every customer-facing operation by creating distinct pipelines for each team."
                                },
                                {
                                    text: "100000 Records",
                                    tooltip: "Each row of data you enter in pieplines, contacts, companies, activities and notes are called records in saleswik. You can purchase additional records if you need to store more than 100000 records."
                                },
                                {
                                    text: "Advanced automation (50)",
                                    tooltip: "Schedule workflows that are triggered at specified time intervals."
                                },
                                {
                                    text: "Stage transition rules",
                                    tooltip: "Set up rules for moving deals in your pipelines, create checkpoints to enxure deals properly transition between stages."
                                },
                            ]
                        }
                    ]
                },
                {
                    id: 3,
                    name: "Website Development",
                    description: "This is a basic plan",
                    plans: [
                        {
                            id: 1,
                            name: "Starter",
                            price: "1,250",
                            mrp: "5,000",
                            link: "/website-development/",
                            tag: "/user/quartly/billed quartly",
                            description: "Start with our starter plan and upgrade only when you need additional features.",
                            button: "Get Started",
                            key: "key features",
                            features: [
                                {
                                    text: "single Pipelines",
                                    tooltip: "get a quick summary fo your customer-facing process and manage opportunities across different stages."
                                },
                                {
                                    text: "500 Records",
                                    tooltip: "Each row of data you enter in pipelines, contacts, companies, activities and notes are called records in saleswik."
                                },
                                {
                                    text: "Automations (3)",
                                    tooltip: "Automate repetitive actions by setting up triggers and specifying the conditions to be met for the execution of the actions."
                                },
                                {
                                    text: "telephony",
                                    tooltip: "Make and receive phone calls, record them , set up automated voice responses, and use call routing--dicrectly in saleswik."
                                },
                            ]
                        },
                        {
                            id: 2,
                            name: "Enterprise",
                            price: "2,500",
                            mrp: "10,000",
                            link: "/website-development/",
                            tag: "/user/quartly/billed quartly",
                            description: "Choose the right set of features you need to begin your journey.",
                            button: "Get Started",
                            button2: "Buy now",
                            key: "key features",
                            features: [
                                {
                                    text: "Team Pipelines (3)",
                                    tooltip: "Create distinct pipelines for every team and unify all your customer-facing operations."
                                },
                                {
                                    text: "500000 Records",
                                    tooltip: "Each row of data you enter in pipelines, contacts, companies, activities adn notes are called records in saleswik. You can purchase additional records if you need to store more than 50000 records."
                                },
                                {
                                    text: "Automations (30)",
                                    tooltip: "Automate a wider range of instant actions to further reduce the time, effort, and errors that go into doing mundane tasks."
                                },
                                {
                                    text: "Email & WhatsApp Business Integration",
                                    tooltip: "Connect all major services to your saleswik account with IMAP, send mass emails, and get email open/click notifications."
                                },
                            ]
                        },
                        {
                            id: 3,
                            name: "Business",
                            // price: "Custom",
                            // mrp: "50,000",
                            link: "/website-development/",
                            tag: "/user/quartly/billed quartly",
                            description: "Enjoy our advanced offering for fast-growing businesses and startups.",
                            button: "Get Started",
                            button2: "Buy now",
                            key: "key features",
                            features: [
                                {
                                    text: "Team Pipelines",
                                    tooltip: "Get aquick summary of every customer-facing operation by creating distinct pipelines for each team."
                                },
                                {
                                    text: "100000 Records",
                                    tooltip: "Each row of data you enter in pieplines, contacts, companies, activities and notes are called records in saleswik. You can purchase additional records if you need to store more than 100000 records."
                                },
                                {
                                    text: "Advanced automation (50)",
                                    tooltip: "Schedule workflows that are triggered at specified time intervals."
                                },
                                {
                                    text: "Stage transition rules",
                                    tooltip: "Set up rules for moving deals in your pipelines, create checkpoints to enxure deals properly transition between stages."
                                },
                            ]
                        }
                    ]
                },
                {
                    id: 1,
                    name: "Software Development",
                    description: "This is a basic plan",
                    plans: [
                        {
                            id: 1,
                            name: "Starter",
                            price: "2,500",
                            mrp: "5,000",
                            link: "/software-development/",
                            tag: "/user/month/billed monthly",
                            description: "Start with our starter plan and upgrade only when you need additional features.",
                            button: "Get Started",
                            key: "key features",
                            features: [
                                {
                                    text: "single Pipelines",
                                    tooltip: "get a quick summary fo your customer-facing process and manage opportunities across different stages."
                                },
                                {
                                    text: "500 Records",
                                    tooltip: "Each row of data you enter in pipelines, contacts, companies, activities and notes are called records in saleswik."
                                },
                                {
                                    text: "Automations (3)",
                                    tooltip: "Automate repetitive actions by setting up triggers and specifying the conditions to be met for the execution of the actions."
                                },
                                {
                                    text: "telephony",
                                    tooltip: "Make and receive phone calls, record them , set up automated voice responses, and use call routing--dicrectly in saleswik."
                                },
                            ]
                        },
                        {
                            id: 2,
                            name: "Enterprise",
                            price: "5,000",
                            mrp: "10,000",
                            link: "/software-development/",
                            tag: "/user/month/billed monthly",
                            description: "Choose the right set of features you need to begin your journey.",
                            button: "Get Started",
                            button2: "Buy now",
                            key: "key features",
                            features: [
                                {
                                    text: "Team Pipelines (3)",
                                    tooltip: "Create distinct pipelines for every team and unify all your customer-facing operations."
                                },
                                {
                                    text: "500000 Records",
                                    tooltip: "Each row of data you enter in pipelines, contacts, companies, activities adn notes are called records in saleswik. You can purchase additional records if you need to store more than 50000 records."
                                },
                                {
                                    text: "Automations (30)",
                                    tooltip: "Automate a wider range of instant actions to further reduce the time, effort, and errors that go into doing mundane tasks."
                                },
                                {
                                    text: "Email & WhatsApp Business Integration",
                                    tooltip: "Connect all major services to your saleswik account with IMAP, send mass emails, and get email open/click notifications."
                                },
                            ]
                        },
                        {
                            id: 3,
                            name: "Business",
                            // price: "25,000",
                            // mrp: "50,000",
                            link: "/software-development/",
                            tag: "/user/month/billed monthly",
                            description: "Enjoy our advanced offering for fast growing businesses and startups.",
                            button: "Get Started",
                            button2: "Buy now",
                            key: "key features",
                            features: [
                                {
                                    text: "Team Pipelines",
                                    tooltip: "Get aquick summary of every customer-facing operation by creating distinct pipelines for each team."
                                },
                                {
                                    text: "100000 Records",
                                    tooltip: "Each row of data you enter in pieplines, contacts, companies, activities and notes are called records in saleswik. You can purchase additional records if you need to store more than 100000 records."
                                },
                                {
                                    text: "Advanced automation (50)",
                                    tooltip: "Schedule workflows that are triggered at specified time intervals."
                                },
                                {
                                    text: "Stage transition rules",
                                    tooltip: "Set up rules for moving deals in your pipelines, create checkpoints to enxure deals properly transition between stages."
                                },
                            ]
                        }
                    ]
                },


            ],
        };
    },
    mounted() {
        this.initTooltips();
    },
    updated() {
        this.initTooltips();
    },
    methods: {
        initTooltips() {
            // Initialize tooltips (assuming using Bootstrap's tooltip)
            const tooltipTriggerList = [].slice.call(
                document.querySelectorAll('[data-bs-toggle="tooltip"]')
            );
            tooltipTriggerList.forEach(function (tooltipTriggerEl) {
                new window.bootstrap.Tooltip(tooltipTriggerEl);
            });
        },
        getDiscount(plan) {
            if (plan.mrp && typeof plan.mrp === 'string') {
                const mrp = parseFloat(plan.mrp.replace(/[^\d.-]/g, ''));
                const price = parseFloat(plan.price.replace(/[^\d.-]/g, ''));
                if (!isNaN(mrp) && !isNaN(price) && mrp > 0) {
                    return ((mrp - price) / mrp * 100).toFixed(0);
                }
            }
            return 0; // Default return if calculation fails
        }

    }
};
</script>

<style scoped>
.nav-link {
    transition: background-color 0.3s ease, color 0.3s ease;
}

.nav-link.active {
    background-color: var(--brand-color) !important;
    color: white !important;
    transition: background-color 0.3s ease, color 0.3s ease, transform 0.3s ease;
    /* transform: scale(1.2); */
}

.sticky-container {
    position: sticky;
    top: 70px;
    z-index: 1000;
    background-color: white;
}


/* .recommended {
    border: 4px solid #efc107; 
    position: relative;
}

.recommended::before {
    content: "Recommended";
    position: absolute;
    top: -20px;
    left: -4px;
    width: 102.5%;
    background: #efc107; 
    color: white;
    padding: 5px 10px;
    font-size: 0.9rem;
    font-weight: bold;
    border-radius: 3px;
} */

/* Add any necessary styling here */
</style>
