## 1. Structure a site using semantic HTML to aid accessibility
We have divided the section into Header, Navigation, Section, and Footer. 

```HTML
    <header id="header">
      <nav id="primary-navigaiton">
        <div id="logo">
          <p>Ghostbusters</p>
        </div>

        <!--tablet,mobile toggle nav menu button-->
        <button id="toggle-menu" aria-label="toggle-menu">
          <i class="fa fa-bars fa-3x" aria-hidden="true"></i>
        </button>
        <!--tablet,mobile toggle nav menu button ends-->

        <ul class="primary-nav-section">
          <li class="primary-nav-list">
            <a href="#about-us" class="primary-nav-link">About us</a>
          </li>
          <li class="primary-nav-list">
            <a href="#team-members" class="primary-nav-link">Team members</a>
          </li>
          <li class="primary-nav-list">
            <a href="#contact-us" class="primary-nav-link">Contact us</a>
          </li>
        </ul>
      </nav>
    </header>
 ```   


For example, in the header part, we have a navigation section for the main content using `<ul>` and `<li>`. Each `<li>` contains an `<a href>` link, so that voice recorder users will know what each item in the list represents. For tablets and mobile devices, we have added a menu button with an aria-label attribute to let users know that it is a toggle menu.

## 2. Ensure a web page is readable for screen readers
- For the toggle menu button, we have added the `aria-label` attribute to provide a clear description of the button's purpose.

   ```HTML
   <button id="toggle-menu" aria-label="Toggle menu">
     <i class="fa fa-bars fa-3x" aria-hidden="true"></i>
   </button>
  ```


- In the main jumbotron section, we have included an `alt` attribute for the main image to provide a descriptive text for screen reader users.
  ```HTML
   <div id="main-jumbotron">
     <img id="main-image" src="img/main.jpeg" alt="A haunted house in the middle of a graveyard"/>
   </div>
  ```


## 3. Ensure our UI has sufficient colour contrast so that everyone can perceive it comfortably
 We primarily use a combination of black and white as the base colors, which provides a strong contrast. Additionally, we have the color orange `#fa823f` to highlight important points and elements. By consciously selecting colors with sufficient contrast, we prioritize accessibility and ensure that our UI is visually accessible to all users, regardless of their visual abilities.

## 4. Use various tools to check that our website meets accessibility criteria
 We testd it using Lighthouse, which can be found in the Chrome developer tools. 
 
 <img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*k6LcDCcfdyeWRUTn6zKXhQ.png">

## 5. Use CSS media queries to ensure our content is always presented effectively on screens of different sizes
We have implemented a single breakpoint at 768px to cater to both tablet and phone screen sizes. When the display width reaches 768px, we apply specific styling adjustments to ensure effective presentation on screens of different sizes.

   ```CSS
    @media (max-width: 768px) {
      #main-text h1 { 
      font-size: 8vw; 
      }
      
      #team-members { 
      margin-left: 0.5rem; 
      margin-right: 0.5rem; 
      margin-top: 5rem; 
      }

      #toggle-menu { 
      border: none;
      background-color: #000000; 
      color: #ffffff; 
      display: block; 
      cursor: pointer; 
      }

      .primary-nav-section {
       display: none;
      }

      #about-us {
        height: auto;
        flex-wrap: nowrap;
        flex-direction: column;
      }

      #about-us-image {
        width: 100%;
      }

      #about-us-image > img {
        width: 40%;
      }

      #about-us-text {
        width: 100%;
      }

      #about-us-text p {
        text-align: justify;
        text-justify: inter-word;
      }

      #booking-btn {
        width: 100%;
        text-align: center;
      }
    }
  ```
 By using this media query with the specified CSS rules, we ensure that when the screen width is 768px or less, the main text heading 1 becomes 8vw, and other components are proportionally adjusted to accommodate smaller screens. This responsive design approach guarantees that our UI is visually optimized and provides an optimal user experience across various devices.
    

## 6. Demonstrate a mobile-first approach to building a website

