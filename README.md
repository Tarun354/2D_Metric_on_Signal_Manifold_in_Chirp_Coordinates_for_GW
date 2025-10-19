<h1>2D Metric on Signal Manifold in Chirp Coordinates for Gravitational Waves</h1>

<p>This repository computes the <strong>2D metric on the signal manifold</strong> in dimensionless chirp coordinates using the <strong>Fisher Information Matrix</strong>, and verifies the metric approximation by comparing exact and metric-based matches.</p>

<hr>

<h2>Waveform Model</h2>

<p>The waveform is parameterized as:</p>

<p style="text-align:center;">
h(<i>t⃗</i>, λ⃗) = A(<i>t⃗</i>, λ⃗) e<sup>-i φ(<i>t⃗</i>, λ⃗)</sup>
</p>

<p>where the parameters are:</p>

<ul>
  <li><strong>Intrinsic parameters</strong> λ⃗<sub>intr</sub>: masses (m<sub>1</sub>, m<sub>2</sub>), spins (s<sub>1z</sub>, s<sub>2z</sub>, …)</li>
  <li><strong>Extrinsic parameters</strong> λ⃗<sub>extr</sub>: sky position and orientation (ι<sub>0</sub>, φ<sub>0</sub>)</li>
</ul>

<hr>

<h2>Match Between Templates</h2>

<p>The match between two neighboring templates in parameter space is defined as:</p>

<p style="text-align:center;">
M(λ⃗, λ⃗ + Δλ⃗) = max<sub>Δλ⃗<sub>extr</sub></sub> &lt;ĥ(λ⃗), ĥ(λ⃗ + Δλ⃗)&gt;
</p>

<p>where:</p>
<ul>
  <li>ĥ = h / ||h|| is the normalized waveform</li>
  <li>&lt;a, b&gt; = ∫<sub>f<sub>low</sub></sub><sup>f<sub>high</sub></sup> [a*(f)b(f) + a(f)b*(f)] / S<sub>h</sub>(f) df is the PSD-weighted inner product</li>
</ul>

<hr>

<h2>Approximate Match Expression</h2>

<p>Using a Taylor expansion around Δλ⃗ = 0 up to quadratic terms:</p>

<p style="text-align:center;">
M(λ⃗, λ⃗ + Δλ⃗) = M|<sub>Δλ⃗=0</sub> + Δλ⃗ᵀ ∂M/∂λ⃗ |<sub>Δλ⃗=0</sub> + 1/2 Δλ<sub>i</sub> Δλ<sub>j</sub> ∂²M/∂λ<sub>i</sub>∂λ<sub>j</sub> |<sub>Δλ⃗=0</sub>
</p>

<p>With initial conditions:</p>
<ul>
  <li>M|<sub>Δλ⃗=0</sub> = 1</li>
  <li>∂M/∂λ⃗ |<sub>Δλ⃗=0</sub> = 0</li>
</ul>

<p>We get the simplified match:</p>

<p style="text-align:center;">
M(λ⃗, λ⃗ + Δλ⃗) = 1 + 1/2 ∂²M/∂λ<sub>i</sub>∂λ<sub>j</sub> Δλ<sub>i</sub> Δλ<sub>j</sub>
</p>

<hr>

<h2>Metric Definition</h2>

<p>The <strong>template-space metric</strong> is defined as:</p>

<p style="text-align:center;">
M(λ⃗, λ⃗ + Δλ⃗) = 1 - g<sub>ij</sub> Δλ<sub>i</sub> Δλ<sub>j</sub> = 1 - Δs²
</p>

<p>with</p>

<p style="text-align:center;">
g<sub>ij</sub> = -1/2 ∂²M/∂λ<sub>i</sub>∂λ<sub>j</sub> |<sub>Δλ⃗=0</sub>
</p>

<hr>

<h2>Fisher Information Matrix</h2>

<p>The <strong>Fisher matrix elements</strong> are:</p>

<p style="text-align:center;">
Γ̃<sub>ab</sub> = &lt; ∂<sub>a</sub>ĥ, ∂<sub>b</sub>ĥ &gt;
</p>

<p>where ∂<sub>a</sub> denotes derivative with respect to parameter a.</p>

<h3>Numerical Derivatives</h3>

<p>Finite-difference approximation:</p>

<p style="text-align:center;">
f'(x) ≈ [f(x+h) - f(x-h)] / 2h + O(h²)
</p>

<h3>Fisher Matrix for Normalized Waveforms</h3>

<p>For ĥ = h / ||h||:</p>

<p style="text-align:center;">
Γ̃<sub>ab</sub> = (1/||h||²) [ &lt; A e<sup>-iφ</sup>(-i)∂<sub>a</sub>φ, A e<sup>-iφ</sup>(-i)∂<sub>b</sub>φ &gt; + &lt; ∂<sub>a</sub>A, ∂<sub>b</sub>A &gt; + cross terms ]
</p>

<p>Neglecting small cross terms:</p>

<p style="text-align:center;">
Γ̃<sub>ab</sub> ≈ 1 / (2 ||h||²) [ &lt; A ∂<sub>a</sub>φ, A ∂<sub>b</sub>φ &gt; + &lt; ∂<sub>a</sub>A, ∂<sub>b</sub>A &gt; ]
</p>

<hr>

<h2>Parameter Space</h2>

<h3>Intrinsic Parameters</h3>

<p>5-dimensional intrinsic parameter space:</p>
<ul>
  <li><strong>Chirp mass</strong> ℳ<sub>c</sub></li>
  <li><strong>Mass ratio</strong> η = m<sub>1</sub> m<sub>2</sub> / (m<sub>1</sub> + m<sub>2</sub>)²</li>
  <li><strong>Mass asymmetry</strong> δ = (m<sub>1</sub> - m<sub>2</sub>) / (m<sub>1</sub> + m<sub>2</sub>)</li>
  <li><strong>Reduced spin</strong> χ = (χ<sub>1</sub> + χ<sub>2</sub>) / 2 (assuming χ<sub>1</sub> = χ<sub>2</sub>)</li>
</ul>

<h3>Metric Projection</h3>

<p>The template-space metric is obtained by projecting out extrinsic parameters:</p>

<p style="text-align:center;">
g = Γ<sub>1</sub> - Γ<sub>2</sub> Γ<sub>3</sub><sup>-1</sup> Γ<sub>4</sub>
</p>

<p>where Γ<sub>1</sub>, Γ<sub>2</sub>, Γ<sub>3</sub>, Γ<sub>4</sub> are blocks of the Fisher matrix corresponding to intrinsic/extrinsic parameters.</p>

<hr>

<p><strong>Author:</strong> Tarun Kumar<br>
<strong>Affiliation:</strong> IIT Gandhinagar</p>
