# Temperature and Energy, Interactively

An interactive, single-page web demo of the very basics of thermal physics: what temperature is, how it is measured, the ideal gas, how temperature is related to the kinetic energy of molecules, and the equipartition of energy.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Statistical Physics 1, Chapter 1, Energy in Thermal Physics, Sections 1.1 to 1.3).

## What's inside

**Thermal equilibrium.** The operational, comparative, and theoretical definitions of temperature, heat, and the relaxation time. A simulation of two blocks of cells in thermal contact, in which neighboring cells simply split their combined energy at random, shows energy flowing from hot to cold "statistically, but almost surely": the block temperatures converge to the predicted final value with visible fluctuations. A fitted curve compares the result with Newton's law of cooling, T(t) = T<sub>env</sub> + (T(0) − T<sub>env</sub>) e<sup>−t/τ</sup>, and sliders set the starting temperatures, the relative size of the blocks, the quality of the contact, and the speed of the simulation. The types of equilibrium (thermal, mechanical, diffusive) are summarized.

**Measuring temperature.** A constant-volume gas thermometer: pressure-versus-temperature lines for three samples, extrapolated to absolute zero at −273.15 °C. A live converter between Celsius, kelvin, and Fahrenheit (Problem 1.1, with absolute zero at −459.67 °F). Thermal expansion (Problems 1.7 and 1.8): the derivation of β = α<sub>x</sub> + α<sub>y</sub> + α<sub>z</sub> = 3α, and a 1 km steel bridge that grows by about 55 cm between winter and summer, with the exact and linearized volume changes compared.

**The ideal gas.** PV = nRT = Nk<sub>B</sub>T, with the meaning of each quantity. The exponential atmosphere (Problem 1.16): P(z) = P(0) e<sup>−mgz/k<sub>B</sub>T</sup>, with the pressure at Ogden, Leadville, Mt. Whitney, and Mt. Everest for an adjustable air temperature. Real gases (Problem 1.17): the virial expansion and the van der Waals equation, with B(T) = b − a/RT fitted to the nitrogen data by hand or with a "Best fit" button that reproduces the lecture's a = 0.1823 J m³/mol² and b = 64.2 cm³/mol.

**Temperature is kinetic energy.** The derivation of the pressure from molecules bouncing off a piston, leading to K̄<sub>trans</sub> = (3/2)k<sub>B</sub>T and v<sub>rms</sub> = √(3k<sub>B</sub>T/m). A live simulation of noninteracting molecules in a box measures the momentum they deliver to the piston and compares it with Nk<sub>B</sub>T/V (the ratio converges to 1). A chart gives v<sub>rms</sub> for several gases at any temperature.

**Equipartition of energy.** Quadratic degrees of freedom, the equipartition theorem, and U<sub>thermal</sub> = Nf · ½k<sub>B</sub>T, with f = 3 for monatomic gases, 5 or 7 for diatomic gases, and 6 for solids. An animation of diatomic molecules and a heat-capacity curve for H₂, N₂, or O₂ (computed from the quantum rigid rotor and harmonic oscillator, as a preview of Chapter 3) show rotation and vibration switching on, and why f = 5 at room temperature.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- The thermal-contact model is a random energy-exchange process between neighboring cells on a grid; its equilibrium is the Boltzmann distribution, with temperature equal to the average energy per cell. Each block is scaled to start at exactly its chosen temperature.
- In the gas simulation the molecules never collide with each other, so nothing would even out a sample whose average v<sub>x</sub>² happened to differ from k<sub>B</sub>T/m. The starting velocities are therefore scaled so that each component averages exactly k<sub>B</sub>T/m; the measured pressure then converges to Nk<sub>B</sub>T/V (checked to within 0.2%).
- The heat-capacity curves use rotational temperatures of 85.3 K (H₂), 2.88 K (N₂), and 2.08 K (O₂) and vibrational temperatures of 6332 K, 3374 K, and 2256 K.
- The animations pause when scrolled off screen and start paused when the system asks for reduced motion.
- Long equations wrap on narrow screens.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode via `prefers-color-scheme`, and is responsive down to phone widths.
- Constants used: k<sub>B</sub> = 1.381 × 10<sup>−23</sup> J/K, N<sub>A</sub> = 6.022 × 10<sup>23</sup>, R = 8.314 J/(mol K).

## Caveats

- The gas-thermometer data are idealized straight lines, as for an ideal gas.
- The exponential atmosphere assumes a single temperature at all heights; real air cools with altitude.
- The diatomic heat-capacity curves are idealized: real hydrogen's low-temperature behavior is complicated by its two nuclear-spin forms, which are ignored here.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Sections 1.1 to 1.3 and Problems 1.1, 1.7, 1.8, 1.16, and 1.17, including the nitrogen virial data).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
