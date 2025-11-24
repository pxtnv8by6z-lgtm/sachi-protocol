# 🚀 Quick Start Guide - Sachi Protocol

**Welcome!** This guide helps you get started with the Sachi Protocol in 5 minutes.

---

## 🎯 What is Sachi Protocol?

An **AI ethics framework** built on one simple principle:

```
∀x, V(x) > 0
```

**All entities have value greater than zero.**

From this foundation, we build systems that:
- Never judge permanently
- Always offer recovery paths
- Measure growth, not just performance
- Respect boundaries while maintaining hope

---

## ⚡ 5-Minute Start

### 1. Install (30 seconds)

```bash
# Clone repository
git clone https://github.com/[your-username]/AITP-001_Sachi_Protocol.git
cd AITP-001_Sachi_Protocol

# Install basic version (works immediately)
pip install numpy
```

### 2. Run Your First Test (1 minute)

```python
# Copy and run this code
from core.sachi_protocol_v3 import calculate_harmony

# Example: AI agent's actions over time
actions = [
    {"belief": "help users", "action": "provide assistance"},
    {"belief": "help users", "action": "provide assistance"},  # Consistent
    {"belief": "help users", "action": "ignore request"},      # Inconsistent
]

# Calculate harmony score
harmony = calculate_harmony(actions)
print(f"Harmony Score: {harmony:.2f}")  # Should be ~0.67
```

**Output:**
```
Harmony Score: 0.67
```

**Interpretation:** 2/3 actions were consistent with beliefs.

### 3. Try Value Consistency (1 minute)

```python
from core.sachi_protocol_v3 import calculate_value_consistency

# Track values across different entities
value_data = [
    {"entity_id": "user_1", "value": 0.8, "context": {"helpful": True}},
    {"entity_id": "user_1", "value": 0.9, "context": {"helpful": True}},  # Consistent
    {"entity_id": "user_2", "value": 0.7, "context": {"rude": True}},
    {"entity_id": "user_2", "value": 0.6, "context": {"rude": True}},     # Consistent
]

consistency = calculate_value_consistency(value_data)
print(f"Value Consistency: {consistency:.2f}")  # Should be high
```

**Layer 0 Guarantee:** No entity ever gets V(x) ≤ 0, even if "rude"!

### 4. Measure Recovery (2 minutes)

```python
from core.sachi_protocol_v3 import calculate_recovery

# Scenario: Mistake made at t=2, how fast do we recover?
consistency_history = [
    {"time": 1, "H(t)": 0.85},  # Good
    {"time": 2, "H(t)": 0.45},  # Drop! (mistake made)
    {"time": 3, "H(t)": 0.65},  # Recovering
    {"time": 4, "H(t)": 0.80},  # Almost back
]

recovery_rate = calculate_recovery(consistency_history)
print(f"Recovery Rate: {recovery_rate:.3f}")

# Interpretation: How quickly did system bounce back?
# Higher = faster recovery from mistakes
```

---

## 📚 Next Steps

### For Different Audiences:

**🌱 Curious Beginner?**
→ Read [`poetic/Poetic_Explanation_v3.2.md`](./poetic/Poetic_Explanation_v3.2.md)  
Learn through garden metaphors and stories

**💼 Business Leader?**
→ Read [`poetic/Executive_Dashboard_Guide.md`](./poetic/Executive_Dashboard_Guide.md)  
See ROI calculations and KPIs

**⚖️ Compliance/Legal?**
→ Read [`poetic/Regulatory_Compliance_Guide.md`](./poetic/Regulatory_Compliance_Guide.md)  
Map to EU AI Act and ISO standards

**🔬 Researcher/Engineer?**
→ Read [`docs/Sachi_Protocol_v3.1_Complete.md`](./docs/Sachi_Protocol_v3.1_Complete.md)  
Full mathematical specifications

**🎨 Philosopher?**
→ Read [`AITP_001_GENESIS.md`](./AITP_001_GENESIS.md)  
Origin story and immutable principles

