---
layout: post
title:  "Blog 4 - Cortex XSOAR pt. 5"
date:   2021-10-08 9:59:31 -0700
categories: jekyll update
---

![Cortex XSOAR logo](/assets/xsoar-logo.png)

# **Recap of Last Week**
Last week, we talked more about playbooks and went over an important part of writing them: conditional tasks.

This week, we'll talk about data manipulation through the use of filters and transformers. Before we talk about how to manipulate data however, we need to talk about how data is handled/stored. 

# **Context**
Data in XSOAR is stored in what is called "context data". The context is structured as a dictionary (key-values)/JSON object. 

Below is a snippet of what is placed into the context by the ThreatStream integration command, `threat-stream-analysis-report`:

```
{
    "Category": "File",
    "Duration": 68,
    "Network": [
        {
            "UdpDestination": "8.8.8.8",
            "UdpPort": 53,
            "UdpSource": "192.168.2.4"
        },
        {
            "UdpDestination": "192.168.2.4",
            "UdpPort": 65324,
            "UdpSource": "8.8.8.8"
        },
        {
            "UdpDestination": "192.168.2.4",
            "UdpPort": 54896,
            "UdpSource": "8.8.8.8"
        }
    ],
    "ReportID": "413336",
    "Started": "2019-05-30 14:05:25",
    "Verdict": "Benign"
}
```

Tasks in a playbook can then use the data in context. To access the context directly, you have to use dot notation and provide the context path. For example, if I wanted to find out the verdict of the report, I could say `Verdict.[0]`. If I wanted to find out the 2nd incident's UDP Destination IP, I'd say `Network.[1].UdpDestination`. To get the value of something in context in a playbook, you should wrap the path like this: `${Network.[1].UdpDestination}`

# **Playbooks - Filters & Transformers**

![Filter](/assets/xsoar-filter.png)<br/><font size="2.75px"><em>Filter UI</em></font>

Now let's talk about manipulating the data that was stored in context. 

You can use a filter to extract the relevant data you want. For example, if an incident has several files with varying file types and extensions, you can filter the files by file extension or file type. Then you can use those filtered files in the subsequent tasks to operate on them. Another example could be, a previous `ad-search` task returned the list of users whose passwords have expired. However, that list is particularly large. You can use a filter to divide the list in half. Then you can operate on the 2 separate lists to improve performance. See all the [Filter Operators](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/filters-and-transformers/filter-operators.html).

Transformers allow you take in a value, operate on it, and transform or render it into another value. Examples include changing 1 data type to another (like an array to string or non-Unix date to Unix date), splitting an array by a delimiter, concatenating a string, or getting a count of the number of elements in an array. See all the [Transformer Operators](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/filters-and-transformers/transformers-operators.html).

In a playbook, after adding filters/transformers on a field, you can test it out by clicking the **Test** button before save and exit the Task edit. This is incredibly useful and you should get into the habit of testing this way before you actually run the playbook. 

# **Next Week**
The next blog post will be a continuation of this one. Look forward to continue learning about XSOAR!

# **More Info**
[Cortex XSOAR](https://www.paloaltonetworks.com/cortex/cortex-xsoar)

[Cortex XSOAR Docs](https://xsoar.pan.dev/docs/concepts/getting-started-guide)

[Sub-playbook Loop](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/configure-a-sub-playbook-loop.html)

[Sub-playbook Tutorial](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/configure-a-sub-playbook-loop/sub-playbook-tutorial.html)

[Create a Conditional Task](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/5-5/cortex-xsoar-admin/playbooks/playbook-tasks/create-a-conditional-task.html)

[Filters and Transformers](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/filters-and-transformers.html)

[Create Filters and Transformers in a Playbook](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/filters-and-transformers/create-filters-and-transformers.html)