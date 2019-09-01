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

<form name="contact" class="contact-form needs-validation" novalidate netlify netlify-honeypot="bot-field">
    <div class="form-group">
        <label for="name">Name</label>
        <input type="text" class="form-control" id="name" name="name" placeholder="Your name" required>
        <div class="invalid-feedback">
            Please enter your name
        </div>
    </div>
    <div class="form-group">
        <label for="email">Email</label>
        <input type="email" class="form-control" id="email" name="email" placeholder="Your email" required>
        <div class="invalid-feedback">
            Please enter your email address
        </div>
    </div>
    <div class="form-group">
        <label for="subject">Subject</label>
        <input type="text" class="form-control" id="subject" name="subject" placeholder="Message subject" required>
        <div class="invalid-feedback">
            Please enter a subject
        </div>
    </div>
    <div class="form-group">
        <label for="message">Message</label>
        <textarea class="form-control" id="message" name="message" rows="3" placeholder="Your message" required></textarea>
        <div class="invalid-feedback">
            Please enter a message
        </div>
    </div>
    <button type="submit" class="btn btn-primary">Send</button>
    <p class="invisible">
        <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
    </p>
</form>

<script>
// Example starter JavaScript for disabling form submissions if there are invalid fields
(function() {
  'use strict';
  window.addEventListener('load', function() {
    // Fetch all the forms we want to apply custom Bootstrap validation styles to
    var forms = document.getElementsByClassName('needs-validation');
    // Loop over them and prevent submission
    var validation = Array.prototype.filter.call(forms, function(form) {
      form.addEventListener('submit', function(event) {
        if (form.checkValidity() === false) {
          event.preventDefault();
          event.stopPropagation();
        }
        form.classList.add('was-validated');
      }, false);
    });
  }, false);
})();
</script>
