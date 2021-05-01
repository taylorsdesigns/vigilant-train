<template>
    <div class="shift-career">
        <HeadingText>Shift Your Career Into Overdrive!</HeadingText>

        <div class="row">
            <div class="col-6">
                <p>
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum dolorem, numquam sequi in dolorum possimus voluptatum saepe reprehenderit, rem delectus laborum maiores corporis! Ut incidunt sint consequuntur tenetur neque quia?
                </p>
                <form @submit.prevent="handleSubmit">
                    <div v-for="(inputs, index) in inputs" :key="index" class="form-input">
                        <label :for="inputs.id">{{inputs.label}}</label><br>
                        <!--<input :id="inputs.id" :type="inputs.type" :name="inputs.name" :placeholder="inputs.placeholder" v-model="inputs.value" :required="required==true ? true : false">-->
                        <input :id="inputs.id" :type="inputs.type" :name="inputs.name" :placeholder="inputs.placeholder" :value="inputs.value" @input="handleSubmission" :required="required==true ? true : false">
                    </div>
                    <input type="submit" :disabled='isDisabled' value="I'm Interested!">
                </form>
            </div>
            <div class="col-6 careers-bg"></div>
        </div>
    </div>
</template>

<script>
import HeadingText from '@/components/heading-text';

export default {
    name: 'ShiftCareer',
    components: {
        HeadingText,
    },
    data() {
        return {
             inputs: [
                {
                    label: "Name (Required)",
                    id: "full_name",
                    name: 'name',
                    type: 'text',
                    placeholder: 'Full Name',
                    value: '',
                    required: true
                },
                {
                    label: "Phone Number",
                    id: "phone",
                    name: 'phone',
                    type: 'text',
                    placeholder: 'Phone Number',
                    value: ''
                },
            ],
        };
    },
    methods: {
        handleSubmit(){
            //console.log(e.target);
            this.$store.commit('insertName', 'value');
            console.log(this.$store);            
            alert("Sucess!");
            this.isDisabled(1);
        }
    },
    computed: {
        isDisabled(bool) {
            if(bool == 1) {
                return true;
            }
            else {
                return false;
            }
        }
    }
};

</script>

<style lang="scss" scoped>
label {
    font-weight: 600;
}
.row {
    display: flex;
    flex-wrap: wrap;
}
.col-6 {
    width: 100%;
    float: left;
    padding: 0 10px;
}
@media all and (min-width:586px) {
.col-6 {
    width: 50%;
}
}
.careers-bg {
    background-image: url('~@/assets/careers.jpg');
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    //transform: skew(1deg, -10deg);
}
form {
    width: 100%;
}
form * {
    width: 100%;
}
input {
    padding: 10px;
    margin: 5px 0;
}
input[type=submit] {
    background-color: var(--color-highlight);
    font-weight: 600;
    margin: 10px 0;
    border: 0;
    border-radius: 5px;
    padding: 15px;
}
.shift-career {
    float: left;
    width: 100%;
}
.form-input {
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
