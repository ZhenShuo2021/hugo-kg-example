---
title: Examples
description: Get inspiration from agent examples
keywords: [ai, agent, cagent]
weight: 40
---

Get inspiration from the following agent examples.
See more examples in the [Docker Agent GitHub repository](https://github.com/docker/docker-agent/tree/main/examples).

## Development team

{{- $example := .Get 0 }}
{{- $baseUrl := "https://raw.githubusercontent.com/docker/docker-agent/refs/heads/main/examples" }}
{{- $url := fmt.Printf "%s/%s" $baseUrl $example }}
{{- with resources.GetRemote $url }}
{{ $data := .Content | transform.Unmarshal }}

```yaml {collapse=true}
{{ .Content }}
```

{{ end }}

## Go developer

## Technical blog writer
