---
tags:
  - probability-theory/stochastic-processes
aliases:
  - Non-stationary Poisson Process
  - Time-dependent Poisson Process
  - NHPP
status: good_enough
created: 2025-12-12 22:16
---
### Non-homogeneous Poisson Process
The **Nonhomogeneous Poisson Process** (NHPP) is a counting process $\{N(t), t \ge 0\}$ that generalizes the standard Poisson process by allowing the arrival rate to vary as a function of time, denoted by the intensity function $\lambda(t)$. Unlike the stationary Poisson process, the NHPP possesses **independent increments** but does **not** possess stationary increments.

**Axiomatic Definition**
The counting process $\{N(t), t \ge 0\}$ is a nonhomogeneous Poisson process with intensity function $\lambda(t), t \ge 0$ if:
1. $N(0) = 0$.
2. The process has **independent increments**.
3. $P(N(t+h) - N(t) \ge 2) = o(h)$.
4. $P(N(t+h) - N(t) = 1) = \lambda(t)h + o(h)$.

_Where:_
- $N(t)$: The total number of events that have occurred by time $t$.
- $\lambda(t)$: The instantaneous **intensity function** (or rate function) at time $t$.
- $o(h)$: Little-o notation, representing a function $f$ such that $\lim_{h \to 0} \frac{f(h)}{h} = 0$.

#### Fundamental Functions
The probabilistic behavior of the NHPP is governed by the integral of the intensity function, known as the **Mean Value Function**, denoted by $m(t)$.
$$m(t) = \int_0^t \lambda(s) \, ds$$
The number of events in any interval $(t, t+s]$ follows a Poisson distribution with a mean equal to the change in the mean value function over that interval:
$$P(N(t+s) - N(t) = n) = \frac{e^{-[m(t+s)-m(t)]} [m(t+s)-m(t)]^n}{n!}, \quad n \ge 0$$
_Where:_
- $m(t)$: The expected number of events in the interval $[0, t]$.
- $m(t+s) - m(t) = \int_t^{t+s} \lambda(y) \, dy$.

#### Interval Distributions (Waiting Times)
Unlike the homogeneous Poisson process, the interarrival times in an NHPP are **not** independent and are **not** identically distributed. The distribution of the time until the next event depends on the current time $t$.

**Waiting Time Reliability:**
The probability that no events occur in the interval $(t, t+s]$, effectively the probability that the waiting time $W$ for the next event exceeds $s$, is:
$$P(W > s | \text{current time } t) = P(N(t+s) - N(t) = 0) = e^{-\int_t^{t+s} \lambda(y) \, dy}$$
#### Properties & Intuition
- **Time-Varying Intensity:** The core utility of the NHPP is modeling systems where the likelihood of an event changes over time (e.g., traffic during rush hour vs. midnight).
- **Integration of Risk:** The probability of an event occurring across an interval is determined by the accumulated "risk" or intensity ($\int \lambda(t)$) over that specific window, rather than just the interval length.
- **Poisson Nature:** Despite the varying rate, the count of events in any disjoint interval remains Poisson distributed.
- **Relation to Homogeneous Process:** An NHPP can be viewed as a time-sampled or time-scaled homogeneous Poisson process. If one transforms the time scale using the mean value function $\tau = m(t)$, the resulting process on the $\tau$ scale is a homogeneous Poisson process with rate 1.

---

# Related
```dataviewjs
await dv.view("99_System/Scripts/tag_tables", dv.current());
```

### Direct Links to this document
```dataview
TABLE file.folder AS "Context"
FROM [[#]]
WHERE file.folder != "10_Concepts"
SORT file.folder ASC
```

