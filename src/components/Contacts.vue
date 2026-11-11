<script setup>
    import { ref, nextTick } from 'vue';
    import axios from 'axios';
    import { Notyf } from 'notyf';
    import 'notyf/notyf.min.css';

    const notyf = new Notyf();

    const WEB3FORMS_ACCESS_KEY = '47f7afaf-d676-4e42-b432-3f6196299ace';
    const SITE_KEY = '6LcrrRouAAAAAGpm_x1-R2361MEsU_yY8cL2lEor';

    const subject = "New message from Portfolio Contact Form";
    const name = ref("");
    const email = ref("");
    const message = ref("");

    const isLoading = ref(false);
    const showRecaptchaModal = ref(false);

    const recaptchaContainer = ref(null);
    const recaptchaWidgetId = ref(null);
    const recaptchaToken = ref('');

    // Step 1: User submits the form -> Open reCAPTCHA modal
    const handleInitialSubmit = () => {
        if (!name.value || !email.value || !message.value) {
            notyf.error('Please fill in all required fields.');
            return;
        }

        showRecaptchaModal.value = true;

        nextTick(() => {
            renderRecaptcha();
        });
    };

    // Render the reCAPTCHA widget inside the modal container
    function renderRecaptcha() {
        if (!window.grecaptcha || !recaptchaContainer.value) {
            return;
        }

        if (recaptchaWidgetId.value !== null) {
            try {
                window.grecaptcha.reset(recaptchaWidgetId.value);
            } catch (e) {
                // Ignore if not rendered yet
            }
        }

        recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
            sitekey: SITE_KEY,
            size: 'normal',
            callback: onRecaptchaSuccess,
            'expired-callback': onRecaptchaExpired,
        });
    }

    // Callback when reCAPTCHA is successfully completed
    async function onRecaptchaSuccess(token) {
        recaptchaToken.value = token;
        showRecaptchaModal.value = false;
        await submitForm();
    }

    // Callback when expired
    function onRecaptchaExpired() {
        recaptchaToken.value = '';
    }

    // Step 2: Perform the actual Web3Forms submit with the token
    const submitForm = async () => {
        if (!recaptchaToken.value) {
            notyf.error('Please verify that you are not a robot.');
            return;
        }

        isLoading.value = true;

        try {
            const response = await axios.post("https://api.web3forms.com/submit", {
                access_key: WEB3FORMS_ACCESS_KEY,
                subject: subject,
                name: name.value,
                email: email.value,
                message: message.value,
                "g-recaptcha-response": recaptchaToken.value
            }, {
                headers: {
                    'Content-Type': "application/json",
                    Accept: "application/json"
                }
            });

            const result = response.data;
            if (result.success) {
                notyf.success("Your message has been sent successfully!");
                
                // Clear input areas explicitly after confirmed success
                name.value = "";
                email.value = "";
                message.value = "";
                recaptchaToken.value = "";
            } else {
                console.error("Web3Forms Error Response:", response.data);
                notyf.error(response.data.message || "Failed to send message. Please try again.");
            }

        } catch (error) {
            notyf.error(error.response?.data?.message || "An error occurred while sending your message.");
        } finally {
            isLoading.value = false;
        }
    };
</script>

