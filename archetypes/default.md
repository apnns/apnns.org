---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: false
menu:
    main:
        weight: 3  # Edit this to order menu
type: {{ .Name | lower }}
---

