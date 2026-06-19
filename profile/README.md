<div align="center">

<img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/rb-mascot.png" alt="RTL Buddy mascot" width="200" />

# RTL Buddy

**Open-source tooling for SystemVerilog/Verilog design and verification —<br/>built to work well for both humans and AI agents.**

[![PyPI](https://img.shields.io/pypi/v/rtl_buddy)](https://pypi.org/project/rtl_buddy/)
[![Docs](https://img.shields.io/badge/docs-rtl--buddy.github.io-blue)](https://rtl-buddy.github.io/rtl_buddy/)
[![License](https://img.shields.io/badge/license-BSD--3--Clause-blue)](https://github.com/rtl-buddy/rtl_buddy/blob/main/LICENSE)

</div>

RTL Buddy is an ecosystem of tools centered on [`rtl_buddy`](https://github.com/rtl-buddy/rtl_buddy),
a Python CLI that gives RTL projects a single, repeatable control plane for everyday design and
verification work. It sits on top of the open-source tools your project already uses — Verilator,
Yosys, OpenROAD, SymbiYosys, Surfer, Verible — giving you a cleaner interface, structured
machine-readable output for CI and coding agents, and rich formatted output for people.

## Start here

- **[`rtl_buddy`](https://github.com/rtl-buddy/rtl_buddy)** — the flagship CLI ([PyPI](https://pypi.org/project/rtl_buddy/) · [docs](https://rtl-buddy.github.io/rtl_buddy/))
- **[rtl-buddy-project-template](https://github.com/rtl-buddy/rtl-buddy-project-template)** — a ready-to-run RTL project with example designs, tests, and full integration; the fastest way to try it

```bash
uv add rtl_buddy
uv run rb test basic        # run a single test
uv run rb regression        # run the full regression
uv run rb cdc -c cdc/sandbox/cdc.yaml
```

## What it does

<table>
  <tr>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/sim-regression.png" width="120" /><br/>
      <b>Simulation &amp; Regression</b><br/><sub><code>rb test</code> · <code>rb regression</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/wave-debug.png" width="120" /><br/>
      <b>Waveform Debug</b><br/><sub><code>rb wave</code> · <code>rb hub</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/synth-pnr-power.png" width="120" /><br/>
      <b>Synth · PnR · Power</b><br/><sub><code>rb synth</code> · <code>rb pnr</code> · <code>rb power</code></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/cdc.png" width="120" /><br/>
      <b>CDC Lint</b><br/><sub><code>rb cdc</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/formal.png" width="120" /><br/>
      <b>Formal Verification</b><br/><sub><code>rb fpv</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/mutation-testing.png" width="120" /><br/>
      <b>Mutation Testing</b><br/><sub><code>rb mut</code></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/axi-profiling.png" width="120" /><br/>
      <b>AXI Profiling</b><br/><sub><code>rb axi-profile</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/spec-traceability.png" width="120" /><br/>
      <b>Spec Traceability</b><br/><sub><code>rb spec</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/fpga-implementation.png" width="120" /><br/>
      <b>FPGA Implementation</b><br/><sub><code>rb fpga</code></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/xplr.png" width="120" /><br/>
      <b>Design-Space Exploration</b><br/><sub><code>rb xplr</code></sub>
    </td>
    <td align="center" width="200">
      <img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/ci-agent-mode.png" width="120" /><br/>
      <b>CI &amp; Agent Mode</b><br/><sub>JSONL logs · <code>rb tool-check</code></sub>
    </td>
    <td align="center" width="200"></td>
  </tr>
</table>

## Design philosophy

RTL Buddy is an **experiment in agent-built EDA tooling** — built by agents, for agents,
with humans in the loop. The code, tests, and tooling across these repos are written
largely by AI coding agents under human supervision, and the tools are designed first to
be driven *by* agents: structured YAML config, machine-readable JSONL output, and
explicit tool-readiness checks so an agent can plan, run, and interpret a full RTL flow
on its own.

We're betting on speed. Letting agents do the building lets us move at a pace a
hand-written toolchain of this scope simply can't — spanning simulation, synthesis, PnR,
power, CDC, formal, mutation, profiling, and more, and growing fast.

We're equally blunt about the catch: **agent-written code moves fast and breaks things.**
Gaps, rough edges, and the occasional wrong turn come with the territory. Our bet is that
we can *close* them just as fast as we make them — with agents, backed by human review,
regression suites, and the project template as a constant end-to-end check.

So treat this as **living, breaking, fast-moving software.** Pin your versions, expect
things to change under you, and [open issues](https://github.com/rtl-buddy) when something
cracks — that loop, agents fixing what agents built, *is* the project.

## The ecosystem

### Core tools

| Repo | What it does |
|------|--------------|
| [`rtl_buddy`](https://github.com/rtl-buddy/rtl_buddy) | The CLI — tests, regressions, synthesis, PnR, power, coverage, and the coordination hub that ties the rest together |
| [`rtl-buddy-cdc`](https://github.com/rtl-buddy/rtl-buddy-cdc) | Clock-domain-crossing lint engine (`rb cdc`) |
| [`rtl-buddy-view`](https://github.com/rtl-buddy/rtl-buddy-view) | RTL hierarchy and connectivity visualization (`rb hier`) |
| [`rtl-buddy-axi-profiler`](https://github.com/rtl-buddy/rtl-buddy-axi-profiler) | AXI/APB/AHB interconnect performance profiler (`rb axi-profile`) |
| [`rtl-buddy-xeno`](https://github.com/rtl-buddy/rtl-buddy-xeno) | SystemVerilog AST mutator powering mutation testing (`rb mut`) and CDC/FPV fuzz corpora |
| [`rtl-buddy-tools`](https://github.com/rtl-buddy/rtl-buddy-tools) | Pinned, validated macOS/Linux builds of every EDA tool `rtl_buddy` depends on |

### Editor integration

| Repo | What it does |
|------|--------------|
| [`rtl-buddy-nvim`](https://github.com/rtl-buddy/rtl-buddy-nvim) | Neovim plugin for the RTL Buddy coordination hub |

### Vendored upstream tools

RTL Buddy maintains lightly-patched forks of several open-source EDA tools so its flows stay
reproducible across platforms. Upstream is always the canonical source — these exist only to pin
known-good builds and carry integration fixes.

[`yosys`](https://github.com/rtl-buddy/yosys) ·
[`yosys-slang`](https://github.com/rtl-buddy/yosys-slang) ·
[`surfer`](https://github.com/rtl-buddy/surfer) ·
[`verilator`](https://github.com/rtl-buddy/verilator) ·
[`PeakRDL`](https://github.com/rtl-buddy/PeakRDL) ·
[`coverview`](https://github.com/rtl-buddy/coverview)

## Documentation

Full docs live at **[rtl-buddy.github.io/rtl_buddy](https://rtl-buddy.github.io/rtl_buddy/)**.

## License

RTL Buddy's first-party tools are released under the BSD-3-Clause license.
Forked upstream projects retain their original licenses.
