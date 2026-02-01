# Take-Home-Project - Shopify Theme App Extension – FAQ Accordion

## Project Overview
This project is a **Shopify Theme App Extension** that adds a **custom FAQ Accordion section** to Shopify Online Store themes.  
The extension allows merchants to easily add FAQ accordion blocks on pages (Homepage, Product page, etc.) and customize the accordion title and content directly from the Shopify Theme Editor.

---

## Goal
The goal of this project is to create a **Shopify Theme App Extension** that functions as a **custom FAQ Accordion section** which can be added to Shopify themes using the Theme Customizer.
- Reference:  
  https://shopify.dev/docs/apps/build/online-store/theme-app-extensions

---

## Extension Category
- **Shopify Interface Area:** Online Store  
- **App Extension Type:** Theme App Extension

---

## Tech Stack
- Shopify CLI  
- Theme App Extension  
- Liquid  
- JSON Schema  
- HTML / CSS / JavaScript :contentReference[oaicite:3]{index=3}

---

## Prerequisites
Before beginning, ensure you have the following installed or set up: :contentReference[oaicite:4]{index=4}

- **Node.js**: Version 18 or higher
- **Code Editor**: Visual Studio Code (recommended)
- **Shopify Partner Account**
- **Shopify Development Store**

---


## Setup & Installation

- Reference:
  https://shopify.dev/docs/apps/build/online-store/theme-app-extensions/build

### 1) Create a New Shopify App
Run the following command to create a new Shopify app:

```bash
npm init @shopify/app@latest
```


## 2) Generate Theme App Extension

After creating the Shopify app, generate a Theme App Extension inside the project.

Run the following command:

```bash
shopify app generate extension
```

## 3) Run the App & Preview Extension

To preview the Theme App Extension along with the rest of the Shopify app, start the development server:

```bash
shopify app dev
```

## 4) Building the Liquid Block (Creating the FAQ Accordion Block)

In this step, we create the Accordion FAQ section using a Liquid block.

### File Path
accordie-main/extensions/accordiextension/assets/accordion.liquid


### Code
```liquid
{{ 'accordie.css' | asset_url | stylesheet_tag }}

<details class="accordie-app">
    <summary>{{ block.settings.title }}</summary>
    <p>{{ block.settings.content }}</p>
</details>

{% schema %}
{
    "name": "Accordion",
    "target": "section",
    "settings": [
        { "type": "text", "id": "title", "label": "Title", "default": "Hello world" },
        { "type": "richtext", "id": "content", "label": "Content", "default": "<p>Describe here your accordion</p>" }
    ]
}
{% endschema %}
```

## 5) CSS Styling (To Look Good and Attractive)

To make the Accordion section look clean and attractive on the storefront, we add custom CSS styling.

### File Path
accordie-main/extensions/accordiextension/assets/accordie.css

We haved in our Git repo. Please go and check once.


## Testing and Implementation

After building the Theme App Extension (Liquid block + CSS), the next step is to test it inside the Shopify Theme Editor and confirm that the Accordion works correctly across different templates.

---

### Testing on Homepage

1. Open **Shopify Admin**
2. Navigate to:
   - **Online Store → Themes**
3. Click **Customize** on your active theme
4. Click **Add section**
5. Search and select **Accordion**
6. Verify:
   - Accordion section is added successfully
   - Styling is applied properly
   - Expand/collapse works smoothly

---

### Testing on Product Page

1. Open **Theme Editor**
2. From the top dropdown, switch template to:
   - **Products → Default product**
3. Click **Add section**
4. Select **Accordion**
5. Verify:
   - Accordion renders correctly on product template
   - Layout is responsive
   - Styling is consistent

---

### Customization Testing (Theme Editor Settings)

In Theme Editor, test customization by editing the Accordion settings:

- Change the **Title**  
  Example: `What if I want to refund?`

- Add **Rich Text Content**, such as:
  - Email links
  - Bold/Italic text
  - Bullet points

After saving changes, confirm:
- Updated title/content appears on storefront
- Rich text formatting works correctly

---

### Expected Output

- Accordion section should be visible on the selected page template
- Title should display from `block.settings.title`
- Content should display from `block.settings.content`
- Accordion should expand/collapse correctly using `<details>` and `<summary>`
- CSS styling should apply consistently on all pages


### Documentation

- https://drive.google.com/file/d/1B6WSQO7EtlZ-yvjTu6SzrtJKCsNAS9SD/view?usp=sharing

