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


In this updated code, I useed :root level, which allows me to define and reuse colors throughout your CSS code. The --primary-color variable represents the orange color used for various elements, and the --background-color and --text-color variables represent the black and white colors, respectively.

By using CSS variables, you can easily update and maintain consistent colors throughout your UI by modifying the variable values at the :root level.
## 8. Use CSS Flexbox to style children in a single-direction layout (ie a row or a column)

## 9. Use CSS Grid to style children in two-direction layout

## 10. Ensure our Git commit history tells a coherent story

## 11. Use the appropriate input types in HTML forms for gathering different types of information
