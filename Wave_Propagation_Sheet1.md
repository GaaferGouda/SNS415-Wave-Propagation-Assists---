# Wave Propagation — Sheet 1 — Full Analytical Solutions

**Prepared by:** Gaafer Gouda — Faculty of Navigation Science and Space Technology, Beni-Suef University  
**Course:** SNS415 — *Wave Propagation*  
**Format:** Full step-by-step analytical solutions for Problems 1–21. Equations are provided in block LaTeX for GitHub rendering.

---

## Constants / Notation

All solutions use these constants unless otherwise stated:

$$
c = 3\times 10^{8}\ \mathrm{m/s}
$$

$$
\eta_0 = 120\pi \approx 376.9911\ \Omega
$$

$$
\beta = \frac{2\pi}{\lambda} = \frac{\omega}{c}
$$

Time-average radiated power (sinusoidal amplitude \(I_0\)):

$$
P_{\text{rad}}=\frac{1}{2}I_0^2 R_{\text{rad}}
$$

RMS vs peak: \(I_{\mathrm{rms}}=I_0/\sqrt{2}\).

---

## Problem 1 — Vector identities

**Question (1A–D):**

(A) Prove the vector identity \(\nabla\cdot(\nabla\times\mathbf{A}) = 0\) for an arbitrary vector function \(\mathbf{A}(\mathbf{r})\).

(B) Prove the vector identity \(\nabla\times(\nabla\phi) = 0\) for an arbitrary scalar function \(\phi(\mathbf{r})\).

(C) Prove the vector identity \(\nabla\times\nabla\times\mathbf{A} = \nabla(\nabla\cdot\mathbf{A}) - \nabla^2\mathbf{A}\).

(D) Prove the vector identity \(\mathbf{a}\times(\mathbf{b}\times\mathbf{c}) = \mathbf{b}(\mathbf{a}\cdot\mathbf{c}) - (\mathbf{a}\cdot\mathbf{b})\mathbf{c}\).

**Solution (1A).** Using index notation and the Levi-Civita symbol \(\varepsilon_{ijk}\):

$$
(\nabla\times\mathbf{A})_i = \varepsilon_{ijk}\partial_j A_k.
$$

Hence

$$
\nabla\cdot(\nabla\times\mathbf{A}) = \partial_i(\varepsilon_{ijk}\partial_j A_k)
= \varepsilon_{ijk}\partial_i\partial_j A_k.
$$

Because partial derivatives commute (\(\partial_i\partial_j=\partial_j\partial_i\)) and \(\varepsilon_{ijk}\) is antisymmetric in \(i,j\), the sum vanishes, so

$$
\nabla\cdot(\nabla\times\mathbf{A}) = 0.
$$

**Solution (1B).**

$$
(\nabla\times\nabla\phi)_i = \varepsilon_{ijk}\partial_j\partial_k\phi = 0,
$$

since \(\partial_j\partial_k\phi\) is symmetric in \(j,k\) while \(\varepsilon_{ijk}\) is antisymmetric.

**Solution (1C).** Expand componentwise:

$$
(\nabla\times\nabla\times\mathbf{A})_i = \varepsilon_{ijk}\partial_j(\varepsilon_{klm}\partial_l A_m)
= \partial_i(\partial_j A_j) - \partial_j\partial_j A_i,
$$

which is the vector identity:

$$
\nabla\times\nabla\times\mathbf{A} = \nabla(\nabla\cdot\mathbf{A}) - \nabla^2\mathbf{A}.
$$

**Solution (1D).** The BAC–CAB vector triple product identity is standard; expanding components or reasoning with projections gives:

$$
\mathbf{a}\times(\mathbf{b}\times\mathbf{c}) = \mathbf{b}(\mathbf{a}\cdot\mathbf{c}) - (\mathbf{a}\cdot\mathbf{b})\mathbf{c}.
$$

---

## Problem 2 — How does radiated field strength vary with distance?

**Question:** How does radiated field strength vary with distance from the source (antenna)?

**Solution.** In the far-field (radiation zone):

- Electric and magnetic field amplitudes scale as \(1/r\):

