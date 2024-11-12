<template>
    <div class="site__body my-5">

        <div class="container-fluid full-background">
        </div>

        <div class="block-header block-header--has-breadcrumb block-header--has-title">
            <div class="container">
                <div class="block-header__body">
                    <h1 class="block-header__title">Contact Us</h1>
                </div>
            </div>
        </div>
        <div class="block">
            <div class="container container--max--lg">
                <div class="card" style="padding: 0px 24px;">
                    <div class="card-body card-body--padding--2">
                        <div class="row">
                            <div class="col-12 col-lg-6 pb-4 pb-lg-0">
                                <div class="mr-1">
                                    <h4 class="contact-us__header card-title my-3" style="font-size: 28px;">Our Address
                                    </h4>
                                    <div class="contact-us__address my-4">
                                        <p class="" style="font-size: 18px;">
                                            N.H. 47 Choudhary Market Tejaji Nagar Khandwa Road Indore (M.P)<br />
                                            Email: red info@example.com<br />
                                            Phone Number: +91 94253, 11328
                                        </p>
                                        <p class="" style="font-size: 18px;">
                                            <strong class="" style="font-size: 18px;">Opening Hours</strong><br />
                                            Monday to Friday: 8am-8pm<br />
                                            Saturday: 8am-6pm<br />
                                            Sunday: 10am-4pm
                                        </p>
                                        <p class="" style="font-size: 18px;">
                                            <strong class="" style="font-size: 18px;">Comment</strong><br />
                                            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur suscipit
                                            suscipit
                                            mi, non tempor nulla finibus eget. Lorem ipsum dolor sit amet, consectetur
                                            adipiscing
                                            elit.
                                        </p>
                                    </div>
                                </div>
                            </div>
                            <div class="col-12 col-lg-6">
                                <div class="ml-1">
                                    <h4 class="contact-us__header card-title my-3" style="font-size: 28px;">Leave us a
                                        Message</h4>
                                    <form>
                                        <div class="form-row ">
                                            <div class="form-group col-md-6">
                                                <label for="form-name" style="font-size: 18px;">Your Name</label>
                                                <input type="text" id="form-name"
                                                    style="background-color: #EBEBEB; font-size: 18px;"
                                                    class="form-control" placeholder="Your Name" required />
                                            </div>
                                            <div class="form-group col-md-6">
                                                <label for="form-email" style="font-size: 18px;">Email</label>
                                                <input type="email" id="form-email"
                                                    style="background-color: #EBEBEB; font-size: 18px;"
                                                    class="form-control" placeholder="Email Address" required />
                                            </div>
                                        </div>
                                        <div class="form-group">
                                            <label for="form-subject" style="font-size: 18px;">Subject</label>
                                            <input type="text" id="form-subject"
                                                style="background-color: #EBEBEB; font-size: 18px;" class="form-control"
                                                placeholder="Subject" required />
                                        </div>
                                        <div class="form-group">
                                            <label for="form-message" style="font-size: 18px;">Message</label>
                                            <textarea id="form-message"
                                                style="background-color: #EBEBEB; font-size: 18px;" class="form-control"
                                                rows="4" required></textarea>
                                        </div>
                                        <button type="submit" class="btn btn-primary mt-3 px-3"
                                            style="font-weight: 600; font-size: 18px; background-color: #E52727; border-color: #E52727;">Send
                                            Message</button>
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="block-space block-space--layout--before-footer"></div>
    </div>
</template>

<style>
.full-background {
    background-image: url('/images/contact-image.jpeg');
    /* Replace with your image URL */
    background-size: cover;
    /* Ensure the image covers the entire container */
    background-position: center;
    /* Center the image */
    background-repeat: no-repeat;
    /* Prevent the background from repeating */
    height: 100vh;
    /* Full viewport height */
    width: 100vw;
    /* Full viewport width */
    position: relative;
    /* Maintain positioning */
}



.site__body {
    background-color: #f8f9fa;
    /* Light background color */
}

