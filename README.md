<h1 id="overview"><strong>Overview</strong></h1>
<p>This repository contains the necessary specifications to build an event driven data layer and install GTM on your web application.</p>
<h2 id="google-tag-manager-deployment">Google Tag Manager&nbsp;</h2>
<p>Google Tag Manager (Container ID <span data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;GTM-KQFMSZR&quot;}" data-sheets-userformat="{&quot;2&quot;:4737,&quot;3&quot;:{&quot;1&quot;:0},&quot;10&quot;:1,&quot;12&quot;:0,&quot;15&quot;:&quot;Arial&quot;}">GTM-KQFMSZR) </span>has already been deployed to Assurant.com and the global properties, with the exception of the Netherlands' website. We found this site still utilizes analytics.js and should be implemented via GTM.</p>
<h3 id="implement-the-code-snippets-in-the-of-the-sample-html-page">Data Layer</h3>
<p>Each file inside the events folder corresponds to a single use case or site event that needs to be implemented. These events are leveraged to trigger tracking rules in the tag management tool of choice and share data with the analytics reporting tool.</p>
<p>As the data layer is event-based, the order in which the events are fired is critical. In general, events should be pushed onto the data layer in the following sequence when a page load (virtual or otherwise) occurs:</p>
<p>Page Load Started &gt; <em>Other Page-level Events</em> &gt; Page Load Completed</p>
<p>If an Event is part of the page load sequence, it will be indicated in the corresponding event file.</p>
<p>Events that occur outside of the page load sequence should be pushed onto the data layer as they occur.</p>
<h2 id="april-2023-changes">Highlights of April 2023 Changes</h2>

### Custom Events: Page Load Started and Page Load Completed

Currently, a dataLayer event initializes with the page and includes several page traits. We recommend sending these traits with `Page Load Started` and `Page Load Completed` events. We will use the Page Load Started event to send a configuration tag to Google Tag Manager, while the Page Load Completed event will send a `page_view` event to GA4. 

The Current and New Variable Names are included below:

| Current Variable Names | Sample Value(s) | New Variable Names | 
| ------------- | ------------- | ------------- |
| bizCategory | corporate | TBD |
| gatedType | nonGated | Page Experience | 
| pageLanguage | English | Page Language | 
| pageType | Lender-Placed Insurance, Manufactured Housing | Site Section | 
| siteType | brochure | TBD | 
| contentName | Overview | Page Name | 
| line_of_business | MFH | Product Category Level 1 |
| Subcategory | Deposit Solutions | Product Category Level 2 |

### Custom Event: Form Starts and Form Completed Events
Form Starts are triggered in Google Tag Manager using:

1. Click event when CSS selector matches `form *,#subscribe-form-btn` - If this selector is not used universally across Assurant sites, it can undercount the total form starts. 

Form submissions are triggered in two ways:

1. Custom dataLayer event called `e_formSubmit`
2. Using Google Tag Manager's built in Form Submission trigger

Search Discovery created two new dataLayer events that should be triggered for form starts and submissions to the new [Form Started](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Form%20Started.md#javascript-coded) and [Form Submission Succeeded](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Form%20Submission%20Succeeded.md#javascript-code)

### Custom Event: Downloads
Currently to trigger successful downloads, Google Tag Manager triggers a download event using:

1. Click event when CSS selector matches RegEx `(.*pdf*|.*jpg*)` - This should work universally, but we recommend moving to a dataLayer event to keep these events consistent with the other dataLayer events.

Search Discovery created a new dataLayer event to track [Download Clicked Events](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Download%20Link%20Clicked.md#javascript-code).

<h2 id="questionscomments">Questions/Comments</h2>
<p>For any questions or comments, please contact nedie.recel@searchdiscovery.com and alyssa.cuson@searchdiscovery.com.</p>
