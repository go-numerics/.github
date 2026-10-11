<p align="center"><img src="https://raw.githubusercontent.com/go-numerics/brand/main/social/go-numerics.png" alt="go-numerics" width="720"></p>

# go-numerics

🌐 **[Website](https://go-numerics.github.io)** · 📚 **[Documentation](https://go-numerics.github.io/docs/)**

**Numerical methods in pure Go (CGO=0): optimisation and root finding, quadrature and ODE solvers, special functions — on go-ndarray.**

Each library ports reference algorithms (MINPACK, L-BFGS-B, QUADPACK, the
Runge–Kutta, Radau and BDF solvers, Cephes and Boost.Math) statement by
statement, and its tests replay recorded answers: SciPy 1.18.1 runs for
`optimize` and `integrate`, with the netlib Fortran as a second oracle, and
[mpmath](https://mpmath.org) at high precision for `special`, with SciPy
measured on the same points. Where the Go code is slower than the reference,
the documentation says so.

```go
r, err := integrate.Quad(func(x float64) float64 { return math.Log(x) / math.Sqrt(x) }, 0, 1, nil)
// r.Value = -4, r.AbsErr = 2.3e-13, r.NEval = 315

root, _ := optimize.Brentq(func(x float64) float64 { return x*x*x - 2*x - 5 }, 2, 3, nil)
// root.Root = 2.094551481542…, 7 iterations

fmt.Println(special.Erfc(10)) // 2.088487583762545e-45
```

## Repositories

| Repo | What it is |
|------|------------|
| [**optimize**](https://github.com/go-numerics/optimize) | minimisation (Nelder–Mead, Powell, CG, BFGS, Newton-CG, L-BFGS-B), scalar and system roots, nonlinear least squares, curve fitting with covariance, linear programming |
| [**integrate**](https://github.com/go-numerics/integrate) | adaptive quadrature (QUADPACK), fixed and sample rules, multiple integrals, initial value problems (RK45, RK23, DOP853, Radau, BDF, stiffness switching) |
| [**special**](https://github.com/go-numerics/special) | gamma, beta, error and normal functions, incomplete gamma and beta and their inverses, Bessel, zeta, elliptic integrals, with an element-wise layer over go-ndarray |
| [**docs**](https://github.com/go-numerics/docs) | the documentation site (Hugo + Hextra), served at [/docs/](https://go-numerics.github.io/docs/) |
| [**go-numerics.github.io**](https://github.com/go-numerics/go-numerics.github.io) | the landing page (Hugo) |
| [**brand**](https://github.com/go-numerics/brand) | logo, icons and social images |

Every library needs Go 1.27.2 or later. It is part of an ecosystem with
[go-ndarray](https://github.com/go-ndarray/ndarray) (N-dimensional arrays),
[go-plot](https://github.com/go-plot/plot) (figures),
[go-dataframe](https://github.com/go-dataframe/dataframe) (labelled tables) and
[go-notebook](https://github.com/go-notebook/notebook) (Go notebooks).
