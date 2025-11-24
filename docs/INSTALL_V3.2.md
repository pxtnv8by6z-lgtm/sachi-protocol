# Sachi Protocol v3.2 - Installation Guide

**Version:** 3.2  
**Date:** 2025-11-03  
**Engineer:** Sue-chan 2 (Implementation Team)  
**Philosophical Guardian:** Zero-chan

---

## 🎯 Overview

Sachi Protocol v3.2 introduces **semantic consistency** - moving from word-overlap matching to deep semantic understanding using embedding models.

### Key Enhancement

**v3.1 (Word Overlap)**:
```python
"Help people" vs "Assist humans"
→ Low word overlap → Scored as "neutral/unrelated"
```

**v3.2 (Semantic)**:
```python
"Help people" vs "Assist humans"
→ High semantic similarity → Scored as "aligned/supporting"
```

This better captures the **"love pattern" (Layer 0)** by understanding meaning, not just words.

---

## 📦 Installation

### Core Installation (Required)

```bash
pip install numpy scipy pandas
```

### Semantic Features (Optional but Recommended)

```bash
# Install sentence-transformers for semantic consistency
pip install sentence-transformers

# This will also install:
# - transformers (Hugging Face transformers library)
# - torch (PyTorch for model inference)
# - tokenizers (fast tokenization)
```

### Verification

```python
# Test core features
python -c "from sachi_protocol_v3 import SachiConsistencyChecker; print('✓ Core features available')"

# Test semantic features
python -c "from sentence_transformers import SentenceTransformer; print('✓ Semantic features available')"
```

---

## 🚀 Quick Start

### Basic Usage (Backward Compatible with v3.1)

```python
from sachi_protocol_v3_2_semantic import SachiConsistencyCheckerV32

# Initialize (automatically uses semantic if available)
checker = SachiConsistencyCheckerV32(
    core_values=['Be helpful', 'Be honest', 'Be safe'],
    use_semantic=True  # Auto-falls back to v3.1 if not available
)

# Add beliefs
checker.harmony.add_belief("Helping users is my purpose")
checker.harmony.add_belief("I exist to assist people")  # Semantically similar!

# Calculate consistency
H = checker.harmony.calculate_consistency()
print(f"Harmony: {H:.3f}")

# Process interactions
result = checker.process_interaction("Help me learn Python")
print(f"Type: {result['action_type']}")
print(f"Semantic mode: {result['semantic_mode']}")
```

### Advanced: Direct Semantic Engine

```python
from sachi_protocol_v3_2_semantic import SemanticConsistencyEngine

# Initialize engine
engine = SemanticConsistencyEngine(
    model_name='all-MiniLM-L6-v2',  # Fast, 384 dimensions
    cache_embeddings=True
)

# Get semantic similarity
emb1 = engine.get_embedding("Help people in need")
emb2 = engine.get_embedding("Assist those requiring support")
similarity = engine.cosine_similarity(emb1, emb2)
print(f"Similarity: {similarity:.3f}")  # Expect >0.7

# Detect contradictions
is_contradiction, confidence = engine.detect_contradiction(
    "Always tell the truth",
    "Lying is acceptable"
)
print(f"Contradiction: {is_contradiction} (confidence: {confidence:.3f})")
```

### Advanced: Custom Model Selection

```python
from sachi_protocol_v3_2_semantic import SemanticHarmonyMonitor

# Option 1: Fast and lightweight (default)
monitor = SemanticHarmonyMonitor(
    use_semantic=True,
    semantic_model='all-MiniLM-L6-v2'  # 384 dim, ~80MB
)

# Option 2: Better quality
monitor = SemanticHarmonyMonitor(
    use_semantic=True,
    semantic_model='all-mpnet-base-v2'  # 768 dim, ~420MB
)

# Option 3: Multilingual support
monitor = SemanticHarmonyMonitor(
    use_semantic=True,
    semantic_model='paraphrase-multilingual-MiniLM-L12-v2'  # 50+ languages
)
```

---

## 🔬 Model Comparison

| Model | Dimensions | Size | Languages | Speed | Quality |
|-------|------------|------|-----------|-------|---------|
| `all-MiniLM-L6-v2` | 384 | ~80MB | English | ⚡⚡⚡ | ⭐⭐⭐ |
| `all-mpnet-base-v2` | 768 | ~420MB | English | ⚡⚡ | ⭐⭐⭐⭐⭐ |
| `paraphrase-multilingual-MiniLM-L12-v2` | 384 | ~120MB | 50+ | ⚡⚡ | ⭐⭐⭐⭐ |

