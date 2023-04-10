# Apollo-Documentation-Assurant-Corporate---US-and-Global

<h1 id="user-content-overview" dir="auto"><strong>Overview</strong></h1>
<p dir="auto">This repository contains the necessary specifications to build an event driven data layer and install GTM on your web application.</p>
<h2 id="user-content-google-tag-manager-deployment" dir="auto"><a id="user-content-google-tag-manager" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#google-tag-manager" aria-hidden="true"></a>Google Tag Manager&nbsp;</h2>
<p dir="auto">Google Tag Manager (Container ID&nbsp;GTM-KQFMSZR)&nbsp;has already been deployed to Assurant.com and the global properties, with the exception of the Netherlands' website. We found this site still utilizes analytics.js and should be implemented via GTM.</p>
<h3 id="user-content-implement-the-code-snippets-in-the-of-the-sample-html-page" dir="auto"><a id="user-content-data-layer" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#data-layer" aria-hidden="true"></a>Data Layer</h3>
<p dir="auto">Each file inside the events folder corresponds to a single use case or site event that needs to be implemented. These events are leveraged to trigger tracking rules in the tag management tool of choice and share data with the analytics reporting tool.</p>
<p dir="auto">As the data layer is event-based, the order in which the events are fired is critical. In general, events should be pushed onto the data layer in the following sequence when a page load (virtual or otherwise) occurs:</p>
<p dir="auto">Page Load Started &gt;&nbsp;<em>Other Page-level Events</em>&nbsp;&gt; Page Load Completed</p>
<p dir="auto">If an Event is part of the page load sequence, it will be indicated in the corresponding event file.</p>
<p dir="auto">Events that occur outside of the page load sequence should be pushed onto the data layer as they occur.</p>
<h2 dir="auto" data-sourcepos="12:1-12:21"><a id="user-content-user-visit-started" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#user-visit-started" aria-hidden="true"></a>User Visit Started</h2>
<p dir="auto" data-sourcepos="14:1-14:81"><em>Current State:</em>&nbsp;This is not used currently on Assurant.com and the Global sites.</p>
<p dir="auto" data-sourcepos="16:1-16:89"><em>When to Trigger:</em>&nbsp;Upon user's first start to the session. It should only be called once.</p>
<h2 dir="auto" data-sourcepos="18:1-18:59"><a id="user-content-custom-events-page-load-started-and-page-load-completed" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#custom-events-page-load-started-and-page-load-completed" aria-hidden="true"></a>Custom Events: Page Load Started and Page Load Completed</h2>
<p dir="auto" data-sourcepos="20:1-20:162"><em>Current State</em>: These events are not triggered today. This dataLayer declaration can be removed since we will be passing some of these traits in the page events.</p>
<div class="snippet-clipboard-content notranslate position-relative overflow-auto">
<pre class="notranslate"><code>bizCategory: "corporate"
gatedType: "non gated"
pageLanguage: "English"
pageType: "Home"
siteType: "brochure"

