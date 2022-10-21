<template>
    <div v-if="contact" class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="goToAddContact" />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from '@/components/ContactForm.vue';
import { contactService } from '@/services/contact.service';
export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: null,
            message: '',
        };
    },
    methods: {
        async goToAddContact(contact) {
            try {
                await contactService.add(contact);
                this.message = 'Liên hệ được thêm thành công.';
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>