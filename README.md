# Readme

Below is an implementation of a Companion Arbiter PUF (CAR-PUF).

## What is an Arbiter PUF?

An Arbiter PUF is a chain of \(k\) multiplexers, each of which either swaps the lines or keeps them intact, depending on the challenge bit fed into that multiplexer. The multiplexers each have delays that are hard to replicate but consistent. Let \(t_u\) and \(t_l\) respectively denote the time for the upper and lower signals to reach the finish line, and let Δ = \(t_u - t_l\) denote the difference in the timings. Note that Δ can be negative or positive. Assume that \(t_u = t_l\) never happens, i.e., Δ is never exactly zero. If the upper signal reaches the finish line first, i.e., Δ < 0, the response is 0; else if the lower signal reaches first, i.e., Δ > 0, the response is 1.

---

![image](https://github.com/user-attachments/assets/90890f82-0a64-4120-bffd-787a9f83c9d4)


We will create a PUF using multiple arbiter PUFs and call it a Companion Arbiter PUF (CAR-PUF for short). A CAR-PUF uses 2 arbiter PUFs – a working PUF and a reference PUF, as well as a secret threshold value τ > 0. Given a challenge, it is fed into both the working PUF and reference PUF, and the timings for the upper and lower signals for both PUFs are measured. Let Δw and Δr be the differences in timings experienced for the two PUFs on the same challenge. The response to this challenge is 0 if |Δw - Δr| ≤ τ and the response is 1 if |Δw - Δr| > τ, where τ > 0 is the secret threshold value.

---

**We show that there exists a linear model that can perfectly predict the responses of a CAR-PUF, and this linear model can be estimated fairly accurately if given enough challenge-response pairs (CRPs).**
