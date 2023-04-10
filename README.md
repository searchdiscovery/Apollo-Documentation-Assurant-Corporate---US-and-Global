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

## User Visit Started

*Current State:* This is not used currently on Assurant.com and the Global sites.

*When to Trigger:* Upon user's first start to the session. It should only be called once.

## Custom Events: Page Load Started and Page Load Completed

*Current State*: These events are not triggered today. This dataLayer declaration can be removed since we will be passing some of these traits in the page events.

```
bizCategory: "corporate"
gatedType: "non gated"
pageLanguage: "English"
pageType: "Home"
siteType: "brochure"
```

*When to Trigger:* The `Page Load Started` should be triggered on the initial load of the page, while the `Page Load Completed` should trigger on Window Loaded.  

We will use the Page Load Started event to send a configuration tag to Google Tag Manager, while the Page Load Completed event will send a `page_view` event to GA4. 

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

## Custom Event: Form Starts and Form Completed Events

*Current State:* 

Form Starts are triggered in Google Tag Manager using:

1. Click event when CSS selector matches `form *,#subscribe-form-btn` - If this selector is not used universally across Assurant sites, it can undercount the total form starts. 

Form submissions are triggered in two ways:

1. Custom dataLayer event called `e_formSubmit`
2. Using Google Tag Manager's built in Form Submission trigger

*Future State: Assurant should migrate from the CSS selectors on form starts and `e_formSubmit` or the built-in triggers on completions to these events:*
1. [Form Started](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Form%20Started.md#javascript-coded): This can be triggered on first interaction with the form. 
2. [Form Submission Succeeded](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Form%20Submission%20Succeeded.md#javascript-code): This should be triggered only when the form is successfully submitted. 

## Custom Event: Downloads

*Current State*: To trigger successful downloads, Google Tag Manager triggers a download event using:

1. Click event when CSS selector matches RegEx `(.*pdf*|.*jpg*)` - This should work universally, but we recommend moving to a dataLayer event to keep these events consistent with the other dataLayer events.

*Future State:* Use the [Download Clicked Events](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Download%20Link%20Clicked.md#javascript-code). We will remove the CSS trigger in GTM.

## Custom Event: Video Plays and Completions

*Current State:* Video Starts are triggered in GTM with a CSS selector `layout-video-overlay-template` and completions use a built-in GTM trigger.

*Future State*: [Video Starts](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Video%20Started.md#video-started) should be triggered on the initial video play and [Video Completions](https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Video%20Completed.md#video-completed) when the full video is watched.

<h2 id="questionscomments">Questions/Comments</h2>
<p>For any questions or comments, please contact nedie.recel@searchdiscovery.com and alyssa.cuson@searchdiscovery.com.</p>
