# Press Line Load & Nip Pressure — Calculations

If the nip is applied by two pneumatic cylinders:

\[
F_{\text{total}} = n \cdot \frac{\pi d^2}{4} \cdot P, \qquad
N' = \frac{F_{\text{total}}}{w}, \qquad
p \approx \frac{N'}{a}
\]

- \( n \): number of cylinders (typ. 2)  
- \( d \): bore (m)  
- \( P \): pressure (Pa) — 5 bar = \(5 \times 10^5\) Pa  
- \( w \): effective press width (m), \( a \): nip contact length (m)

**Examples at 5 bar, \(w = 0.33\) m, \(n = 2\):**

| Bore \(d\) | \(F_{\text{total}}\) (N) | \(N'\) (N·m⁻¹) |
|---:|---:|---:|
| 32 mm | 804 | 2,437 |
| 50 mm | 1,963 | 5,950 |
| 63 mm | 3,117 | 9,446 |
| 80 mm | 5,027 | 15,232 |
| **83 mm** | **≈ 5,445** | **≈ 16,500** |

> To reach **\(N' \approx 16{,}500\;N·m^{-1}\)** at 5 bar, use ~**two 83 mm** bores (or higher pressure with smaller bores).  
> For \( a = 5\) mm, \( p \approx 3.3\) MPa. Increase \(a\) or reduce \(N′\) to lower pressure.

## Safety
- Guard the nip; interlocks where practical.  
- Regulator + gauge; **LOTO** before maintenance.  
- Vent air; verify zero stored energy.