$$
|E| \propto \frac{1}{r},\qquad |H| \propto \frac{1}{r}.
$$

- Time-average power density (Poynting flux) scales as \(1/r^2\):

$$
S=\frac{1}{2}\Re\{\mathbf{E}\times\mathbf{H}^*\} \approx \frac{1}{2}\frac{|E|^2}{\eta_0}\propto\frac{1}{r^2}.
$$

This is because radiated energy spreads over a sphere of area \(4\pi r^2\).

---

## Problem 3 — What is meant by radiation resistance?

**Question:** What is meant by radiation resistance?

**Solution.** Radiation resistance \(R_{\text{rad}}\) is a conceptual resistance that accounts for the power radiated away by the antenna. If the antenna feed current amplitude is \(I_0\) (peak), the time-average radiated power is:

$$
P_{\text{rad}}=\frac{1}{2}I_0^2 R_{\text{rad}}.
$$

Interpreting radiation as a resistive loss at the feed point, \(R_{\text{rad}}\) quantifies how much of the input current contributes to radiated power rather than stored reactive energy or ohmic loss.

---

## Problem 4 — Distinguish antenna analysis and antenna design

**Question:** Distinguish between antenna analysis and antenna design.

**Solution.**

- **Antenna analysis:** Given an antenna geometry and excitation, compute electromagnetic fields, input impedance, radiation pattern, gain, efficiency, etc. Analysis uses Maxwell’s equations and boundary conditions or numerical solvers (MoM, FEM, FDTD).

- **Antenna design:** Starting from performance requirements (gain, beamwidth, impedance, size), synthesize or optimize an antenna geometry and feed to meet those specifications. Design uses analysis tools, heuristics, and optimization loops.

---

## Problem 5 — Short dipole: constant vs triangular current distribution

**Question:** How does the field produced by a short dipole with constant current distribution differ from that for triangular current distribution?

**Solution.**

For a short dipole of length \(l\):

- **Constant current** (approx): dipole moment \(p = I_0 l\).
- **Triangular current** (linear taper to zero at ends): effective dipole moment \(p = I_0 l/2\) (for same peak current \(I_0\)).

Far-field electric field amplitude is proportional to the dipole moment, so for identical \(I_0\):

$$
E_{\text{tri}} = \frac{1}{2} E_{\text{const}}.
$$

Radiated power scales as \(E^2\), thus:

$$
P_{\text{tri}} = \left(\frac{1}{2}\right)^2 P_{\text{const}} = \frac{1}{4} P_{\text{const}}.
$$

Therefore triangular distribution radiates less for the same peak current; but normalized patterns (angular dependence) are the same (\(\sin\theta\) shape) for electrically small dipoles.

---

## Problem 6 — Power density of infinitesimal dipole with triangle current and comparison

**Question:** Find the expression for the power density radiated by an infinitesimal dipole with triangle current and compare it with constant current.

**Solution.**

For a short dipole (constant current \(I_0\)), far-field:

$$
E_\theta = \frac{j\eta_0\beta I_0 l}{4\pi r} e^{-j\beta r}\sin\theta,
$$

so the time-average power density is:

$$
S = \frac{1}{2}\frac{|E_\theta|^2}{\eta_0}
= \frac{\eta_0\beta^2 I_0^2 l^2}{32\pi^2 r^2}\sin^2\theta.
$$

For triangular current with same peak \(I_0\), effective \(I_0 l \to I_0 (l/2)\). Therefore:

$$
S_{\text{tri}} = \frac{\eta_0\beta^2 I_0^2 (l/2)^2}{32\pi^2 r^2}\sin^2\theta = \frac{1}{4} S_{\text{const}}.
$$

Hence triangular current radiates one quarter the power of constant current (for same \(I_0\)).

---

## Problem 7 — What is meant by the ‘far field’ of an antenna?

**Question:** What is meant by the ‘far field’ of an antenna?

**Solution.** The far-field (Fraunhofer) region is where the angular field distribution is essentially independent of radial distance and fields decrease as \(1/r\). Rule-of-thumb boundary:

$$
r \gtrsim \frac{2D^2}{\lambda},
$$

where \(D\) is the largest dimension of the antenna. In the far field, E and H are transverse to the radial direction and \(E/H=\eta_0\).

