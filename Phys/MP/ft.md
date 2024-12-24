# Fourier Transforms

## 0. Sturm-Liouville Theory

Our matters of interest are:

(1) The conditions under which an ODE can be written as an eigenvalue equation with a self-adjoint (hermitian) operator.

(2) Methods for solving ODEs subject to boundary conditions.

(3) Properties of the solutions in (2).

The general eigenproblem characteristics of second-order differential equations are referred to as **Sturm-Liouville theory**, where the Hermitian operator $\mathcal{L}$ is expressed as:

$$
\begin{aligned}
\mathcal{L}(x) &= \frac{d}{dx}\left(p(x)\frac{d}{dx} \right)+(\lambda w(x)-q(x)) \\
\mathcal{L}y &= \lambda y
\end{aligned}
$$

Here, $p(x), q(x), w(x)$ are given functions, and $p(x) > 0$, $w(x) > 0$. $\lambda$ is a real discrete eigenvalue, and $y(x)$ is the eigenfunction, which must satisfy specific boundary conditions on the domain $[a,b]$:

1. **Dirichlet boundary conditions**: $y(a)$ and $y(b)$ are fixed to given values.
2. **Neumann boundary conditions**: The boundary terms vanish at the boundaries (e.g., $y'(a) + \alpha y(a) = 0$, $y'(b) + \beta y(b) = 0$).

Eigenfunctions in a Sturm-Liouville problem can be normalized by an appropriate constant, and eigenfunctions corresponding to different eigenvalues, $y_n(x)$ and $y_m(x)$, are orthogonal with respect to the weight function $w(x)$: $\int_a^b y_n(x)y_m(x)w(x)dx=0 \quad (\lambda_n \neq \lambda_m)$.

### Model of a Vibrating String

The motion of a vibrating string is described by the wave equation:

$$
\frac{\partial^2 u(x,t)}{\partial t^2}=c^2\frac{\partial^2 u(x,t)}{\partial x^2}, \quad c=\sqrt{\frac{T}{\mu}}
$$

Using separation of variables, $u(x,t) = X(x)T(t)$, the equation splits into two ODEs:

- $\frac{d^2T(t)}{dt^2} + \omega^2T(t) = 0$ (temporal equation)
- $\frac{d^2X(x)}{dx^2} + \lambda X(x) = 0, \quad \lambda = \frac{\omega^2}{c^2}$ (spatial equation, eigenvalue problem)

If the string is fixed at both ends, the boundary conditions are $u(0,t) = u(L,t) = 0$. Interpreted as a Sturm-Liouville problem, $X(0) = X(L) = 0$. This determines the normal modes and eigenfrequencies of the string. Solving the spatial equation yields eigenvalues $\lambda_n = \left(\frac{n\pi}{L}\right)^2, \quad n=1,2,3,\dots$, with corresponding eigenfrequencies $\omega_n = c\sqrt{\lambda_n} = \frac{n\pi c}{L}$. The eigenfunctions (standing waves) are $X_n(x) = \sin{\left(\frac{n\pi x}{L} \right)}$. Eigenfunctions corresponding to different modes are orthogonal: $\int_0^L X_m(x)X_n(x)dx = 0 \quad (m \neq n)$.

From a physical perspective, the string forms standing wave patterns at specific eigenfrequencies, which depend on the string length $L$, tension $T$, and mass density $\mu$. At specific nodes, the displacement is always zero.

## 1. Fourier Series

The Fourier series is defined as a representation of a function or signal as a series of sines and cosines:

$$
\begin{aligned}
f(x) &= \frac{a_0}{2} + \sum_{n=1}^\infty \left[a_n\cos{nx} + b_n\sin{nx}\right] \\
a_n &= \frac{1}{\pi} \int_0^{2\pi} f(s)\cos{ns}ds, \quad n=0,1,2,\dots \\
b_n &= \frac{1}{\pi} \int_0^{2\pi} f(s)\sin{ns}ds, \quad n=0,1,2,\dots
\end{aligned}
$$

