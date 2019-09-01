---
layout: page
title: Contact
permalink: /contact/
bootstrap: true
---

<style>
    .bootstrap-iso .form-control {
        height: calc(1.5em + .75rem + 2px);
    }
    .contact-form {
        max-width: 768px;
        margin: auto;
    }
</style>

<form name="contact" class="contact-form" netlify>
    <div class="form-group">
        <label for="name">Name</label>
        <input type="text" class="form-control" id="name" name="name" placeholder="Your name">
    </div>
    <div class="form-group">
        <label for="email">Email</label>
        <input type="email" class="form-control" id="email" name="email" placeholder="Your email">
    </div>
    <div class="form-group">
        <label for="subject">Subject</label>
        <input type="text" class="form-control" id="subject" name="subject" placeholder="Message subject">
    </div>
    <div class="form-group">
        <label for="message">Message</label>
        <textarea class="form-control" id="message" name="message" rows="3" placeholder="Your message"></textarea>
    </div>
    <button type="submit" class="btn btn-primary">Send</button>
</form>