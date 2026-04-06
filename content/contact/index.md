---
title: "Contact"
type: "page"
# Standard PaperMod parameters
---

![Collaborate and Inquire](engineering-contact.png)

{{< rawhtml >}}
<style>
  /* Base input field styling */
  .formspree-input, .formspree-textarea {
    margin-bottom: 15px;
    width: 100%;
    max-width: 400px;
    padding: 10px;
    
    /* Dark background matching the image style */
    background-color: #2a2b2e; 
    
    /* Off-white text for readability */
    color: #f8f9fa; 
    
    /* Subtle cyan border, inspired by the glowing lines in the image */
    border: 2px solid #00bcd4; 
    
    border-radius: 4px;
    
    /* Smooth transition for interaction */
    transition: border-color 0.2s, box-shadow 0.2s;
  }

  /* Interaction styling: change border and add glow on focus (selection) */
  .formspree-input:focus, .formspree-textarea:focus {
    outline: none;
    border-color: #f8f9fa; /* Focus to white text color */
    
    /* Cyan glow effect */
    box-shadow: 0 0 8px rgba(0, 188, 212, 0.6); 
  }
</style>

<form action="https://formspree.io/f/xjgpjjbk" method="POST">
  <label for="email">Email address:</label><br>
  <input type="email" id="email" name="email" placeholder="your.email@example.com" required class="formspree-input">
  <br>
  <label for="message">Message:</label><br>
  <textarea id="message" name="message" rows="5" placeholder="How can I help you?" required class="formspree-textarea"></textarea>
  <br>
  <input type="hidden" name="_next" value="https://endofwave.github.io/engineering-tools/success/">
  <button type="submit" style="padding: 10px 20px; cursor: pointer; border-radius: 4px; background-color: #007bff; color: white; border: none; font-weight: bold;">Send Message</button>
</form>
{{< /rawhtml >}}