<template>
    <div class="chapman-cares">
        <HeadingText>Chapman Cares</HeadingText>

        <img
            :src="require('@/assets/cares-banner.jpg')"
            alt="Chapman Cares"
            class="banner-img"
        />

        <div v-for="(event, index) in events" :key="index" class="event">
            <h3 class="event-name">{{ event.name }}</h3>
            <p class="event-text"><img class="body-image banner-img" :src="event.image" :alt="event.alt"> {{ event.text }}</p>
        </div>
    </div>
</template>

<script>
import HeadingText from '@/components/heading-text';

export default {
    name: 'ChapmanCares',
    components: {
        HeadingText,
    },
    data() {
        return {
            events: [
                {
                    name: 'Making Strides Against Cancer',
                    text:
                        'Thousands of people, young and old, participated in the Making Strides Against Breast Cancer event at Tempe Beach Park. As a sponsorship partner, Chapman Auto brought the Breast Cancer Pace Car, driven by Danica Patrick. Chapman Auto employees participated in the walk, helping to raise thousands of dollars for breast cancer research.',
                    image: require('@/assets/making-strides.jpg'),
                    alt: 'Offical Pace Car'
                },
                {
                    name: 'Canine Companions For Independence',
                    text:
                        'Chapman Auto has been a proud supporter of Canine Companions for Independence for more than 10 years. From sponsoring a golf tournament to puppy training, Chapman Auto employees are proud to work with CCI as they help others live happy, independent lives.',
                    image: require('@/assets/canine-companions.jpg'),
                    alt: '3 golden retriever puppies'
                },
            ],
        };
    },
};
</script>

<style lang="scss" scoped>
@media all and (max-width:586px) {
    .banner-img {
    width: 100%;
}
}
.event {
    margin-top: 2rem;clear: both;
}
.event-name {
    margin-bottom: 1rem;
}
.body-image {
    float: left;
    margin: 0 25px 25px 0;
}
</style>