</code></pre>
</div>
<p dir="auto" data-sourcepos="30:1-30:162"><em>When to Trigger:</em>&nbsp;The&nbsp;<code>Page Load Started</code>&nbsp;should be triggered on the initial load of the page, while the&nbsp;<code>Page Load Completed</code>&nbsp;should trigger on Window Loaded.</p>
<p dir="auto" data-sourcepos="32:1-32:212">We will use the Page Load Started event to send a configuration tag to Google Tag Manager, while the Page Load Completed event will send a&nbsp;<code>page_view</code>&nbsp;event to GA4. We recommend setting the traits in both events.</p>
<p dir="auto" data-sourcepos="34:1-34:54">The Current and New Variable Names are included below:</p>
<table data-sourcepos="36:1-45:62">
<thead>
<tr data-sourcepos="36:1-36:66">
<th data-sourcepos="36:2-36:25">Current Variable Names</th>
<th data-sourcepos="36:27-36:43">Sample Value(s)</th>
<th data-sourcepos="36:45-36:64">New Variable Names</th>
</tr>
</thead>
<tbody>
<tr data-sourcepos="38:1-38:33">
<td data-sourcepos="38:2-38:14">bizCategory</td>
<td data-sourcepos="38:16-38:26">corporate</td>
<td data-sourcepos="38:28-38:32">TBD</td>
</tr>
<tr data-sourcepos="39:1-39:43">
<td data-sourcepos="39:2-39:12">gatedType</td>
<td data-sourcepos="39:14-39:23">nonGated</td>
<td data-sourcepos="39:25-39:41">Page Experience</td>
</tr>
<tr data-sourcepos="40:1-40:43">
<td data-sourcepos="40:2-40:15">pageLanguage</td>
<td data-sourcepos="40:17-40:25">English</td>
<td data-sourcepos="40:27-40:41">Page Language</td>
</tr>
<tr data-sourcepos="41:1-41:76">
<td data-sourcepos="41:2-41:11">pageType</td>
<td data-sourcepos="41:13-41:59">Lender-Placed Insurance, Manufactured Housing</td>
<td data-sourcepos="41:61-41:74">Site Section</td>
</tr>
<tr data-sourcepos="42:1-42:30">
<td data-sourcepos="42:2-42:11">siteType</td>
<td data-sourcepos="42:13-42:22">brochure</td>
<td data-sourcepos="42:24-42:28">TBD</td>
</tr>
<tr data-sourcepos="43:1-43:39">
<td data-sourcepos="43:2-43:14">contentName</td>
<td data-sourcepos="43:16-43:25">Overview</td>
<td data-sourcepos="43:27-43:37">Page Name</td>
</tr>
<tr data-sourcepos="44:1-44:53">
<td data-sourcepos="44:2-44:19">line_of_business</td>
<td data-sourcepos="44:21-44:25">MFH</td>
<td data-sourcepos="44:27-44:52">Product Category Level 1</td>
</tr>
<tr data-sourcepos="45:1-45:62">
<td data-sourcepos="45:2-45:14">Subcategory</td>
<td data-sourcepos="45:16-45:34">Deposit Solutions</td>
<td data-sourcepos="45:36-45:61">Product Category Level 2</td>
</tr>
</tbody>
</table>
<h2 dir="auto" data-sourcepos="47:1-47:54"><a id="user-content-custom-event-form-starts-and-form-completed-events" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#custom-event-form-starts-and-form-completed-events" aria-hidden="true"></a>Custom Event: Form Starts and Form Completed Events</h2>
<p dir="auto" data-sourcepos="49:1-49:17"><em>Current State:</em></p>
<p dir="auto" data-sourcepos="51:1-51:54">Form Starts are triggered in Google Tag Manager using:</p>
<ol dir="auto" data-sourcepos="53:1-54:0">
<li data-sourcepos="53:1-54:0">Click event when CSS selector matches&nbsp;<code>form *,#subscribe-form-btn</code>&nbsp;- If this selector is not used universally across Assurant sites, it can undercount the total form starts.</li>
</ol>
<p dir="auto" data-sourcepos="55:1-55:43">Form submissions are triggered in two ways:</p>
<ol dir="auto" data-sourcepos="57:1-59:0">
<li data-sourcepos="57:1-57:47">Custom dataLayer event called&nbsp;<code>e_formSubmit</code></li>
<li data-sourcepos="58:1-59:0">Using Google Tag Manager's built in Form Submission trigger</li>
</ol>
<p dir="auto" data-sourcepos="60:1-60:153"><em>Future State: Assurant should migrate from the CSS selectors on form starts and&nbsp;<code>e_formSubmit</code>&nbsp;or the built-in triggers on completions to these events:</em></p>
<ol dir="auto" data-sourcepos="61:1-63:0">
<li data-sourcepos="61:1-61:236"><a href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Form%20Started.md#javascript-coded">Form Started</a>: This can be triggered on first interaction with the form.</li>
<li data-sourcepos="62:1-63:0"><a href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Form%20Submission%20Succeeded.md#javascript-code">Form Submission Succeeded</a>: This should be triggered only when the form is successfully submitted.</li>
</ol>
<h2 dir="auto" data-sourcepos="64:1-64:26"><a id="user-content-custom-event-downloads" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#custom-event-downloads" aria-hidden="true"></a>Custom Event: Downloads</h2>
<p dir="auto" data-sourcepos="66:1-66:101"><em>Current State</em>: To trigger successful downloads, Google Tag Manager triggers a download event using:</p>
<ol dir="auto" data-sourcepos="68:1-69:0">
<li data-sourcepos="68:1-69:0">Click event when CSS selector matches RegEx&nbsp;<code>(.*pdf*|.*jpg*)</code>&nbsp;- This should work universally, but we recommend moving to a dataLayer event to keep these events consistent with the other dataLayer events.</li>
</ol>
<p dir="auto" data-sourcepos="70:1-70:258"><em>Future State:</em>&nbsp;Use the&nbsp;<a href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Download%20Link%20Clicked.md#javascript-code">Download Clicked Events</a>. We will remove the CSS trigger in GTM.</p>
<h2 dir="auto" data-sourcepos="72:1-72:44"><a id="user-content-custom-event-video-plays-and-completions" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#custom-event-video-plays-and-completions" aria-hidden="true"></a>Custom Event: Video Plays and Completions</h2>
<p dir="auto" data-sourcepos="74:1-74:146"><em>Current State:</em>&nbsp;Video Starts are triggered in GTM with a CSS selector&nbsp;<code>layout-video-overlay-template</code>&nbsp;and completions use a built-in GTM trigger.</p>
<p dir="auto" data-sourcepos="76:1-76:450"><em>Future State</em>:&nbsp;<a href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Video%20Started.md#video-started">Video Starts</a>&nbsp;should be triggered on the initial video play and&nbsp;<a href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/blob/main/Data%20Layer%20Events/Video%20Completed.md#video-completed">Video Completions</a>&nbsp;when the full video is watched.</p>
<h2 id="user-content-questionscomments" dir="auto"><a id="user-content-questionscomments" class="anchor" href="https://github.com/searchdiscovery/Apollo-Documentation-Assurant-Corporate---US-and-Global/edit/main/README.md#questionscomments" aria-hidden="true"></a>Questions/Comments</h2>
<p dir="auto">For any questions or comments, please contact nedie.recel@searchdiscovery.com and alyssa.cuson@searchdiscovery.com.</p>
