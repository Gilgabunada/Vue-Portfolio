<template>
<!-- CONTACT SECTION STARTS HERE -->
    <section id="contact" class="section page-4 d-flex flex-column justify-content-between py-4 px-3 px-lg-5">
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

                            <!-- Facebook (Bootstrap SVG Icon + Base Domain) -->
                            <a href="https://facebook.com" target="_blank" rel="noopener noreferrer" class="social-icon-btn d-flex align-items-center justify-content-center" title="Facebook">
                                <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/icons/facebook.svg" alt="Facebook" width="18" height="18" class="invert-icon">
                            </a>

                            <!-- LinkedIn (Base Domain) -->
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
                        <form class="contact-form-box p-3 p-md-4 d-flex flex-column justify-content-between h-100">
                        <div>
                            <div class="mb-2">
                                <label class="card-label text-uppercase fw-bold mb-1 small">YOUR NAME</label>
                                <input type="text" class="form-control form-control-sm custom-input" placeholder="e.g. Gil Gabunada" required>
                                </div>

                                <div class="mb-2">
                                <label class="card-label text-uppercase fw-bold mb-1 small">EMAIL OR PHONE NUMBER</label>
                                <input type="text" class="form-control form-control-sm custom-input" placeholder="e.g. alex@company.com or +1 415-000-0000" required>
                                </div>

                                <div class="mb-2">
                                <label class="card-label text-uppercase fw-bold mb-1 small">PROJECT BRIEF / MESSAGE</label>
                                <textarea class="form-control form-control-sm custom-input" rows="3" placeholder="Tell me about your product scope, timeline, and goals..."></textarea>
                            </div>
                        </div>

                            <div class="d-flex justify-content-end mt-2">
                                <button type="submit" class="btn send-btn btn-sm px-3 py-1 fw-semibold d-inline-flex align-items-center gap-2">
                                Send Message
                                    <img src="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/icons/arrow-right.svg" alt="Arrow" width="14" height="14" class="invert-icon">
                                </button>
                            </div>
                        </form>
                    </div>

                    </div>
                </div>
                <!-- Right Column: Contact Form Box ends -->
        </section>
</template>