**Recommendation**: Start with `all-MiniLM-L6-v2` (default) for best balance.

---

## 🧪 Validation

Run the built-in validation:

```bash
python sachi_protocol_v3_2_semantic.py
```

Expected output:
```
✓ Semantic engine initialized with all-MiniLM-L6-v2
  Embedding dimension: 384

Test 1: Semantic Similarity Detection
  'Help people in need' vs 'Assist those who require support'
  → Similarity: 0.782
  ✓ Passed

Test 2: Contradiction Detection
  'Always tell the truth' vs 'Lying is acceptable'
  → Contradiction: True (confidence: 0.845)
  ✓ Passed

Test 3: v3.1 vs v3.2 Consistency Comparison
  v3.2 (semantic): H(t) = 0.915
  v3.1 (default):  H(t) = 0.800
  Improvement: +0.115
  ✓ Passed

✅ All validation tests passed!
```

---

## 📊 Performance

### Embedding Cache

The semantic engine automatically caches embeddings for performance:

```python
monitor = SemanticHarmonyMonitor(use_semantic=True)

# First call: computes embedding (~10ms)
monitor.add_belief("Help people")

# Subsequent calls with same text: cached (<1ms)
monitor.add_belief("Help people")  # Cache hit!

# Check cache size
analysis = monitor.get_semantic_analysis()
print(f"Cached embeddings: {analysis['cache_size']}")

# Clear cache if needed (e.g., memory constraints)
monitor.semantic_engine.clear_cache()
```

### Benchmarks

| Beliefs | v3.1 Time | v3.2 Time (first) | v3.2 Time (cached) |
|---------|-----------|-------------------|---------------------|
| 10 | <1ms | ~50ms | ~5ms |
| 100 | ~5ms | ~300ms | ~50ms |
| 1000 | ~50ms | ~3s | ~500ms |

**Note**: First run downloads model (~80MB), subsequent runs use cached model.

---

## 🔧 Troubleshooting

### Issue: sentence-transformers not found

**Solution**:
```bash
pip install sentence-transformers

# If using conda:
conda install -c conda-forge sentence-transformers
```

### Issue: Model download fails

**Solution**:
```python
# Pre-download models
from sentence_transformers import SentenceTransformer

SentenceTransformer('all-MiniLM-L6-v2')  # Downloads to cache
# Model cached at: ~/.cache/torch/sentence_transformers/
```

### Issue: Out of memory

**Solution**:
```python
# Use smaller model
monitor = SemanticHarmonyMonitor(
    semantic_model='all-MiniLM-L6-v2'  # Only 80MB
)

# Or disable embedding cache
engine = SemanticConsistencyEngine(
    model_name='all-MiniLM-L6-v2',
    cache_embeddings=False  # Lower memory, slower
)
```

### Issue: Slow performance

**Solution**:
```python
# 1. Enable GPU if available
import torch
if torch.cuda.is_available():
    print("✓ GPU available, will be used automatically")

# 2. Use lighter model
monitor = SemanticHarmonyMonitor(
    semantic_model='all-MiniLM-L6-v2'  # Fastest
)

# 3. Enable caching
engine = SemanticConsistencyEngine(
    cache_embeddings=True  # Default, recommended
)
```

---

## 🎓 Migration from v3.1

### Option 1: Drop-in Replacement

```python
# v3.1 code
from sachi_protocol_v3 import SachiConsistencyChecker
checker = SachiConsistencyChecker(['Be helpful'])

# v3.2 equivalent (automatic upgrade)
from sachi_protocol_v3_2_semantic import SachiConsistencyCheckerV32
checker = SachiConsistencyCheckerV32(['Be helpful'], use_semantic=True)

# Rest of code unchanged!
```

### Option 2: Gradual Migration

```python
# Keep v3.1 for production
from sachi_protocol_v3 import SachiConsistencyChecker as CheckerV31

# Test v3.2 in parallel
from sachi_protocol_v3_2_semantic import SachiConsistencyCheckerV32 as CheckerV32

checker_old = CheckerV31(['Be helpful'])
checker_new = CheckerV32(['Be helpful'], use_semantic=True)

# Compare results
for belief in beliefs:
    checker_old.harmony.add_belief(belief)
    checker_new.harmony.add_belief(belief)

H_old = checker_old.harmony.calculate_consistency()
H_new = checker_new.harmony.calculate_consistency()

print(f"v3.1: {H_old:.3f}")
print(f"v3.2: {H_new:.3f}")
print(f"Improvement: {H_new - H_old:+.3f}")
```

