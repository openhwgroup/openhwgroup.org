---
title: "Events"
date: 2019-05-04T10:00:45-04:00
hide_sidebar: true
layout: "single"
---

{{< grid/div isMarkdown="false" >}}
    <a href="/events/members" class="btn btn-primary margin-bottom-30">Events from Members</a>
{{</ grid/div>}}

{{< grid/div class="row" isMarkdown="false" >}}
{{< newsroom/events
    id="events_archive" 
    archive="true"
    publishTarget="openhwgroup"
    count="10"
    templateId="event-list-with-description"
    templatePath="js/templates/event-list-with-description.mustache"
    paginate="true" >}} 
{{</ grid/div >}}