.card {
    border-radius: 0.5rem;
    /* Rounded corners for the card */
}

.card-title {
    font-weight: bold;
    /* Bold title */
}

.contact-us__header {
    margin-bottom: 1rem;
    /* Margin below the header */
}

.btn-danger {
    background-color: #E52727;
    /* Red button */
    border: none;
    /* Remove border */
}

.btn-danger:hover {
    background-color: #333333;
    /* Darker red on hover */
}

.block-map {
    margin-bottom: 2rem;
    /* Spacing below the map */
}

.block-header__title {
    font-size: 2rem;
    /* Title size */
    font-weight: bold;
    /* Bold title */
}













@media (-webkit-max-device-pixel-ratio: 1),
(max-resolution: 1dppx) {
    .footer-contacts__title {
        font-weight: 400;
    }
}

.footer-contacts__text {
    line-height: 22px;
    list-style: none;
    margin: 0;
    font-size: 15px;
}

.footer-contacts__text a {
    color: inherit;
}

.footer-contacts__contacts {
    font-size: 14px;
    line-height: 20px;
    list-style: none;
    padding: 0;
    display: -ms-flexbox;
    display: flex;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
}

.footer-contacts__contacts a {
    color: inherit;
}

.footer-contacts__contacts dt {
    font-size: 12px;
    font-weight: 400;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    margin-bottom: 2px;
}

.footer-contacts__contacts dd {
    color: #fff;
    margin: 0;
    font-weight: 500;
}

@media (-webkit-max-device-pixel-ratio: 1),
(max-resolution: 1dppx) {
    .footer-contacts__contacts dd {
        font-weight: 400;
    }
}

.footer-contacts__icon {
    display: inline-block;
    text-align: center;
    width: 22px;
    margin-right: 2px;
}

@media (min-width: 1400px) {
    .footer-contacts {
        padding-right: 36px;
    }
}

@media (min-width: 1200px) {
    .footer-contacts__contacts {
        margin: 24px -15px 0;
    }

    .footer-contacts__contacts dl {
        width: calc(100% / 2 - 30px - 1px);
        margin: 0 15px;
    }

    .footer-contacts__contacts dl:nth-child(n + 3) {
        margin-top: 18px;
    }
}

@media (max-width: 1199.98px) {
    .footer-contacts__contacts {
        margin: -6px;
    }

    .footer-contacts__contacts dl {
        width: calc(100% / 4 - 12px);
        margin: 6px;
    }

    .footer-contacts {
        text-align: center;
        margin-bottom: 42px;
    }

    .footer-contacts__title {
        font-size: 24px;
        margin-bottom: 12px;
    }

    .footer-contacts__contacts {
        padding-top: 28px;
    }

    .footer-contacts__contacts dl {
        background: hsla(0, 0%, 100%, 0.05);
        padding: 16px 12px;
        border-radius: 3px;
        display: -ms-flexbox;
        display: flex;
        -ms-flex-direction: column;
        flex-direction: column;
        -ms-flex-pack: center;
        justify-content: center;
    }
}

@media (max-width: 991.98px) {
    .footer-contacts__contacts {
        margin: -6px;
    }

    .footer-contacts__contacts dl {
        width: calc(100% / 2 - 12px);
        margin: 6px;
        padding: 20px 16px;
    }
}

@media (max-width: 767.98px) {
    .footer-contacts__contacts dl {
        padding: 16px;
    }
}

@media (max-width: 479px) {
    .footer-contacts__contacts {
        margin: -4px;
    }

    .footer-contacts__contacts dl {
        width: calc(100% / 1 - 8px);
        margin: 4px;
    }
}

.contacts__map {
    position: relative;
    height: 400px;
}

.contacts__map iframe {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
}

@media (max-width: 991.98px) {
    .contacts__map {
        height: 380px;
    }
}

@media (max-width: 767.98px) {
    .contacts__map {
        height: 360px;
    }
}
</style>
