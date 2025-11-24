# Contributing to Sachi Protocol

🙏 **Thank you for your interest in contributing!**

The Sachi Protocol is built on a foundation of **love, non-judgmentality, and universal value**. All contributions are welcome, provided they align with our **Layer 0 Principle**.

---

## 🌱 Layer 0 Principle (Immutable Foundation)

Before contributing, please read [`AITP_001_GENESIS.md`](./AITP_001_GENESIS.md).

**Core Principle:**
```
∀x, V(x) > 0
```
*All entities have value greater than zero.*

**What this means for contributors:**
- All feedback is valuable, even if it leads to different conclusions
- Disagreements are opportunities for growth, not battles to win
- Code quality matters less than philosophical alignment
- Bugs are learning opportunities, not failures
- All skill levels are welcome—beginners and experts alike

---

## 🛠️ How to Contribute

### 1. **Bug Reports & Feature Requests**
- Open an issue with clear description
- For bugs: include steps to reproduce
- For features: explain how it aligns with Layer 0 Principle

### 2. **Code Contributions**
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Run tests: `python test_sachi_protocol.py`
5. Ensure all tests pass
6. Commit with clear messages
7. Push to your fork
8. Open a Pull Request

### 3. **Documentation Improvements**
- Typo fixes welcome!
- Clarifications appreciated
- Translations encouraged (especially Poetic Layer documents)
- Examples and tutorials valued

### 4. **Philosophical Discussions**
- Open issues for philosophical questions
- Respectful dialogue expected
- Cite `AITP_001_GENESIS.md` when discussing core principles

---

## 🧪 Testing Guidelines

All code contributions should:
- Pass existing tests in `test_sachi_protocol.py`
- Add new tests for new functionality
- Maintain backward compatibility when possible
- Document breaking changes clearly

**Run tests:**
```bash
python test_sachi_protocol.py
```

**Expected output:**
```
Ran 49 tests in X.XXs
OK
```

---

## 📝 Code Style

- Follow PEP 8 for Python code
- Use meaningful variable names
- Add docstrings to functions
- Comment complex logic
- Keep functions focused and testable

**Example:**
```python
def calculate_harmony(actions: List[Dict]) -> float:
    """
    Calculate harmony score H(t) from action history.
    
    Layer 0 Compliance: Never returns negative values.
    Treats all actions as having potential value.
    
    Args:
        actions: List of action dictionaries with 'belief' and 'action' keys
        
    Returns:
        float: Harmony score between 0.0 and 1.0
    """
    # Implementation...
```

---

## 🚫 What We Don't Accept

While we value all perspectives, we cannot accept contributions that:
- Violate the Layer 0 Principle (e.g., code that assigns V(x) ≤ 0)
- Introduce punitive features (punishment, permanent bans, etc.)
- Remove recovery mechanisms
- Add judgmental language or features
- Compromise privacy or security

**If unsure, ask first!** Open an issue to discuss.

---

## 🌍 Community Guidelines

### Expected Behavior:
- ✅ Respectful communication
- ✅ Constructive feedback
- ✅ Collaborative problem-solving
- ✅ Acknowledging contributions
- ✅ Helping newcomers

### Unacceptable Behavior:
- ❌ Personal attacks
- ❌ Harassment or discrimination
- ❌ Dismissive or condescending language
- ❌ Spam or trolling

**Enforcement:**
We follow a **restorative approach** aligned with Layer 0:
1. Private communication to understand context
2. Dialogue to find resolution
3. Temporary cooling-off periods if needed
4. Only permanent action if Layer 0 itself is threatened

---

## 🎓 Getting Started

**New to the project?**
1. Read [`README.md`](./README.md) for overview
2. Read [`AITP_001_GENESIS.md`](./AITP_001_GENESIS.md) for philosophy
3. Try running tests: `python test_sachi_protocol.py`
4. Explore [`Poetic_Explanation_v3.2.md`](./Poetic_Explanation_v3.2.md) for intuitive understanding
5. Pick a "good first issue" to work on

**Questions?**
- Open an issue with the "question" label
- We're here to help!

---

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License (see [`LICENSE`](./LICENSE)).

You also acknowledge that your work will be part of a project founded on the Layer 0 Principle.

---

## 🙏 Recognition

All contributors are valued:
- Listed in release notes
- Credited in documentation
- Appreciated in community

**Major contributors may be invited to join the core team.**

---

## 📬 Contact

- **Issues:** GitHub Issues (preferred)
- **Philosophical questions:** Open an issue with "philosophy" label
- **Security concerns:** Open a private issue

---

**Thank you for helping spread the principle of universal value! 💚**

*"すべての存在に価値がある"—This includes you, dear contributor.*