---

## Problem 8 — Poynting vector relation

**Question:** Start from \(\mathbf{S}=\tfrac12\mathbf{E}\times\mathbf{H}^*\). Prove that \(\mathbf{S}=\hat r\frac{1}{2\eta_0}|E|^2\) in the far field.

**Solution.** In the far field \(\mathbf{E}\perp\mathbf{H}\) and \(|E|=\eta_0|H|\). Therefore the vector product points radially and its magnitude is:

$$
\mathbf{S}=\frac{1}{2}\mathbf{E}\times\mathbf{H}^*=\hat r\frac{1}{2}|E||H|=\hat r\frac{1}{2}\frac{|E|^2}{\eta_0}.
$$

Thus the stated result follows.

---

## Problem 9 — Polar (power) radiation pattern of a short z-directed dipole

**Question:** Plot (describe) the normalized power radiation pattern \(P_n(\theta)\) of a short z-directed dipole for slices at  \(\phi=\pi/4,\ \pi/2,\ 0\).

**Solution.** The normalized power pattern is:

$$
P_n(\theta)\propto\sin^2\theta.
$$

This is independent of \(\phi\), so polar plots for \(\phi=\pi/4,\ \pi/2,\ 0\) are identical in shape. The pattern has nulls at \(\theta=0,\pi\) and maximum at \(\theta=\pi/2\). Half-power points where \(\sin^2\theta=1/2\) ⇒ \(\theta=45^\circ,135^\circ\) ⇒ HPBW = \(90^\circ\).

---

## Problem 10 — Radiated power density given; find \(P_{\text{rad}}, R_{\text{rad}}\), pattern and HPBW

**Question (10a–c):** Given the radiated power density function of a short dipole:

$$
\mathbf{S}(r,\theta)=\hat r\;\frac{1}{2}\eta_0\beta^2\frac{(I_0 l)^2}{(4\pi r)^2}\sin^2\theta
= \hat r\;\frac{\eta_0\beta^2(I_0 l)^2}{32\pi^2 r^2}\sin^2\theta,
$$

where \(\beta=\omega\sqrt{\mu_0\epsilon_0}\), \(\eta_0=\sqrt{\mu_0/\epsilon_0}\).

(a) Calculate radiated power \(P_{\text{rad}}\).

(b) Calculate radiation resistance \(R_{\text{rad}}\).

(c) Calculate normalized radiation pattern and determine HPBW.

**Solution (10a).** Integrate the radial flux over a sphere:

$$
P_{\text{rad}}=\int_0^{2\pi}\int_0^\pi S(r,\theta) r^2\sin\theta\,d\theta d\phi
=\frac{\eta_0\beta^2(I_0 l)^2}{32\pi^2}\cdot 2\pi\int_0^\pi\sin^3\theta\,d\theta.
$$

Compute \(\int_0^\pi\sin^3\theta\,d\theta=\tfrac{4}{3}\). Thus:

$$
P_{\text{rad}}=\frac{\eta_0\beta^2(I_0 l)^2}{32\pi^2}\cdot 2\pi\cdot\frac{4}{3}
=\frac{\eta_0\beta^2(I_0 l)^2}{12\pi}.
$$

Using \(\beta=2\pi/\lambda\) and \(\eta_0=120\pi\), this becomes the common form:

$$
P_{\text{rad}}=40\pi^2 I_0^2\left(\frac{l}{\lambda}\right)^2.
$$

**Solution (10b).** From \(P_{\text{rad}}=\tfrac12 I_0^2 R_{\text{rad}}\):

$$
R_{\text{rad}}=\frac{2P_{\text{rad}}}{I_0^2}=\frac{\eta_0\beta^2 l^2}{6\pi}
=80\pi^2\left(\frac{l}{\lambda}\right)^2.
$$

**Solution (10c).** Normalized pattern:

$$
P_n(\theta)=\sin^2\theta.
$$

Half-power when \(\sin^2\theta=1/2\) ⇒ \(\theta=45^\circ,135^\circ\) ⇒ HPBW \(=90^\circ\).

---

