# Apollo-Documentation-Assurant-Corporate---US-and-Global

<h1 id="overview"><strong>Overview</strong></h1>
<p>This repository contains the necessary specifications to build an event driven data layer and install GTM on your web application.</p>
<h2 id="google-tag-manager-deployment">Google Tag Manager&nbsp;</h2>
<p>Google Tag Manager (Container ID <span data-sheets-value="{&quot;1&quot;:2,&quot;2&quot;:&quot;GTM-KQFMSZR&quot;}" data-sheets-userformat="{&quot;2&quot;:4737,&quot;3&quot;:{&quot;1&quot;:0},&quot;10&quot;:1,&quot;12&quot;:0,&quot;15&quot;:&quot;Arial&quot;}">GTM-KQFMSZR) </span>has already been deployed to Assurant.com and the global properties, with the exception of the Netherlands' website. We found this site still utilizes the analytics.js and should be implemented via GTM.</p>
<h3 id="implement-the-code-snippets-in-the-of-the-sample-html-page">Data Layer</h3>
<p>Each file inside the events folder corresponds to a single use case or site event that needs to be implemented. These events are leveraged to trigger tracking rules in the tag management tool of choice and share data with the analytics reporting tool.</p>
<p>As the data layer is event-based, the order in which the events are fired is critical. In general, events should be pushed onto the data layer in the following sequence when a page load (virtual or otherwise) occurs:</p>
<p>Page Load Started &gt; <em>Other Page-level Events</em> &gt; Page Load Completed</p>
<p>If an Event is part of the page load sequence, it will be indicated in the corresponding event file.</p>
<p>Events that occur outside of the page load sequence should be pushed onto the data layer as they occur.</p>
<h2 id="questionscomments">Questions/Comments</h2>
<p>For any questions or comments, please contact nedie.recel@searchdiscovery.com.</p>