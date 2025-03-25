<template>
    <form id="contact-form" class="text-sm" @submit.prevent="submitForm">
        <div class="flex flex-col">
            <label for="name-input" class="mb-3">_name:</label>
            <input type="text" id="name-input" v-model="formData.name" name="name" :placeholder="name" class="p-2 mb-5 placeholder-slate-600" required>
        </div>
        <div class="flex flex-col">
            <label for="email-input" class="mb-3">_email:</label>
            <input type="email" id="email-input" v-model="formData.email" name="email" :placeholder="email" class="p-2 mb-5 placeholder-slate-600" required>
        </div>
        <div class="flex flex-col">
            <label for="message-input" class="mb-3">_message:</label>
            <textarea id="message-input" v-model="formData.message" name="message" :placeholder="message" class="placeholder-slate-600" required></textarea>
        </div>
        <button id="submit-button" type="submit" class="py-2 px-4">submit-message</button>
    </form>
</template>

<script>
export default {
    name: 'ContactForm',
    props: {
        name: {
            type: String,
            required: true
        },
        email: {
            type: String,
            required: true
        },
        message: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            formData: {
                name: '',
                email: '',
                message: ''
            }
        }
    },
    methods: {
        submitForm() {
            const subject = `Portfolio Contact from ${this.formData.name}`;
            const body = `Name: ${this.formData.name}\nEmail: ${this.formData.email}\n\nMessage:\n${this.formData.message}`;
            
            // Create mailto URL
            const mailtoUrl = `mailto:sharmadishanto4@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
            
            // Open email client
            window.location.href = mailtoUrl;
            
            // Reset form
            this.formData = {
                name: '',
                email: '',
                message: ''
            };
        }
    }
}
</script>

<style>
form {
    @apply font-fira_retina text-menu-text
}
input {
    background-color: #011221;
    border: 2px solid #1E2D3D;
    border-radius: 7px;
}

/* Change Autocomplete styles in Chrome*/
input:-webkit-autofill,
input:-webkit-autofill:hover, 
input:-webkit-autofill:focus,
textarea:-webkit-autofill,
textarea:-webkit-autofill:hover,
textarea:-webkit-autofill:focus,
select:-webkit-autofill,
select:-webkit-autofill:hover,
select:-webkit-autofill:focus {
  -webkit-text-fill-color: rgb(190, 190, 190);
  transition: background-color 5000s ease-in-out 0s;
  border: 2px solid #607b96;
}

#message-input {
    background-color: #011221;
    border: 2px solid #1E2D3D;
    border-radius: 7px;
    resize: none;
    height: 150px;
    padding: 10px;
}

#submit-button {
    @apply font-fira_retina text-white text-sm;
    background-color: #1E2D3D;
    border-radius: 7px;
    margin-top: 20px;
    cursor: pointer;
}

#submit-button:hover {
    background-color: #263B50;
}

input:focus, #message-input:focus {
    outline: none;
    transition: none;
    border: 2px solid #607b96;
    box-shadow: #607b9669 0px 0px 0px 2px;
}

#contact-form {
    max-width: 370px;
    width: 100%;
}

@media (max-width: 1920px) {
    #contact-form {
        max-width: 320px;
        max-height: 400px;
    }
    #submit-button {
        font-size: 12px;
    }
    textarea {
        font-size: 13px;
        max-height: 130px !important;
    }
    input {
        font-size: 13px;
    }
}
</style>