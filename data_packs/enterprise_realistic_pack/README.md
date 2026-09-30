# 数据包

## 使用方式

先分析资料真实度：

```powershell
python scripts/enterprise_overlay/analyze_enterprise_data_realism.py --output reports/verification/enterprise_data_realism_latest.json
```

再构建 clean overlay 预览数据集并跑入库质量门禁：

```powershell
python scripts/enterprise_overlay/build_enterprise_overlay_dataset.py --all-scenarios --output reports/verification/enterprise_overlay_build_latest.json
```

最后分析 dirty samples 的治理风险：

```powershell
python scripts/enterprise_overlay/analyze_dirty_enterprise_samples.py --output reports/verification/dirty_enterprise_samples_latest.json
```

只有 `clean_overlay/` 预检通过后，才可以进入知识库版本重建和回归评测。`dirty_samples/`
始终作为治理样本，不直接进入 active 知识库。

