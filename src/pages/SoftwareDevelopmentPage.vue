<template>
    <div>
        <FormBanner :service="'Software Development'" :category="category" :place="place" v-observe />

        <LeadManagement :values="features" :title="'Factors, you will love'" v-observe />

        <AutoScrolling v-observe />
        <TempCustomers :reviews="customers" title="our customers" v-observe />
        <Faq :questions="questions" v-observe />
        <Counter :service="'Software Development'" :serviceCount="2000" :category="'India'" :categoryCount="1500"
            :place="'All over the world'" :placeCount="5000" v-observe />
        <WhyChooseUs v-observe />

    </div>
</template>

<script>
import LeadManagement from '@/components/services/LeadManagement.vue'
import WhyChooseUs from '@/components/WhyChooseUs.vue'
import TempCustomers from "@/components/TempCustomers.vue";
import Faq from '@/components/FaqSection.vue';
import FormBanner from '@/components/FormBanner.vue';
import Counter from '@/components/services/SalesCounter.vue';
import AutoScrolling from '@/components/services/AutoScrolling.vue';
export default {
    name: "SoftwareDevelopment",
    components: {
        LeadManagement,
        WhyChooseUs,
        FormBanner,
        TempCustomers,
        Faq,
        Counter,
        AutoScrolling,
    },
    data() {
        return {
            services: '',
            category: '',
            place: '',
            features: [
                {
                    id: 1,
                    icon: 'bi-boxes fs-4',
                    title: "Stock Management System",
                    description: "Track inventory levels and manage stock efficiently.",
                },
                {
                    id: 2,
                    icon: 'bi-currency-dollar fs-4',
                    title: "Financial Management System",
                    description: "Handle financial transactions and budgeting seamlessly.",
                },
                {
                    id: 3,
                    icon: 'bi-credit-card fs-4',
                    title: "Payment Management System",
                    description: "Streamline payment processing and transactions.",
                },
                {
                    id: 4,
                    icon: 'bi-briefcase fs-4',
                    title: "Asset Management System",
                    description: "Manage and track company assets effectively.",
                },
                {
                    id: 5,
                    icon: 'bi-people fs-4',
                    title: "Human Resources Management System",
                    description: "Automate HR processes and manage employee data.",
                },
                {
                    id: 65,
                    icon: 'bi-file-earmark-text fs-4',
                    title: "Document Management System",
                    description: "Organize and store documents securely.",
                },
                {
                    id: 63,
                    icon: 'bi-kanban fs-4',
                    title: "Project Management System",
                    description: "Plan, track, and manage projects efficiently.",
                },
                {
                    id: 54,
                    icon: 'bi-graph-up-arrow fs-4',
                    title: "Lead Management System",
                    description: "Track and manage leads through the sales process.",
                },
            ],
            questions: [
                {
                    id: 1,
                    question: "Why do I need custom software?",
                    answer: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed quis vitae pariatur omnis iste eius earum enim distinctio libero et harum eaque sapiente nihil atque provident odio voluptate, officiis dolores!."
                },
                {
                    id: 2,
                    question: "How long will it take to develop the software?",
                    answer: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed quis vitae pariatur omnis iste eius earum enim distinctio libero et harum eaque sapiente nihil atque provident odio voluptate, officiis dolores!"
                },
                {
                    id: 3,
                    question: "How much will it cost?",
                    answer: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed quis vitae pariatur omnis iste eius earum enim distinctio libero et harum eaque sapiente nihil atque provident odio voluptate, officiis dolores!"
                },
                {
                    id: 4,
                    question: "Will the software be easy to use?",
                    answer: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed quis vitae pariatur omnis iste eius earum enim distinctio libero et harum eaque sapiente nihil atque provident odio voluptate, officiis dolores!"
                },
                {
                    id: 5,
                    question: "What are the steps involved in software development?",
                    answer: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed quis vitae pariatur omnis iste eius earum enim distinctio libero et harum eaque sapiente nihil atque provident odio voluptate, officiis dolores!"
                },
                {
                    id: 6,
                    question: "How will you handle my data and ensure privacy?",
                    answer: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed quis vitae pariatur omnis iste eius earum enim distinctio libero et harum eaque sapiente nihil atque provident odio voluptate, officiis dolores!"
                },
            ],
            customers: [
                {
                    id: 1,
                    show: false,
                    imgr: '/img/users/1.png',
                    name: 'Ram',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "We initially thought Saleswik was a small tool that only stores client data but once we started working on it, we knew its depth. We are very excited to use the new features like Team Pipelines, Email-in, and File Cabinet. We 100% recommend Saleswik to everyone!"
                },
                {
                    id: 2,
                    show: false,
                    imgr: '/img/users/2.png',
                    name: 'Shyam',
                    company: 'XYz Pvt Ltd',
                    rating: '4.5',
                    text: "Saleswik was the perfect solution for our startup, which was moving from paper-based and Excel sheets to an automated solution for sales outreach and managing incoming calls. It has all the basic functionality of other leading CRMs at half the price. In addition, onboarding/training was provided at no additional cost. I highly recommend Zoho Saleswik for any micro business."
                },
                {
                    id: 3,
                    show: false,
                    imgr: '/img/users/3.png',
                    name: 'Nikhil',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "Loved its UI. I have tried many other apps but this app is the best. The details in which the products are shown in picture is above all."
                },
                {
                    id: 4,
                    show: false,
                    imgr: '/img/users/4.png',
                    name: 'Abhishek',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "The general idea was to keep everything in one place and at an affordable price, and Saleswik was very accessible that way, and with the ability to expand without switching CRMs."
                },
                {
                    id: 5,
                    show: false,
                    imgr: '/img/users/5.png',
                    name: 'Rajan',
                    company: 'XYz Pvt Ltd',
                    rating: '4',
                    text: "When you work with software that is structured with features that make it so easy to use—that's when you realize you've struck gold and you don't want to go anywhere else. The pricing is also just right and ideal for small businesses."
                },
                {
                    id: 6,
                    show: false,
                    imgr: '/img/users/1.png',
                    name: 'Yogesh',
                    company: 'XYz Pvt Ltd',
                    rating: '4.5',
                    text: "Saleswik has been really helpful for us to keep a track on contacts and deals. Since we are small team, Saleswik was so user-friendly that we were able to start using from week 1 of our trial."
                },
                {
                    id: 7,
                    show: false,
                    imgr: '/img/users/2.png',
                    name: 'Lokesh',
                    company: 'XYz Pvt Ltd',
                    rating: '4',
                    text: "The CRM options available in the market are either too expensive, with complex features that are not essential for a small business, or are priced less with nominal features. But Saleswik is game-changing. It has exceeded our expectations such that V4 Creative cannot work without it."
                },
                {
                    id: 8,
                    show: false,
                    imgr: '/img/users/3.png',
                    name: 'Bhasker',
                    company: 'XYz Pvt Ltd',
                    rating: '3.5',
                    text: "As vendor and customers needed order visibility, we wanted to automate the entire business and found only Saleswik to be the best suited in terms of integration."
                },
                {
                    id: 9,
                    show: false,
                    imgr: '/img/users/4.png',
                    name: 'Vivek',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "Saleswik has stayed true to its value proposition—a CRM tailored for small businesses and startups."
                },
                {
                    id: 10,
                    show: false,
                    imgr: '/img/users/5.png',
                    name: 'Ankit',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "Since the implementation of Saleswik, we have seen positive outcomes in business operations and the accessibility of data. One glance at the Dashboards indicates the performance of my sales folks!"
                },
                {
                    id: 11,
                    show: false,
                    imgr: '/img/users/1.png',
                    name: 'Karan',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "The mobile app of Saleswik increases productivity on a whole different level. As a small business, it gives us the edge over our competitors and we're very happy to use Saleswik!"
                },
                {
                    id: 12,
                    show: false,
                    imgr: '/img/users/2.png',
                    name: 'Rajat',
                    company: 'XYz Pvt Ltd',
                    rating: '4',
                    text: "Saleswik helps me stay on track, lets me know where I am at any point of time and what I need to do to reach where I really want to go!"
                },
                {
                    id: 13,
                    show: false,
                    imgr: '/img/users/3.png',
                    name: 'Ajay',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "Since I started using Saleswik, no lead has been lost. The student conversion rate has increased by 25 percent, to 30 percent."
                },
                {
                    id: 14,
                    show: false,
                    imgr: '/img/users/4.png',
                    name: 'Vikas',
                    company: 'XYz Pvt Ltd',
                    rating: '5',
                    text: "Saleswik has helped us to decentralize information. Now all the team has access to the documents and sales information. We no longer have the problem that some documents is stored on the PC of a teammate who is not accessible at the time."
                },
            ]
        }
    },
    created() {
        // Log the route params to debug
        console.log('Route params:', this.$route.params);

        // Extract the route parameter by the correct name
        const routeParam = this.$route.params.title; // Use 'slug' if that is the parameter name

        // Check if routeParam is defined
        if (routeParam) {
            this.extractParams(routeParam);
        } else {
            console.error('Route parameter is undefined');
        }
    },
    methods: {
        extractParams(paramString) {
            // Split the string based on ' in ' keyword and then further parse it
            let parts = paramString.split('-in-');
            if (parts.length >= 2) {
                this.services = parts[0].replace(/-/g, ' ');
                this.category = parts[1].replace(/-/g, ' ');

                // Check if there is a third part for the place
                if (parts.length > 2) {
                    this.place = parts.slice(2).join(' ').replace(/-/g, ' ');
                }
            }
        }
    }
}
</script>
<style lang="">

</style>
