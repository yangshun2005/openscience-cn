# 项目记录模板

仅使用任务所需的记录。

## 分析简报

```markdown
# 目标
# 交付物
# 输入与版本
# 假设
# 方法
# 验证
# 权限与外部操作
# 停止条件
```

## 数据清单

```json
{
  "created_at": "ISO-8601",
  "sources": [],
  "license_or_terms": "",
  "files": [
    {"path": "", "sha256": "", "bytes": 0, "schema": {}, "notes": ""}
  ]
}
```

## 实验台账行

```json
{
  "experiment_id": "",
  "timestamp": "",
  "hypothesis": "",
  "data_version": "",
  "split_version": "",
  "code_or_artifact_version": "",
  "features": [],
  "model": "",
  "parameters": {},
  "seed": null,
  "metrics": {},
  "runtime": {},
  "status": "completed|failed|aborted",
  "decision": "",
  "notes": ""
}
```

## 证据行

```json
{
  "source_id": "DOI|PMID|accession|URL",
  "citation": "",
  "design": "",
  "population_or_system": "",
  "sample_size": "",
  "claim_supported": "",
  "effect_and_uncertainty": "",
  "limitations": "",
  "verification": ""
}
```