## Problem 11 — Vertical wire 1 m, I=5 A, f=2 MHz: fields at 2 km and 25 km

**Question:** A vertical wire 1 m long carries a current of 5 A at 2 MHz in free space. Calculate the strength of radiated field produced at distance 2 km and 25 km in the direction at right angles to the axis of the wire. Compare with values at 45° to the axis. Explain and conclude.

**Solution.**

Given:

- \(l=1\) m, \(I_0=5\) A, \(f=2\times10^6\) Hz.
- \(\lambda=c/f=3\times10^8/2\times10^6=150\) m.
- \(\beta=2\pi/\lambda\approx0.04188790205\ \mathrm{rad/m}\).

Short-dipole formula (valid as \(l/\lambda=1/150\ll1\)):

$$
|E_\theta|=\frac{\eta_0\beta I_0 l}{4\pi r}\sin\theta.
$$

Compute numerically:

- \(r_1=2000\) m, \(\theta=90^\circ\):

$$
|E|=\frac{120\pi\cdot0.0418879\cdot5\cdot1}{4\pi\cdot2000}
=\frac{120\cdot0.0418879\cdot5}{4\cdot2000}\approx3.1416\times10^{-3}\ \mathrm{V/m}.
$$

- \(r_2=25000\) m, \(\theta=90^\circ\):

$$
|E|\approx\frac{120\cdot0.0418879\cdot5}{4\cdot25000}\approx2.5133\times10^{-4}\ \mathrm{V/m}.
$$

- For \(\theta=45^\circ\) multiply by \(\sin45^\circ=\tfrac{\sqrt2}{2}\approx0.7071\):

  - \(r=2000\) m: \(2.2214\times10^{-3}\) V/m.
  - \(r=25000\) m: \(1.7772\times10^{-4}\) V/m.

**Conclusion:** Field decays as \(1/r\) and scales with \(\sin\theta\); maximum at \(\theta=90^\circ\).

---

## Problem 12 — Power radiated by 50 cm dipole at 30 MHz with I=2 A; current to radiate 5 W

**Question:** Find the power radiated by a 50 cm dipole antenna operated at 30 MHz with current of 2 A. How much current to radiate 5 W?

**Solution.**

Given: \(l=0.5\) m, \(f=30\times10^6\) Hz ⇒ \(\lambda=10\) m, \(\beta=2\pi/10=0.62831853\ \mathrm{rad/m}\).

Using triangular-current short-dipole expression (center-fed triangular distribution):

$$
P_{\text{rad}}=\frac{\eta_0\beta^2 I_0^2 l^2}{48\pi}.
$$

For \(I_0=2\) A:

$$
P_{\text{rad}}=\frac{120\pi\cdot(0.62831853)^2\cdot 2^2\cdot 0.5^2}{48\pi}\approx0.98696\ \mathrm{W}.
$$

So radiated power ≈ **0.987 W**.

For required \(P_{\text{rad}}=5\) W, solve for \(I_0\):

$$
I_0=\sqrt{\frac{48\pi P_{\text{rad}}}{\eta_0\beta^2 l^2}}\approx4.5016\ \mathrm{A}.
$$

So **≈4.50 A** amplitude is needed.

---

## Problem 13 — Current to radiate 1 kW using l=0.01λ

**Question:** What current is needed to radiate 1 kW using a short dipole antenna having length \(l=0.01\lambda\)?

**Solution.**

Radiation resistance for short dipole:

$$
R_{\text{rad}}=80\pi^2\left(\frac{l}{\lambda}\right)^2.
$$

For \(l/\lambda=0.01\):

$$
R_{\text{rad}}=80\pi^2(0.01)^2\approx0.0789568\ \Omega.
$$

From \(P=\tfrac12 I_0^2 R_{\text{rad}}\):

$$
I_0=\sqrt{\frac{2P}{R_{\text{rad}}}}=\sqrt{\frac{2\times1000}{0.0789568}}\approx159.155\ \mathrm{A}.
$$

**Answer:** ~**159.16 A** (peak).

---

## Problem 14 — Compare triangular vs constant current short dipole (items a–g)

