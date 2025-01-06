---
title: "Home"
seo_title: "OpenHW Group"
headline: "OpenHW Foundation"
subtitle: "The leading global community for <br> Industrial Grade, Open Source RISC-V CPU development and Innovation"
hide_sidebar : true
hide_page_title: true
hide_breadcrumb: true
header_wrapper_class: "bg-home"
date: 2019-03-14T15:50:25-04:00
links: [[href: "/about/", text: "Members"], [href: "/become-a-member/", text: "Join Us"]]
show_featured_story: true
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
        {{< grid/div class="col-sm-8 col-sm-offset-1 news-list" isMarkdown="false" >}}
            {{< events >}}
                <h2 class="header-underline margin-bottom-30">Events</h2>
                {{< pinned_news disabled="true" >}}
                {{< newsroom/events
                  id="event-list-container" 
                  containerClass="news-items clearfix"
                  templateId="event-short-list"
                  templatePath="/js/templates/event-list-format.mustache"
                  upcoming="1"
                  class="news-items"
                  publishTarget="openhwgroup"
                  count="3" >}}
            {{</ events >}}
        {{</ grid/div>}}
    {{</ grid/div>}}
{{</ grid/div>}}

{{< core-v-family >}}

{{< member-partner >}}

{{< testimonials >}}

{{< about-us >}}

{{< contact-us >}}