From the form of the Fourier series, the imposed conditions are that $f(x)$ must have only a finite number of finite discontinuities and only a finite number of extreme values (maxima and minima) in $[0, 2\pi]$ (**Dirichlet conditions**). Such functions are called **piecewise regular**.

We can rewrite the equation as:

$$
\begin{aligned}
f(x) &= \sum_{n=1}^\infty c_ne^{inx}, \\
c_n &= \frac{1}{2}(a_n-ib_n), \quad c_{-n}=\frac{1}{2}(a_n+ib_n), \quad n>0, \quad c_0 = \frac{1}{2}a_0
\end{aligned}
$$

Typically, $f(x)$ is a periodic continuous function, decomposed into frequency components via the Fourier series.

The Sturm-Liouville theory forms an orthogonal basis in function space. Thus, any function $f(x)$ can be represented similarly to a Fourier series using the eigenfunctions $y_n(x)$ of a Sturm-Liouville problem:

$$
f(x)=\sum_{n=1}^\infty c_ny_n(x), \quad \text{where} \quad c_n=\frac{\int_a^b f(x)y_n(x)w(x)dx}{\int_a^b y_n(x)^2w(x)dx}
$$

For instance, in the vibration of a string, the solution $u(x,t)$ is expressed as a linear combination of eigenfunctions $X_n(x)$:

$$
u(x,t)=\sum_{n=1}^\infty \left[ A_n\cos{\omega_nt}+B_n\sin{\omega_nt}\right]X_n(x)
$$

Here, $A_n$ and $B_n$ are Fourier coefficients.


## 2. (Continuous) Fourier Transform

The eigenvalue problems described above generate discrete eigenvalues under finite boundary conditions, which can be represented by Fourier series. However, when a string is infinitely long or boundary conditions are absent, the solution to the wave equation has a continuous frequency spectrum. In such cases, the **Fourier transform** is used, typically defined as:

$$
g(\omega) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^\infty f(t)e^{i\omega t}dt
$$

For example, the wave equation describing the vibration of an infinitely long string is:

$$
u(x,t) = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^\infty \hat{u}(k,0)e^{i(kx-\omega t)}dk
$$

Here, $\hat{u}(k,0)$ is the Fourier transform of the initial condition $u(x,0)$, and $k = \frac{2\pi}{\lambda}$ is the wavenumber, satisfying the relation $\omega = c|k|$. The Fourier transform converts oscillations occurring in space and time into the frequency domain, allowing analysis of each component.

In the large-$n$ limit, the delta function $\delta_n(t) = \frac{1}{2\pi} \int_{-n}^n e^{i\omega t}d\omega$ is especially useful in Fourier analysis and helps derive results for Fourier integrals:

$$
f(x) = \frac{1}{2\pi} \int_{-\infty}^\infty e^{-i\omega x}d\omega \int_{-\infty}^\infty f(t)e^{i\omega t}dt
$$

### Inverse Fourier Transform

The inverse Fourier transform is given by:

$$
\begin{aligned}
g(\omega) &= \frac{1}{2\pi} \int_{-\infty}^\infty f(t)e^{i\omega t}dt, \\
f(t) &= \frac{1}{2\pi} \int_{-\infty}^\infty g(\omega)e^{-i\omega t}d\omega
\end{aligned}
$$

### Transforms in 3D Space

In three-dimensional space, the Fourier transform and its inverse are expressed as:

$$
\begin{aligned}
g(\mathbf{k}) &= \frac{1}{(2\pi)^{3/2}} \int f(\mathbf{r})e^{i\mathbf{k \cdot r}}d^3r, \\
f(\mathbf{r}) &= \frac{1}{(2\pi)^{3/2}} \int g(\mathbf{k})e^{-i\mathbf{k \cdot r}}d^3k
\end{aligned}
$$

### Properties of Fourier Transform

Some key properties of the Fourier transform are:

