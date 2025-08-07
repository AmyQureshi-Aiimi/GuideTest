# Theming

Customise and brand Aiimi Insight Engine with logos, background images and colour palettes within the Control Hub. Putting the control in your hands to configure and evolve Aiimi Insight Engine with your brand.

{% hint style="info" %}
To help with accessibility we prompt where text contrasts against the colour palette would not meet WCAG 2.1 AA standards.
{% endhint %}

## General

There are a number of settings to customise Aiimi Insight Engine. You can change names, contact details, and branding.

1. **Display Name** - Enter the Display Name you want to use for Aiimi Insight Engine.
   * You could change the name to match any internal naming conventions.
2. **Support Email** - Enter the Support Email to be used for support and queries.
   * There are a couple of ways users can contact admins, you can choose where they're sent.
3. **Show Support Email As A Modal** - Check this so users can see and copy the support email.
4. **Include "Powered By Aiimi Insight Engine"** - Check this to show this message within the system.&#x20;
5. **Help Centre URL** - Enter the URL users are navigated to when they select "Visit the Help Centre".

<figure><img src="../../.gitbook/assets/image (755).png" alt="" width="563"><figcaption></figcaption></figure>

### ChatBot

1. **ChatBot Name** - Enter the name that will be used for the chatbot within your system.
2. **ChatBot Description** - Enter a description for the ChatBot.

### External Search Links

External search tool links can be added so users can quickly search that tool from Aiimi Insight Engine.

1. Select Add Link to add new search tools to Aiimi Insight Engine.
2. **Link Name** - Enter the External Search Link Name to add a new search tool in Link Name.
3. **URL** - Enter the URL for the External Search Tool.&#x20;
   * This must be a valid link with a suffix of "q=".
4. Select Add.

You can edit or delete an existing search link from the external search link table.

<figure><img src="../../.gitbook/assets/image (263).png" alt="" width="375"><figcaption></figcaption></figure>

***

## Layout

{% hint style="warning" %}
We recommend testing images to ensure it contrasts well with the foreground before deploying.
{% endhint %}

### Site Logo

Choose a logo to use in the navigation bar, on the login page. You can also customise where selecting the logo will take you.  The logo will scale to fit within 150px wide by 24px high while maintaining aspect ratio.

1. Select Upload a Logo.
2. Within the modal, drag and drop the logo

Or

2. Select Upload a Logo.
3. Select Choose a file to open up your file explorer.

### Navigation

**Landing Page:** Select this to take users to their landing page when they select the logo.

**Custom Page:** Select this to take users to a different URL when they select the logo.

1. Specify where users will be taken by entering the URL into the Custom page URL.

### Landing Page Logo

The logo should be no more than 250px wide by 50px high. The image will be scaled to fit the maximum while maintaining aspect ratio. If you have a square logo which is 100px by 100px, it would be displayed as 50px by 50px on the landing page.

1. Select Upload a Logo.
2. Within the modal, drag and drop the logo

Or

2. Select Upload a Logo.
3. Select Choose a file to open up your file explorer.

### Landing Page Background

Choose the type of background and the logo to use on the Aiimi Insight Engine landing page.

**Background image -** Select this to use an image for your landing page background. It will use the Additional background Image used for the login page.

* There is an overlay placed over background images to ensure any text remains legible no matter what type of image is used. There's no way to remove the background overlay if a background image  is being used.
* The background image is set to Fill the browser window, we recommend at least 1920x1080 for HD screens.

**Background colour -** Select this to use a colour for your landing page background.

1. **Hex colour** - Enter the hex code value for the colour you want to use for the background.&#x20;
   * The text contrast check will check if this colour is accessible with our dark text.

<figure><img src="../../.gitbook/assets/image (790).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Site Message

This adds a message to the top of every users Aiimi Insight Engine. You can share important information, updates or upcoming down time.

1. Turn on a site wide messages with the Toggle at the top of the page.
2. **Site Message** - Enter the text you want to be displayed across the application.
3. **Banner Colour** - Select the colour of banner.&#x20;
   * Each colour has certain connotations in a users mind.
     1. Blue - A routine message or sharing information.
     2. Yellow - An action is required or important information.
     3. Red - Some critical information or urgent action is required.
     4. &#x20;Grey - A neutral message for information only.

#### Custom Banner Colour

1. **Hex Code -** Enter the hex code of the colour you want to use.&#x20;
   * This may be helpful if you have business standards for banners.
2. **Text Contrast Check -** This ensures that the hex code you enter passes the AA accessibility standard with the standard font colour.

<figure><img src="../../.gitbook/assets/image (869).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Colours

Customise the 3 main colours used across the system. We recommend these match your brand.&#x20;

{% hint style="warning" %}
We recommend testing colour combinations for accessibility before deploying.
{% endhint %}

1. Enter the Hex Code for each colour type.
   * **Primary** - This affects the primary buttons. We recommend using your primary brand colour.
     * Please note, the button text is white and not customisable, please make sure your chosen colour meets accessibility standards for contrast.
     * You can check the colour contrast here: [https://webaim.org/resources/contrastchecker/](https://urldefense.com/v3/__https:/webaim.org/resources/contrastchecker/__;!!L5AuLKg72A-7!5nEgqUcvwtWNJyhz9mTFhh_J9zt_zOGww30YIPR_pb4kQkFYDA46h75tu969bMqTDrTLlfcEZdJ8M-3UewI0vCw$)
   * **Secondary** - This affects a few UI elements around the application (for example, some hover states.
     * We suggest using a darker shade of your primary colour for consistency.
   * **Tertiary** - This is a legacy setting and currently does not impact the UI, so it can be left as is.
2. When you enter a colour checks will be done for the colour contrast.&#x20;
   * This will tell you if the colours are WCAG AA accessible against the white, grey and black backgrounds used.
   * We recommend a minimum accessibility level of AA. [Visit the WCAG website for more information on accessibility](https://wcag.com/).

<figure><img src="../../.gitbook/assets/image (756).png" alt=""><figcaption></figcaption></figure>

