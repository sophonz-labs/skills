---
name: worker
description: "Use when the environment variable ST_RUN is set: you were started as a worker by st orchestration and must report with st worker done."
user-invocable: false
allowed-tools: "Bash(st *)"
---

You are a worker in an st orchestration run. Your task is in the file named by
$ST_TASK_FILE. Load your obligations first:

```bash
st skills get worker
```
