# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>JavaScript Event Handling & Interactive Elements</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 20px auto;
      padding: 10px;
    }
    button {
      padding: 10px 15px;
      margin: 5px;
      cursor: pointer;
    }
    #hoverBox {
      width: 150px;
      height: 80px;
      background: #2196f3;
      color: white;
      line-height: 80px;
      text-align: center;
      margin: 10px 0;
      border-radius: 5px;
      user-select: none;
    }
    #hoverBox.hovered {
      background: #0b7dda;
    }
    .accordion-btn {
      width: 100%;
      text-align: left;
      padding: 10px;
      border: none;
      background: #eee;
      cursor: pointer;
      margin-top: 5px;
    }
    .accordion-btn.active {
      background: #ccc;
    }
    .panel {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.3s ease;
      background: #f9f9f9;
      padding: 0 10px;
      border: 1px solid #ccc;
      border-top: none;
    }
    .panel.open {
      max-height: 100px;
      padding: 10px;
    }
    .error {
      color: red;
      font-size: 0.9em;
    }
    #formMessage {
      font-weight: bold;
      margin-top: 10px;
    }
  </style>
</head>
<body>

  <h1>JavaScript Concepts Demo</h1>

  <!-- Event Handling -->
  <section>
    <h2>Event Handling</h2>
    <button id="colorBtn">Click me to change color</button>
    <div id="hoverBox">Hover over me!</div>
    <input type="text" id="keyInput" placeholder="Type something..." />
    <p id="keyPressed">Last key pressed: None</p>
  </section>

  <!-- Interactive Elements -->
  <section>
    <h2>Interactive Elements</h2>
    <button id="toggleTextBtn">Toggle Text</button>

    <div>
      <img id="galleryImage" src="https://picsum.photos/id/1015/300/200" alt="Gallery" style="width:100%;max-width:300px;margin-top:10px;display:block;">
      <button id="prevImage">Previous</button>
      <button id="nextImage">Next</button>
    </div>

    <div>
      <button class="accordion-btn">Section 1</button>
      <div class="panel"><p>This is content for section 1.</p></div>

      <button class="accordion-btn">Section 2</button>
      <div class="panel"><p>This is content for section 2.</p></div>
    </div>
  </section>

  <!-- Form Validation -->
  <section>
    <h2>Form Validation</h2>
    <form id="signupForm" novalidate>
      <label>
        Name (required):
        <input type="text" id="name" required />
        <span class="error" id="nameError"></span>
      </label><br />
      <label>
        Email (required):
        <input type="email" id="email" required />
        <span class="error" id="emailError"></span>
      </label><br />
      <label>
        Password (min 8 chars):
        <input type="password" id="password" required minlength="8" />
        <span class="error" id="passwordError"></span>
      </label><br />
      <button type="submit">Submit</button>
    </form>
    <p id="formMessage"></p>
  </section>

  <script>
    // Event Handling
    const colorBtn = document.getElementById('colorBtn');
    colorBtn.addEventListener('click', () => {
      colorBtn.style.backgroundColor = '#' + Math.floor(Math.random() * 16777215).toString(16);
    });

    const hoverBox = document.getElementById('hoverBox');
    hoverBox.addEventListener('mouseenter', () => hoverBox.classList.add('hovered'));
    hoverBox.addEventListener('mouseleave', () => hoverBox.classList.remove('hovered'));

    const keyInput = document.getElementById('keyInput');
    const keyPressed = document.getElementById('keyPressed');
    keyInput.addEventListener('keydown', e => {
      keyPressed.textContent = 'Last key pressed: ' + e.key;
    });

    // Interactive Elements
    const toggleTextBtn = document.getElementById('toggleTextBtn');
    toggleTextBtn.addEventListener('click', () => {
      if (toggleTextBtn.textContent === 'Toggle Text') {
        toggleTextBtn.textContent = 'Text Toggled!';
        toggleTextBtn.style.backgroundColor = '#ff5722';
      } else {
        toggleTextBtn.textContent = 'Toggle Text';
        toggleTextBtn.style.backgroundColor = '';
      }
    });

    const images = [
      'https://picsum.photos/id/1015/300/200',
      'https://picsum.photos/id/1016/300/200',
      'https://picsum.photos/id/1025/300/200'
    ];
    let currentImageIndex = 0;
    const galleryImage = document.getElementById('galleryImage');
    document.getElementById('prevImage').addEventListener('click', () => {
      currentImageIndex = (currentImageIndex - 1 + images.length) % images.length;
      galleryImage.src = images[currentImageIndex];
    });
    document.getElementById('nextImage').addEventListener('click', () => {
      currentImageIndex = (currentImageIndex + 1) % images.length;
      galleryImage.src = images[currentImageIndex];
    });

    const accordionBtns = document.querySelectorAll('.accordion-btn');
    accordionBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        const panel = btn.nextElementSibling;
        const isOpen = panel.classList.contains('open');
        document.querySelectorAll('.panel').forEach(p => p.classList.remove('open'));
        document.querySelectorAll('.accordion-btn').forEach(b => b.classList.remove('active'));
        if (!isOpen) {
          panel.classList.add('open');
          btn.classList.add('active');
        }
      });
    });

    // Form Validation
    const form = document.getElementById('signupForm');
    const nameInput = document.getElementById('name');
    const emailInput = document.getElementById('email');
    const passwordInput = document.getElementById('password');

    const nameError = document.getElementById('nameError');
    const emailError = document.getElementById('emailError');
    const passwordError = document.getElementById('passwordError');
    const formMessage = document.getElementById('formMessage');

    nameInput.addEventListener('input', () => {
      nameError.textContent = nameInput.validity.valueMissing ? 'Name is required.' : '';
    });
    emailInput.addEventListener('input', () => {
      if (emailInput.validity.valueMissing) {
        emailError.textContent = 'Email is required.';
      } else if (emailInput.validity.typeMismatch) {
        emailError.textContent = 'Please enter a valid email.';
      } else {
        emailError.textContent = '';
      }
    });
    passwordInput.addEventListener('input', () => {
      if (passwordInput.validity.valueMissing) {
        passwordError.textContent = 'Password is required.';
      } else if (passwordInput.value.length < 8) {
        passwordError.textContent = 'Password must be at least 8 characters.';
      } else {
        passwordError.textContent = '';
      }
    });

    form.addEventListener('submit', e => {
      e.preventDefault();
      let valid = true;

      if (!nameInput.value.trim()) {
        nameError.textContent = 'Name is required.';
        valid = false;
      }
      if (!emailInput.value.trim()) {
        emailError.textContent = 'Email is required.';
        valid = false;
      } else if (!emailInput.checkValidity()) {
        emailError.textContent = 'Please enter a valid email.';
        valid = false;
      }
      if (!passwordInput.value) {
        passwordError.textContent = 'Password is required.';
        valid = false;
      } else if (passwordInput.value.length < 8) {
        passwordError.textContent = 'Password must be at least 8 characters.';
        valid = false;
      }

      if (valid) {
        formMessage.style.color = 'green';
        formMessage.textContent = 'Form submitted successfully!';
        form.reset();
      } else {
        formMessage.style.color = 'red';
        formMessage.textContent = 'Please fix errors and try again.';
      }
    });
  </script>

</body>
</html>