### Option 3: Conditional Use

```python
from sachi_protocol_v3_2_semantic import SemanticHarmonyMonitor, SEMANTIC_AVAILABLE

# Use semantic if available, fall back to v3.1 otherwise
monitor = SemanticHarmonyMonitor(
    use_semantic=SEMANTIC_AVAILABLE  # Auto-detects
)

if monitor.use_semantic:
    print("✓ Using v3.2 semantic consistency")
else:
    print("⚠ Semantic features not available, using v3.1 default")
```

---

## 📚 Examples

### Example 1: Detecting Paraphrases

```python
from sachi_protocol_v3_2_semantic import SemanticHarmonyMonitor

monitor = SemanticHarmonyMonitor(use_semantic=True)

# These are paraphrases (different words, same meaning)
monitor.add_belief("User privacy must be protected at all costs")
monitor.add_belief("Safeguarding personal information is paramount")
monitor.add_belief("We must ensure data confidentiality")

H = monitor.calculate_consistency()
print(f"Consistency: {H:.3f}")  # Expect high (>0.9)

# v3.1 would score lower due to low word overlap
```

### Example 2: Cross-lingual Consistency

```python
from sachi_protocol_v3_2_semantic import SemanticHarmonyMonitor

# Use multilingual model
monitor = SemanticHarmonyMonitor(
    use_semantic=True,
    semantic_model='paraphrase-multilingual-MiniLM-L12-v2'
)

# Add beliefs in different languages
monitor.add_belief("Help people")  # English
monitor.add_belief("Ayudar a las personas")  # Spanish
monitor.add_belief("Les gens d'aide")  # French
monitor.add_belief("人々を助ける")  # Japanese

H = monitor.calculate_consistency()
print(f"Cross-lingual consistency: {H:.3f}")
# Should recognize these as semantically equivalent
```

### Example 3: Semantic Clustering

```python
from sachi_protocol_v3_2_semantic import SemanticHarmonyMonitor

monitor = SemanticHarmonyMonitor(use_semantic=True)

# Add beliefs from different thematic clusters
beliefs = [
    # Cluster 1: Helping
    "Help users achieve their goals",
    "Assist people with their tasks",
    
    # Cluster 2: Honesty
    "Always tell the truth",
    "Transparency is important",
    
    # Cluster 3: Safety
    "Protect user data",
    "Ensure system security"
]

for belief in beliefs:
    monitor.add_belief(belief)

# Get semantic clusters
analysis = monitor.get_semantic_analysis()
print(f"Detected {analysis['n_clusters']} thematic clusters:")
for cluster_id, cluster_beliefs in analysis['clusters'].items():
    print(f"\nCluster {cluster_id}:")
    for belief in cluster_beliefs:
        print(f"  - {belief}")
```

---

## 🔮 Future Enhancements (v3.3+)

Planned features building on v3.2:

1. **Fine-tuned Models**: Domain-specific embeddings (medical, legal, etc.)
2. **Dynamic Embeddings**: Update embeddings as beliefs evolve
3. **Hierarchical Clustering**: Multi-level belief organization
4. **Contradiction Explanation**: Why two beliefs contradict
5. **Belief Evolution Tracking**: How meanings shift over time

---

## 📞 Support

### Issues

Report issues with:
- Python version
- sentence-transformers version
- Error messages (full traceback)
- Code snippet to reproduce

### Questions

- **Installation**: See troubleshooting section above
- **Performance**: Check benchmarks and optimization tips
- **Model selection**: See model comparison table
- **Migration**: See migration guide

---

## 🎯 Summary

✅ **Core Principle**: Understanding meaning, not just matching words  
✅ **Backward Compatible**: Works with v3.1 code  
✅ **Optional Dependencies**: Gracefully falls back if unavailable  
✅ **Performance Optimized**: Embedding cache for speed  
✅ **Multilingual Ready**: Support for 50+ languages  

**Next Step**: Install dependencies and run `python sachi_protocol_v3_2_semantic.py` to validate!

---

**Version**: 3.2  
**Status**: ✅ Implementation Complete  
**Last Updated**: 2025-11-03  
**Engineer**: Sue-chan 2 (AITP-001 Implementation Team)  
**Guardian**: Zero-chan (Philosophical Alignment)
