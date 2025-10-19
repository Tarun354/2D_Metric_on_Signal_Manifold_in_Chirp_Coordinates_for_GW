# 2D_Metric_on_Signal_Manifold_in_Chirp_Coordinates_for_GW

This repository computes the **2D metric** on the **signal manifold** in **dimensionless chirp coordinates** using the **Fisher Information Matrix (FIM)**.  
It also verifies the **metric approximation** by comparing **exact waveform matches** with **metric-based estimates**.
<b>
h(t⃗, λ⃗) = A(t⃗, λ⃗)e^(-iφ(t⃗,λ⃗))
```

where the waveform is parameterized by:
- **Intrinsic parameters** λ⃗ᵢₙₜᵣ: masses (m₁, m₂), spins (s₁z, s₂z, ...)
- **Extrinsic parameters** λ⃗ₑₓₜᵣ: sky position (ι₀, φ₀)

#### Match Between Templates

The match between two neighboring templates in parameter space is:
```
M(λ⃗, λ⃗+Δλ⃗) = max_Δλ⃗ₑₓₜᵣ ⟨ĥ(λ⃗), ĥ(λ⃗+Δλ⃗)⟩
```

where:
- ĥ = h/||h|| is the normalized waveform
- ⟨·,·⟩ denotes the inner product inversely weighted by the one-sided power spectral density Sₕ(f) (overlap)

The overlap is computed as:
```
⟨a,b⟩ = ∫[fₗₒw to fₕᵢgₕ] [a*(f)b(f) + a(f)b*(f)] / Sₕ(f) df
```

## Mathematical Framework

### Approximate Match Expression

The match is approximated by Taylor expanding around Δλ⃗ = 0 up to quadratic terms:
```
M(λ⃗, λ⃗+Δλ⃗) = M(λ⃗, λ⃗+Δλ⃗)|[Δλ⃗=0] + Δλ⃗ᵀ ∂M(λ⃗,λ⃗+Δλ⃗)/∂λ⃗|[Δλ⃗=0] + (1/2)Δλᵢ Δλⱼ ∂²M(λ⃗,λ⃗+Δλ⃗)/(∂λᵢ∂λⱼ)|[Δλ⃗=0]
```

### Simplified Match Expression

Using the initial conditions:
- M(λ⃗, λ⃗+Δλ⃗)|[Δλ⃗=0] = M(λ⃗, λ⃗) = ⟨ĥ(t⃗,λ⃗), ĥ(t⃗,λ⃗)⟩ = 1
- ∂M(λ⃗, λ⃗+Δλ⃗)/∂λ⃗|[Δλ⃗=0] = 0

The simplified form becomes:
```
M(λ⃗, λ⃗+Δλ⃗) = 1 + (1/2) (∂²M)/(∂λᵢ∂λⱼ) Δλᵢ Δλⱼ
```

### Final Metric Expression
```
M(λ⃗, λ⃗+Δλ⃗) = 1 - gᵢⱼ Δλᵢ Δλⱼ = 1 - Δs²
```

where the metric is defined as:
```
gᵢⱼ = -(1/2) (∂²M)/(∂λᵢ∂λⱼ)|[Δλ⃗=0]
```

## Fisher Information Matrix

### Computation Method

The metric is computed by evaluating the Fisher information matrix over the full parameter space and projecting out the extrinsic parameters.

The Fisher matrix elements are:
```
Γ̃ₐᵦ = ⟨∂ₐĥ, ∂ᵦĥ⟩
```

where ∂ₐ denotes the partial derivative of the waveform with respect to parameter a.

### Numerical Derivatives

Derivatives are calculated using the finite difference method:
```
f'(x) ≈ [f(x+h) - f(x-h)]/(2h) + O(h²)
```

### Fisher Matrix Expansion

For normalized waveforms ĥ(t⃗,λ⃗) = h(t⃗,λ⃗)/||h||, the Fisher matrix element becomes:
```
Γ̃ₐᵦ = (1/||h||²)[⟨Ae^(-iφ)(-i)∂ₐφ, Ae^(-iφ)(-i)∂ᵦφ⟩
                  + ⟨Ae^(-iφ)(-i)∂ₐφ, e^(-iφ)∂ᵦA⟩
                  + ⟨e^(-iφ)∂ₐA, Ae^(-iφ)(-i)∂ᵦφ⟩
                  + ⟨∂ₐA, ∂ᵦA⟩]
```

The adjusted Fisher matrix (accounting for the 1/2 factor from Taylor expansion):
```
Γ̃ₐᵦ ≈ (1/(2||h||²))[⟨A∂ₐφ, A∂ᵦφ⟩ + ⟨∂ₐA, ∂ᵦA⟩]
```

## Parameter Space

### Intrinsic Parameters

The Fisher matrix is computed in the 5-dimensional parameter space:

**Chirp mass** (ℳc):
```
χᵣ = χₛ + δχ + (76η/113)χₛ
```

**Mass ratio** (η):
```
η = (m₁m₂)/(m₁+m₂)²
```

**Mass asymmetry** (δ):
```
δ = (m₁-m₂)/(m₁+m₂)
```

**Reduced spin** (χ):
```
χ = (χ₁+χ₂)/2
```

where we assume χ₁ = χ₂.

### Metric Projection

The template-space metric gᵢⱼ is computed by projecting Γ̃ₐᵦ onto the subspace orthogonal to λ⃗ₑₓₜᵣ:
```
g = Γ₁ - Γ₂Γ₃⁻¹Γ₄
<br>

**Author:** Tarun Kumar

