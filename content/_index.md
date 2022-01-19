---
title: "Home"
seo_title: "OpenHW Group"
headline: "OpenHW Group"
hide_sidebar : true
hide_page_title: true
hide_breadcrumb: true
#subtitle: ""
#description: ""
tagline: "Proven processor IP"
date: 2019-03-14T15:50:25-04:00
links: [[href: "/membership/members/", text: "Members"], [href: "https://share.hsforms.com/1XdNvwOBNRTONOVdZjwVleg4o9yd", text: "Join Our Mailing List"]]
container: "container-fluid"
---

{{< grid/div id="news" class="container margin-bottom-50" isMarkdown="false">}}
    {{< grid/div class="row" isMarkdown="false">}}
        {{< news >}}
            {{< newsroom/news
                id="news_lists" 
                includeList="true"
                class="news-list"
                publishTarget="openhwgroup"
                count="3" >}}
        {{</ news >}}
        {{< events >}}
            {{< newsroom/events
                id="event-list-container" 
                containerClass="news-items clearfix"
                templateId="event-short-list"
                includeList="true"
                upcoming="1"
                class="news-items"
                publishTarget="openhwgroup"
                count="1" >}}
        {{</ events >}}
    {{</ grid/div>}}
{{</ grid/div>}}

{{< core-v-family >}}

{{< member-partner >}}

{{< testimonials >}}

{{< about-us >}}