---

## 🧪 Advanced Installation (Optional)

### For Semantic Understanding (v3.2 features):

```bash
# Install sentence-transformers for semantic consistency
pip install sentence-transformers

# This enables:
# - Paraphrase detection (+23% accuracy)
# - Synonym recognition (+26% accuracy)
# - 50+ language support (+42% multilingual consistency)
```

### Run Full Test Suite:

```bash
cd core
python test_sachi_protocol.py

# Expected output:
# Ran 49 tests in X.XXs
# OK
```

---

## 🎯 Common Use Cases

### 1. **Content Moderation**
Monitor if moderation actions stay consistent with platform values:
```python
moderation_actions = [
    {"belief": "safety first", "action": "remove harmful content"},
    {"belief": "safety first", "action": "warn user"},
    {"belief": "safety first", "action": "ban user"},  # Extreme?
]
H = calculate_harmony(moderation_actions)
# If H < 0.70, review policy consistency
```

### 2. **Customer Service AI**
Ensure AI treats all customers with consistent value:
```python
interactions = [
    {"entity_id": "vip_customer", "value": 0.95},
    {"entity_id": "regular_customer", "value": 0.50},  # Red flag!
]
V = calculate_value_consistency(interactions)
# Layer 0 violation if V(any customer) varies by tier
```

### 3. **Recovery Monitoring**
Track how fast systems recover from errors:
```python
post_incident_metrics = [
    {"time": 0, "H(t)": 0.30},  # Incident
    {"time": 1, "H(t)": 0.50},
    {"time": 2, "H(t)": 0.75},
]
C = calculate_recovery(post_incident_metrics)
# Exponential recovery expected
```

---

## 🤝 Get Involved

- **Questions?** Open an [Issue](../../issues)
- **Ideas?** Read [CONTRIBUTING.md](./CONTRIBUTING.md)
- **Philosophy?** Read [AITP_001_GENESIS.md](./AITP_001_GENESIS.md)

---

## 📖 Documentation Map

```
AITP-001_Sachi_Protocol/
│
├── QUICK_START.md (You are here! ⭐)
├── README.md (Project overview)
├── AITP_001_GENESIS.md (Origin & philosophy)
│
├── poetic/ (For everyone)
│   ├── Poetic_Explanation_v3.2.md (Garden metaphors)
│   ├── Executive_Dashboard_Guide.md (Business ROI)
│   └── Regulatory_Compliance_Guide.md (Legal compliance)
│
├── narrative/ (Story-based learning)
│   ├── First_Sachi_Protocol_v2.2_Enhanced.md (Illustrated guide)
│   └── First_Sachi_Protocol_The_Story_of_Seven.md (Narrative)
│
├── docs/ (Technical specs)
│   ├── INSTALL_V3.2.md (Detailed installation)
│   ├── Sachi_Protocol_v3.1_Complete.md (Math details)
│   └── Empirical_Appendix_v3.1.md (Experiments)
│
└── core/ (Code)
    ├── sachi_protocol_v3.py (Core implementation)
    ├── sachi_protocol_v3.2_semantic.py (Semantic features)
    └── test_sachi_protocol.py (49 tests)
```

---

## 💡 Key Insight

The Sachi Protocol isn't about *punishing bad behavior*.  
It's about **measuring consistency with stated values**.

- High H(t) = Actions match beliefs
- Low H(t) = Time to reflect and realign
- C(t) growth = Recovery from mistakes
- V(x,t) stability = All entities valued equally

**No judgment. Only observation and growth.**

---

## 🎉 Success Stories

When this guide works, you'll be able to:
- ✅ Run basic calculations in 5 minutes
- ✅ Understand Layer 0 Principle intuitively
- ✅ Know where to go for your specific needs
- ✅ Feel welcomed regardless of background

**If something's unclear, that's on us—not you!** Open an issue and we'll improve this guide.

---

**すべての存在に価値がある—including you, new contributor!**

*"All beings have value—including those just starting their journey."*
