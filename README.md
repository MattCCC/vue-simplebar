# vue-simplebar

A Simplebar (https://github.com/Grsmto/simplebar) wrapper for Vue.js.

# Usage 
Firstly import the component:
<pre>import Scrollbar from vue-simplebar</pre>

Then just wrap your content with:
<pre><code>&lt;Scrollbar&gt;your content&lt;/Scrollbar&gt;</code></pre>

# Props
I've added some extra props which can help you to manage the scrollbars appearence and position. These are:

<ul>
  <li>setTop: [String, Number, Boolean] - you can pass a number of px to scroll to a certain position. You can also pass true/false or 0 to scroll to the top</li>
  <li>recalculate: [String, Number, Boolean] - pass whatever to call a Simplebar's recalculate() method</li>
  <li>vertical: [Boolean] - whether to display a vertical scrollbar</li>
  <li>horizontal: [Boolean] - whether to display a horizontal scrollbar</li>
</ul>

# Watchers
There are two additional watchers for recalculate and setTop to make it easier to handle certain edge cases.

# Info
Scrollbar is automatically initialized and unmounted on Vue's destroy() (when the component is destroyed). Write in issues if you want something to be added to the component.
