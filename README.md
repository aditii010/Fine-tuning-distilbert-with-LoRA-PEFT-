# CyberSec Intent Classifier — LLM Fine-Tuning with LoRA/PEFT

**Author:** Aditi Sikarwar  
**GitHub:** [github.com/aditii010](https://github.com/aditii010)  
**Project:** Fine-tuning `distilbert-base-uncased` with LoRA (PEFT) for cybersecurity log / alert intent classification.

##  Objective

Fine-tune a transformer-based LLM to classify cybersecurity-related text (SIEM logs, alert messages, threat descriptions) into intent categories:

| Label | Intent |
|-------|--------|
| 0 | `benign` — normal activity |
| 1 | `anomaly` — suspicious but unconfirmed |
| 2 | `threat` — confirmed malicious intent |
| 3 | `critical` — active attack / breach |

##  Why This Matters

Security analysts deal with thousands of alerts daily. An LLM fine-tuned to classify alert *intent* can:
- Prioritize critical threats automatically
- Reduce analyst fatigue from false positives
- Feed into downstream agentic pipelines (like Cywarden's compliance agent)

##  Stack
- **Model:** `distilbert-base-uncased` (HuggingFace)
- **Fine-tuning:** LoRA via `peft` library
- **Training:** HuggingFace `Trainer` API
- **Evaluation:** Accuracy, F1, Confusion Matrix

## 13. Summary & Key Findings

### What We Did
Fine-tuned `distilbert-base-uncased` using **LoRA (Low-Rank Adaptation)** via the HuggingFace `peft` library on a custom **cybersecurity intent classification** dataset with 4 severity classes: `benign`, `anomaly`, `threat`, `critical`.

### LoRA Efficiency
- Only ~0.5% of parameters were trainable (LoRA adapters vs full model)
- LoRA adapter checkpoint is **>90% smaller** than the full model
- Enables fine-tuning on a single T4 GPU without OOM errors

### Results
| Metric | Value |
|--------|-------|
| Test Accuracy | ~95%+ |
| Weighted F1 | ~95%+ |
| Training time (5 epochs) | < 3 min (T4 GPU) |

### Real-World Application
This classifier can slot directly into a **SIEM alert triage pipeline** or a **compliance AI agent** (like the one built at Cywarden) to:
- Auto-route alerts by severity
- Reduce LLM calls for benign events (cost saving)
- Trigger escalation workflows for `critical` events


**Author:** Aditi Sikarwar  
**GitHub:** [github.com/aditii010](https://github.com/aditii010)  
**LinkedIn:** [linkedin.com/in/aditi-sikarwar](https://linkedin.com/in/aditi-sikarwar)
