---
categories: basics
layout: article
title: Collaboration-Focused UI
---

<p>In Algorithmia version 21.2, we've updated our platform with a number of user interface (UI) improvements to support an organizational, collaborative approach to algorithm development and management. It's now easier for teams to work together to deliver MLOps functionality in a shared workspace, while individual users can still utilize their personal workspace as an isolated, "sandbox" environment in order to keep the production environment uncluttered.</p>
<h2>Navigation improvements</h2>
<p>We've relocated resource creation, viewing, and management functionality in an effort to clarify who the owner of a resource is when it's created and at the point it's accessed. In the redesigned interface, you'll now see links in the left-hand navigation menu to navigate directly to workspaces associated with any organizations to which you belong, as well as to your personal workspace. Each resource is scoped within a specific workspace, and in the UI you'll only be able to interact with it from within that workspace.</p>
<h3>Organization workspaces</h3>
<p>Resources (i.e., <strong>Algorithms</strong>, <strong>Data</strong>, and <strong>API keys</strong>) owned by each organization are now visible in that organization's workspace, along with other organization-related tabs that were previously on an organization's profile (i.e., <strong style="font-family: inherit; font-size: 1em;">Reporting</strong><span style="font-family: inherit; font-size: 1em;">, </span><strong style="font-family: inherit; font-size: 1em;">Errors</strong><span style="font-family: inherit; font-size: 1em;">, </span><strong style="font-family: inherit; font-size: 1em;">Members</strong><span style="font-family: inherit; font-size: 1em;">, and </span><strong style="font-family: inherit; font-size: 1em;">Invites</strong><span style="font-family: inherit; font-size: 1em;">). Finally, the organization-level settings previously available through the </span><strong style="font-family: inherit; font-size: 1em;">Edit Organization</strong><span style="font-family: inherit; font-size: 1em;"> button have been moved to a designated </span><strong style="font-family: inherit; font-size: 1em;">Settings</strong><span style="font-family: inherit; font-size: 1em;"> tab.</span></p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091205305.png)

<h3>Personal workspace</h3>
<p>Analogously, resources owned by individuals are now visible under the individual account's <strong>Personal Workspace</strong> on the left-hand navigation bar.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091274591.png)

<p>Not only is it now easier to switch between workspaces, we've also updated the workspace landing pages to display the algorithms you've modified most recently so that it's easier to quickly find them and get back to work.</p>
<h2>Org-owned shared resources</h2>
<p>In this org-first version of Algorithmia, only cluster admins can create organizations.</p>
<p>Furthermore, in addition to algorithms, you can now assign data sources and API keys to be owned by, and automatically shared within, an organization. Org members are automatically granted access to these shared resources, enabling your team to more closely collaborate on algorithm development. Additionally, using org-owned resources, you no longer need to worry about a critical component of a project becoming unavailable or requiring modification when an org member transfers out of the team or leaves the company.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1627948450822.png)

<h3>Org-owned algorithms</h3>
<p>As before, you can create an algorithm under the ownership of an org to enable shared algorithm access between all members of the org. Because there are no longer global resource-creation buttons, to create an algorithm you must navigate to a specific workspace and click the&nbsp;<strong>New algorithm</strong> button. In the algorithm-creation form, the <strong>Owner</strong> field will be pre-populated with the name of the org under which you're creating the algorithm. If you'd like to create an algorithm under the ownership of your individual account, you still can; just navigate to your personal workspace and create the algorithm there.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091096402.png)

<h3>Org-owned data sources</h3>
<p>In the updated UI, all data sources can now be created under the ownership of a specific org or your individual account. This includes data connectors, which could not previously be shared between members of an org.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628008092400.png)

<p>As before, you can also create org-owned data collections to share hosted data between org members.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628008185277.png)

<h3>Org-owned API keys</h3>
<p>In the updated UI, standard (non-admin) API keys can now be created under the ownership of a specific org instead of just an individual account. Org-owned API keys have access to all resources owned by the org.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091378863.png)

<p>To create a new org-owned API key, navigate to the workspace of the org that you'd like to be the key owner and click the <strong>New API key</strong> button under the&nbsp;<strong>API Keys</strong> tab. When you create the key, you'll "assign" it either to the org or to an individual org member account. Algorithmia logs which API key is used for each authenticated resource request, thereby facilitating auditability at the individual user account level while still providing for shared access to resources between multiple individuals.</p>
<p>Note that as a best practice, we recommend assigning all API keys to individual accounts for auditability and usage reporting purposes. However, there may be cases where it's desirable to assign an org-owned API key to the org itself, so that you can make a key available to all members, so this option is available as well.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091438177.png)

<p>As in the previous UI, we recommend you provide a <strong>Label</strong> for your key so that it's easily distinguishable from others that you've created and its purpose is clear. The remaining key-creation fields have not changed&mdash;you can still control key access on a per-algorithm basis if desired, and you can limit the key's data-access permissions as well.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091731532.png)

<p>User account-owned API keys can still be created by clicking the <strong>New API key</strong> dropdown in the <strong>API Keys</strong> tab in your personal workspace. If you have cluster admin permissions, you'll also be able to create an admin API key through this dropdown as well.</p>

![]({{site.url}}/developers/images/post_images/platform/org-first-1628091826008.png)