$$
\begin{aligned}
\left[f(\mathbf{r-R})\right]^T(\mathbf{k}) &= e^{i\mathbf{k \cdot R}}g(\mathbf{k}) \quad \text{: translation}, \\
\left[f(\alpha \mathbf{r})\right]^T(\mathbf{k}) &= \frac{1}{\alpha^3}g(\alpha^{-1}\mathbf{k}) \quad \text{: change of scale}, \\
\left[f(-\mathbf{r})\right]^T(\mathbf{k}) &= g(-\mathbf{k}) \quad \text{: sign change}, \\
\left[f^*(-\mathbf{r})\right]^T(\mathbf{k}) &= g^*(\mathbf{k}) \quad \text{: complex conjugation}, \\
\left[\nabla f(\mathbf{r})\right]^T(\mathbf{k}) &= -i\mathbf{k}g(\mathbf{k}) \quad \text{: gradient}, \\
\left[\nabla^2 f(\mathbf{r})\right]^T(\mathbf{k}) &= -k^2g(\mathbf{k}) \quad \text{: Laplacian}
\end{aligned}
$$

## 3. Fourier Convolution Theorem

The operation of combining two functions $f(x)$ and $g(x)$ to produce a new function is called convolution, defined as:

$$
\begin{aligned}
(f*g)(x) &= \frac{1}{2\pi} \int_{-\infty}^\infty g(y)f(x-y)dy, \\
(f*g)(\mathbf{r}) &= \frac{1}{(2\pi)^{3/2}} \int_{-\infty}^\infty g(\mathbf{r'})f(\mathbf{r-r'})d^3r' \quad \text{(in 3D)}
\end{aligned}
$$

## 4. Signal-Processing Applications

Signal-processing applications of Fourier analysis are diverse, including filtering, compression, and spectral analysis.

## 5. Discrete Fourier Transform

The Fourier series deals with periodic continuous functions and consists of infinite frequency components. The Discrete Fourier Transform (DFT), on the other hand, transforms finite-length sampled data into its frequency components. For a data length of $N$, only $N$ frequency components are calculated, making it widely used in digital signal processing.

## 6. Laplace Transform

The Laplace transform is defined as:

$$
F(s) = \int_0^\infty f(t)e^{-st}dt \quad \text{where} \quad s = \sigma + i\omega
$$

The Fourier transform is a special case of the Laplace transform with $\sigma = 0$.

### Properties of Laplace Transformation

The Laplace transform has various useful properties, including linearity, time-shifting, and frequency-shifting.

### Inverse Laplace Transformation

The inverse Laplace transform allows retrieving the original function from its Laplace transform.

## 7. Fractional Fourier Transform

The fractional Fourier transform generalizes the Fourier transform, providing intermediate representations between the time and frequency domains.

## 8. Fast Fourier Transform

The Fast Fourier Transform (FFT) is an efficient algorithm for computing the DFT, significantly reducing computational complexity from $O(N^2)$ to $O(N\log N)$. It is crucial in modern signal processing and numerical analysis.

## 9. Quantum Fourier Transform

The Quantum Fourier Transform (QFT) is the quantum analog of the classical Fourier transform, used in quantum algorithms like Shor's factoring algorithm.

## 10. Fourier Transform Spectroscopy

Fourier transform spectroscopy leverages the Fourier transform to analyze the spectral components of signals, widely applied in fields such as optics and remote sensing.

---

## References

- [Fourier Transform](https://en.wikipedia.org/wiki/Fourier_transform)
- [But what is a Fourier series? From heat flow to drawing with circles](https://youtu.be/r6sGWTCMz2k?si=7qbcgFs99zq7Rqel)
- [But what is the Fourier Transform? A visual introduction.](https://youtu.be/spUNpyF58BY?si=ERk6tVKPGpCU2s79)
- [But what is a convolution?](https://youtu.be/KuXjwB4LzSA?si=fY-nNP6YwLxpBnsn)
- [Convolutions | Why X+Y in probability is a beautiful mess](https://youtu.be/IaSGqQa5O-M?si=nc6fMDvYEkgGmeRk)
- [The Fast Fourier Transform (FFT): Most Ingenious Algorithm Ever?](https://youtu.be/h7apO7q16V0?si=1LbfkI8O8BAHTUBK)
- *Mathematical Methods for Physicists*, Arfken
