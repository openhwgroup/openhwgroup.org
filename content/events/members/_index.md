---
title: "Members"
date: 2022-02-04T10:00:45-04:00
hide_sidebar: true
layout: "single"
---

{{< grid/div isMarkdown="false">}}
  <p class="margin-0">Are you attending an event you want the OpenHW community to know about?</p>
  <p><a href="https://newsroom.eclipse.org/node/add/events" target="_blank">Submit your event</a> details, and indicate that there is a "Member organization participating", to appear on this page.</p>
{{</ grid/div >}}

{{< newsroom/events
    id="events_archive" 
    archive="true"
    publishTarget="openhwgroup&parameters[ef_participation][]=member_org_participating"
    count="10"
    templateId="event-list-with-description"
    templatePath="js/templates/event-list-with-description.mustache"
    paginate="true" >}}