![Alt Text](../demo.gif)

## 7. Use CSS variables to apply repeated colours to HTML elements
We didn't use global CSS variables, but I can modify your existing CSS code as follows:
```CSS
:root {
  --primary-color: #fa823f;
  --background-color: #000000;
  --text-color: #ffffff;
}

/* Rest of your existing CSS code */

body {
  background-color: var(--background-color);
  color: var(--text-color);
}

#header,
#primary-navigation,
#logo,
.primary-nav-link,
#toggle-menu,
.toggle-nav-list a,
#main-jumbotron,
#main-text h1,
#about-us-text h1,
#about-us-text p,
#booking-btn a,
#contact-us,
label,
input,
button,
textarea,
#modal,
#modal h1,
#modal p,
footer {
  color: var(--text-color);
}

```


In this updated code, I useed `:root` level, which allows me to define and reuse colors throughout your CSS code. The `--primary-color` variable represents the orange color used for various elements, and the `--background-color` and `--text-color` variables represent the black and white colors, respectively.

By using CSS variables, you can easily update and maintain consistent colors throughout your UI by modifying the variable values at the `:root` level.

## 8. Use CSS Flexbox to style children in a single-direction layout (ie a row or a column)

```css
#about-us-text {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  justify-content: center;
  padding: 1rem;
  width: 50%;
}
```
We utilized several components with the display: `flex` property to arrange items either in a row or a column. As an example, in the `'about-us'` section, we have three text contents that need to be displayed in a column rather than a row. To achieve this, we apply the `flex-direction: column` property, which arranges the child elements in a column layout.

## 9. Use CSS Grid to style children in two-direction layout

Unfortunately, in this project, we did not utilize the grid attribute. Our website has a simple and basic design, and using the `display:flex` property was sufficient to arrange the layout either in a row or column.

## 10. Ensure our Git commit history tells a coherent story

Whenever we make modifications or add new code, we create a new branch. After making the necessary changes, we include a concise and descriptive commit message. This practice enables us to easily track and revert to previous versions if needed.

## 11. Use the appropriate input types in HTML forms for gathering different types of information

* Name: The input type "text" `<input type="text">` is suitable for capturing the name.

```HTML
 <label for="name">Name</label>
 <input id="name" name="name" type="text" required/>
```

* Email: The input type "email" `<input type="email">` is appropriate for collecting email addresses.

```HTML
 <label for="email">Email</label>
 <input id="email" name="email" type="email" required/>
```

* Telephone: The input type "tel" `<input type="tel">` is used for gathering telephone numbers.
```HTML
<label for="tel">Telephone</label>
<input id="tel" name="tel" type="tel" required/>
```

* Preferred contact method: Radio buttons `<input type="radio">` are used to select the preferred contact method. Each option has a corresponding value attribute to indicate the choice.
```HTML
<fieldset>
 <legend>Preferred contact method</legend>
   <input id="contact-email"  type="radio" name="contact" value="email" checked/>
  <label for="contact-email" class="radio">Email</label>
    <input id="contact-tel" type="radio" name="contact" value="telephone"/>
  <label for="contact-tel" class="radio">Telephone</label>
    <input id="contact-post" type="radio" name="contact" value="post" />
    <label for="contact-post" class="radio">Post</label>
</fieldset>
```

* Message: The `<textarea>` element is used for capturing longer text inputs, such as messages or comments.
 ```HTML
   <label for="message">Message</label>
   <textarea name="message" id="msg" required></textarea>
```
    
* Marketing consent: A checkbox `<input type="checkbox">` is utilized to obtain consent for signing up to a weekly newsletter.
 ```HTML
  <input id="marketingConsent" name="marketingConsent" type="checkbox"/>
   <label for="marketingConsent" class="checkbox">Sign up to weekly newsletter</label>
 ```
    
* The form also includes a submit button `<button type="submit">Submit</button>` to submit the form data.
  ```HTML
   <button type="submit" id="submit">Submit</button>
  ```