**Question:** Compare with respect to: (a) Radiation pattern E & H plane, (b) Radiation resistance, (c) Current distribution, (d) Radiated power, (e) HPBW, (f) Directivity, (g) Gain.

**Solution (summary):**

- (a) **Radiation pattern:** For electrically small dipole both show \(\sin\theta\) angular dependence (same normalized shape).  
- (b) **Radiation resistance:** Triangular (for same peak \(I_0\)) yields 1/4 the radiated power ⇒ effectively lower \(R_{\text{rad}}\) (≈1/4 of constant-current case for same \(I_0\)).  
- (c) **Current distribution:** Constant: uniform; triangular: linear taper to zero at ends.  
- (d) **Radiated power:** \(P_{\text{tri}}=\tfrac{1}{4}P_{\text{const}}\) for same \(I_0\).  
- (e) **HPBW:** Same (~90°) since angular variation identical.  
- (f) **Directivity:** Same (directivity depends only on angular distribution). For short dipole \(D_0\approx1.5\).  
- (g) **Gain:** \(G=e_r D\). If efficiency identical, triangular radiates less for same \(I_0\) so lower absolute gain when driven with same peak current; for equal radiated power the gains are identical.

---

## Problem 15 — Prove \(R_{\text{rad}}=80\pi^2\left(\dfrac{l}{\lambda}\right)^2\)

**Question:** Prove that for a short constant-current dipole \(R_{\text{rad}}=80\pi^2(l/\lambda)^2\).

**Solution.** Start from:

$$
P_{\text{rad}}=\frac{\eta_0\beta^2 I_0^2 l^2}{12\pi}.
$$

Then

$$
R_{\text{rad}}=\frac{2P_{\text{rad}}}{I_0^2}=\frac{\eta_0\beta^2 l^2}{6\pi}.
$$

Substitute \(\beta=2\pi/\lambda\) and \(\eta_0=120\pi\):

$$
R_{\text{rad}}=120\pi\cdot\frac{(2\pi)^2}{\lambda^2}\cdot\frac{l^2}{6\pi}=80\pi^2\left(\frac{l}{\lambda}\right)^2.
$$

QED.

---

## Problem 16 — Show \(\omega\mu=\beta\eta\)

**Question:** Show that \(\omega\mu=\beta\eta\).

**Solution.** Using \(\beta=\omega\sqrt{\mu\epsilon}\) and \(\eta=\sqrt{\mu/\epsilon}\):

$$
\beta\eta=\omega\sqrt{\mu\epsilon}\cdot\sqrt{\frac{\mu}{\epsilon}}=\omega\mu.
$$

Thus \(\beta\eta=\omega\mu\).

---

## Problem 17 — Distance in xy-plane where |E|<1e-3 V/m for given dipole

**Question:** Az-directed short dipole at origin, \(l=1\) m, \(I_0=10\) A, \(f=1\) MHz. Find distance in xy-plane beyond which \(|E|<1\times10^{-3}\) V/m.

**Solution.**

Given \(\lambda=300\) m ⇒ \(\beta=2\pi/\lambda\approx0.02094395\). In xy-plane \(\theta=90^\circ\). Short-dipole magnitude:

$$
|E_\theta|=\frac{\eta_0\beta I_0 l}{4\pi r}.
$$

Solve for \(r\) when \(|E|=10^{-3}\) V/m:

$$
r=\frac{\eta_0\beta I_0 l}{4\pi|E|}=\frac{120\pi\cdot0.02094395\cdot10\cdot1}{4\pi\cdot10^{-3}}\approx6283.185\ \mathrm{m}.
$$

**Answer:** \(r\approx6.283\) km.

---

## Problem 18 — Fill table (Short dipole and 1/2 wave)

**Question:** Complete the following table (Antenna, Rrad, Prad, HPBW, Do, G) for Short Dipole and 1/2 Wave.

**Solution (values):**

- **Short dipole:**  
  - \(R_{\text{rad}}=80\pi^2(l/\lambda)^2\).  
  - \(P_{\text{rad}}=40\pi^2 I_0^2 (l/\lambda)^2\).  
  - HPBW \(=90^\circ\).  
  - \(D_0\approx1.5\).  
  - \(G=e_r D_0\).