<template>
<!-- CONTACT SECTION STARTS HERE -->
    <section id="contact" class="section page-4 d-flex flex-column justify-content-between py-4 px-3 px-lg-5 position-relative">
        <div class="container my-auto">
            <div class="row g-3 align-items-stretch justify-content-center">
            
                <!-- Left Column: Contact Info & Social Links starts-->
                <div class="col-12 col-lg-5 d-flex flex-column justify-content-between text-center text-lg-start">
                    <h1 class="text-white mb-4 fs-3">Contact Me</h1>
                    
                    <!-- Info List starts-->
                    <div class="d-flex flex-column gap-3 mb-3 align-items-center align-items-lg-start">
                        
                        <!-- Cellphone -->
                        <div class="d-flex align-items-center gap-2">
                            <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/icons/telephone.svg" alt="Phone" width="18" height="18" class="invert-icon flex-shrink-0">
                            <div>
                                <span class="card-label text-uppercase d-block fw-bold small">CELLPHONE NUMBER</span>
                                <p class="mb-0 fw-semibold text-white small">+1 (555) 234-8901</p>
                            </div>
                        </div>

                        <!-- Studio Address -->
                        <div class="d-flex align-items-center gap-2">
                            <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/icons/geo-alt.svg" alt="Address" width="18" height="18" class="invert-icon flex-shrink-0">
                            <div>
                                <span class="card-label text-uppercase d-block fw-bold small">STUDIO ADDRESS</span>
                                <p class="mb-0 fw-semibold text-white small">450 Mission St, San Francisco, CA 94105</p>
                            </div>
                        </div>

                        <!-- Remote Base -->
                        <div class="d-flex align-items-center gap-2">
                            <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/icons/globe.svg" alt="Remote Base" width="18" height="18" class="invert-icon flex-shrink-0">
                            <div>
                                <span class="card-label text-uppercase d-block fw-bold small">REMOTE BASE</span>
                                <p class="mb-0 fw-semibold text-white small">Available Worldwide (PST / UTC-8 timezone)</p>
                            </div>
                        </div>
                    </div>
                    <!-- Info List ends-->

                    <!-- Connect Channels Section starts-->
                    <div>
                        <span class="card-label text-uppercase d-block fw-bold mb-2 small">CONNECT CHANNELS</span>
                        <div class="d-flex flex-wrap gap-2 justify-content-center justify-content-lg-start">

                            <!-- Facebook -->
                            <a href="https://facebook.com" target="_blank" rel="noopener noreferrer" class="social-icon-btn d-flex align-items-center justify-content-center" title="Facebook">
                                <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/icons/facebook.svg" alt="Facebook" width="18" height="18" class="invert-icon">
                            </a>

                            <!-- LinkedIn -->
                            <a href="https://linkedin.com" target="_blank" rel="noopener noreferrer" class="social-icon-btn d-flex align-items-center justify-content-center" title="LinkedIn">
                                <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" alt="LinkedIn" width="18" height="18">
                            </a>

                            <!-- GitHub -->
                            <a href="https://github.com" target="_blank" rel="noopener noreferrer" class="social-icon-btn d-flex align-items-center justify-content-center" title="GitHub">
                                <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub" width="18" height="18" class="invert-icon">
                            </a>

                        </div>
                    </div>
                    <!-- Connect Channels Section ends-->
                </div>
                <!-- Left Column: Contact Info & Social Links ends-->

                <!-- Right Column: Contact Form Box starts -->
                <div class="col-12 col-lg-7">
                    <form @submit.prevent="handleInitialSubmit" class="contact-form-box p-3 p-md-4 d-flex flex-column justify-content-between h-100">
                        <div>
                            <div class="mb-2">
                                <label class="card-label text-uppercase fw-bold mb-1 small">YOUR NAME</label>
                                <input v-model="name" type="text" class="form-control form-control-sm custom-input" placeholder="e.g. Gil Gabunada" required>
                            </div>

                            <div class="mb-2">
                                <label class="card-label text-uppercase fw-bold mb-1 small">EMAIL</label>
                                <input v-model="email" type="email" class="form-control form-control-sm custom-input" placeholder="e.g. alex@company.com" required>
                            </div>

                            <div class="mb-2">
                                <label class="card-label text-uppercase fw-bold mb-1 small">PROJECT BRIEF / MESSAGE</label>
                                <textarea v-model="message" class="form-control form-control-sm custom-input" rows="3" placeholder="Tell me about your product scope, timeline, and goals..."></textarea>
                            </div>
                        </div>

                        <div class="d-flex justify-content-end mt-2">
                            <button type="submit" class="btn send-btn btn-sm px-3 py-1 fw-semibold d-inline-flex align-items-center gap-2" :disabled="isLoading">
                                {{ isLoading ? 'Sending...' : 'Send Message' }}
                            </button>
                        </div>
                    </form>
                </div>
                <!-- Right Column: Contact Form Box ends -->

            </div>
        </div>

        <!-- reCAPTCHA Popup Modal Overlay -->
        <div v-if="showRecaptchaModal" class="custom-recaptcha-overlay position-fixed top-0 start-0 w-100 h-100 d-flex                      justify-content-center align-items-center bg-dark bg-opacity-75" style="z-index: 1050;">
            <div class="bg-white p-4 rounded shadow-lg text-center position-relative" style="max-width: 400px; width: 100%;">
                <h5 class="mb-3 text-dark fw-bold">Security Verification</h5>
                <p class="text-muted small mb-3">Please verify that you are not a robot to send your message.</p>
                
                <div class="d-flex justify-content-center mb-3">
                    <div ref="recaptchaContainer"></div>
                </div>

                <button type="button" class="btn btn-secondary btn-sm w-100" @click="showRecaptchaModal = false">
                    Cancel
                </button>
            </div>
        </div>
    </section>
</template>