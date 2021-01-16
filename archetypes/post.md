---
{{- $date := replaceRE "(\\d{4})(\\d{2})(\\d{2})" "$1-$2-$3 00:00:00+09:00" (index (split .Name "_") 0) | time }}
{{- $title := index (split .Name "_") 1 }}
title: {{ replace $title "-" " " | title }}
summary: ""
description: ""
toc: false
date: {{ $date }}
categories: ""
tags: ["", ""]
slug: {{ $title }}
archives:
    - {{ $date.Format "2006" }}
    - {{ $date.Format "2006-01" }}
    - {{ $date.Format "2006-01-02" }}
draft: false
---