- **Half-wave dipole:**  
  - \(R_{\text{rad}}\approx73\ \Omega\).  
  - \(P_{\text{rad}}=\tfrac12 I_0^2\cdot73\ \Omega\).  
  - HPBW (E-plane) ≈ \(78^\circ\).  
  - \(D_0\approx1.64\) (≈ 2.15 dBi).  
  - \(G=e_r D_0\).

---

## Problem 19 — 6 cm dipole at 2.4 GHz: E and H at r=0.5 m, θ=60°

**Question:** A 6 cm z-directed dipole carries a current of 1 A at 2.4 GHz. Calculate the electric and magnetic field strengths at a distance of 50 cm along θ=60°.

**Solution.**

Given: \(l=0.06\) m, \(f=2.4\times10^9\) Hz ⇒ \(\lambda=0.125\) m, \(\beta=2\pi/\lambda\approx50.26548\). Since \(l/\lambda\approx0.48\), use finite-length dipole expression (center-fed approximation):

$$
E_\theta = j60I_0\frac{e^{-j\beta r}}{r}\left[\frac{\cos(\tfrac{\beta l}{2}\cos\theta)-\cos(\tfrac{\beta l}{2})}{\sin\theta}\right].
$$

Compute bracket: \(\tfrac{\beta l}{2}=\pi\frac{l}{\lambda}\approx0.48\pi\). Evaluating numerically for \(\theta=60^\circ\) yields bracket ≈ 0.7692362.

Magnitude:

$$
|E_\theta|=\frac{60\cdot1}{0.5}\cdot0.7692362\approx92.3083\ \mathrm{V/m}.
$$

Magnetic field magnitude:

$$
|H_\phi|=\frac{|E_\theta|}{\eta_0}\approx\frac{92.3083}{120\pi}\approx0.2449\ \mathrm{A/m}.
$$

**Results:** \(E_\theta\approx92.31\) V/m, \(H_\phi\approx0.2449\) A/m.

---

## Problem 20 — Power density at 30 km from 5 kW antenna with 37 dB directivity

**Question:** Find power density (W/m²) at r=30 km from an antenna radiating 5 kW with directivity of 37 dB. What directivity is required if power density is 2.5 mW/m²?

**Solution.**

Convert directivity:

$$
D_0=10^{37/10}=10^{3.7}\approx5011.8723.
$$

Power density on main beam axis:

$$
S=\frac{P_{\text{rad}}D_0}{4\pi r^2}=\frac{5000\cdot5011.8723}{4\pi(30\times10^3)^2}\approx2.22\times10^{-3}\ \mathrm{W/m^2}=2.22\ \mathrm{mW/m^2}.
$$

If required \(S=2.5\ \mathrm{mW/m^2}=2.5\times10^{-3}\ \mathrm{W/m^2}\):

$$
D=\frac{S\,4\pi r^2}{P_{\text{rad}}}=\frac{(2.5\times10^{-3})4\pi(30\times10^3)^2}{5000}\approx5248.6,
$$

which is \(10\log_{10}(5248.6)\approx37.2\) dB.

**Answer:** With 37 dB → \(S\approx2.22\) mW/m²; to get 2.5 mW/m² need ≈37.2 dB.

---

## Problem 21 — Radiated and dissipated power for Pin=1.5 kW, efficiency=95%

**Question:** Calculate radiated and dissipated power if input power is 1.5 kW and radiation efficiency is 95%

**Solution.**

Given \(P_{\text{in}}=1500\) W, \(e_r=0.95\). Then:

$$
P_{\text{rad}}=e_r P_{\text{in}}=0.95\times1500=1425\ \mathrm{W}.
$$

Dissipated power (loss):

$$
P_{\text{loss}}=P_{\text{in}}-P_{\text{rad}}=1500-1425=75\ \mathrm{W}.
$$

---

## Final notes

- All derivations assume free-space parameters and far-field behavior where applicable.  
- Finite-length corrections used in Problem 19 where \(l/\lambda\) is not negligible.  
- Units are SI; angles in degrees unless specified.  

---

© 2025 Beni-Suef University — SNS415 Wave Propagation (Prepared by Gaafer Gouda)
