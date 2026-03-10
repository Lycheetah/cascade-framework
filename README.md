# CASCADE: Self-Reorganizing Knowledge Structures via Truth Pressure

**CASCADE** formalizes how scientific paradigm shifts work computationally: when new knowledge with stronger evidence contradicts existing foundations, the system *contextualizes* the old knowledge (demotes it to "valid in limited scope") rather than deleting it, while promoting the new knowledge to foundational status.

One metric (truth pressure Π), three layers (Foundation/Theory/Edge), four phases, three provable invariants.

## The Core Idea

When Newtonian mechanics met quantum mechanics, science didn't delete Newton. It contextualized him: "excellent approximation at macroscopic scales." CASCADE does this automatically, and we can prove that coherence never decreases, information is never lost, and the right block always gets promoted — remove truth pressure and accuracy drops to coin-flip (48–58%).

## Results

| Domain | Fidelity Checks | Invariant Preservation | Demotion Accuracy | Without Π |
|--------|:-:|:-:|:-:|:-:|
| Synthetic (1,000 cascades) | — | 100% | 100% | 48% |
| Miasma → Germ Theory | 5/5 | 100% | 100% | 57.7% |
| Classical → Quantum Physics | 7/7 | 100% | 100% | 55.8% |

**Paper:** `paper/CASCADE_FINAL_ARXIV_READY.tex` (arXiv submission pending)

## Quick Start

```bash
# Clone
git clone https://github.com/Lycheetah/cascade-framework.git
cd cascade-framework

# Install dependencies (just numpy and scipy)
pip install numpy scipy

# Run all experiments (synthetic + both historical domains)
cd experiments
python run_experiments.py

# Run with custom settings
python run_experiments.py --trials 500 --seed 123
```

## Repository Structure

```
cascade-framework/
├── paper/
│   └── CASCADE_FINAL_ARXIV_READY.tex    # arXiv paper (LaTeX source)
├── experiments/
│   ├── cascade_engine.py                 # Core engine (domain-agnostic)
│   ├── cascade_real_experiments.py       # Synthetic experiments from paper
│   ├── domain_germ_theory.py             # Miasma → Germ Theory dataset
│   ├── domain_quantum_physics.py         # Classical → Quantum dataset
│   ├── domain_template.py                # Template for adding new domains
│   └── run_experiments.py                # Run all domain experiments
├── README.md
└── LICENSE
```

## Adding a New Domain

Copy `experiments/domain_template.py`, fill in your knowledge blocks with evidence scores, define fidelity checks, and import in `run_experiments.py`. The engine handles everything else. See the template for a scoring guide.

## Limitations (read these)

- Evidence scores in historical experiments are author-assigned judgments, not independently measured
- Contradiction detection uses domain labels, not natural language inference
- Tested on ≤15 blocks per domain; scalability beyond 10⁴ blocks needs approximate methods
- No neural network integration — operates on symbolic knowledge blocks
- The mechanism requires an external contradiction oracle

These are stated in the paper. We're working on independent annotator validation.

## How to Cite

Paper is pending arXiv submission. For now:

```
Clark, M. C. J. (2026). CASCADE: Self-Reorganizing Knowledge Structures
via Truth Pressure and Coherence-Preserving Demotion. Lycheetah Foundation.
https://github.com/Lycheetah/cascade-framework
```

## License

MIT License. See [LICENSE](LICENSE).

## Author

**Mackenzie C. J. Clark** — [Lycheetah Foundation](https://github.com/Lycheetah), Dunedin, New Zealand

Independent research. No external funding. Built on a 2012 laptop with numpy and scipy.
