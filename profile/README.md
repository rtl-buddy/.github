<div align="center">

<img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/rb-mascot.png" alt="RTL Buddy mascot" width="160" />

# RTL Buddy

**One CLI that runs your SystemVerilog tests, lint, formal, synthesis, place-and-route and power on open-source tools,<br/>and reports every result as a table for you and as JSON for your CI and coding agents.**

[![PyPI](https://img.shields.io/pypi/v/rtl_buddy?label=rtl_buddy)](https://pypi.org/project/rtl_buddy/)
[![Python](https://img.shields.io/pypi/pyversions/rtl_buddy)](https://pypi.org/project/rtl_buddy/)
[![Tests](https://img.shields.io/github/actions/workflow/status/rtl-buddy/rtl_buddy/test.yml?branch=main&label=tests)](https://github.com/rtl-buddy/rtl_buddy/actions/workflows/test.yml)
[![Last release](https://img.shields.io/github/release-date/rtl-buddy/rtl_buddy?label=last%20release)](https://github.com/rtl-buddy/rtl_buddy/releases)
[![Docs](https://img.shields.io/badge/docs-rtl--buddy.github.io-blue)](https://rtl-buddy.github.io/rtl_buddy/latest/)
[![License](https://img.shields.io/badge/license-BSD--3--Clause-blue)](https://github.com/rtl-buddy/rtl_buddy/blob/main/LICENSE)

<a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#browse-it-live-in-the-hub"><img src="https://raw.githubusercontent.com/rtl-buddy/rtl_buddy/main/static/img/tour/hub-sch.png" alt="The RTL Buddy hub: live schematic of the template's ALU subsystem with the coverage overlay on, instance tree on the left" width="900" /></a>

*The hub's schematic pane of the template's ALU subsystem, coverage overlay on. Every picture and table on this page is real output from the [project template](https://github.com/rtl-buddy/rtl-buddy-project-template).*

**[Take the tour →](https://rtl-buddy.github.io/rtl_buddy/latest/tour/)** command by command, from one test to a routed chip.

</div>

## Who it is for

- **RTL engineers** who want `rb test`, `rb cdc`, `rb fpv`, `rb synth` and `rb pnr` to feel like one tool, not six, with the artefacts of each step feeding the next.
- **CI pipelines** that need a stable exit code, a machine-readable verdict and structured logs from every flow, without parsing tool output.
- **Coding agents** that need to plan, run and interpret a full RTL flow on their own: YAML configs, JSONL output, `rb tool-check`, a [bundled skill](https://rtl-buddy.github.io/rtl_buddy/latest/agents/) and a queryable [design graph](https://rtl-buddy.github.io/rtl_buddy/latest/concepts/graph/).

It sits on top of the open-source tools your project already uses: Verilator, Yosys, OpenROAD, SymbiYosys, Surfer, Verible, KLayout, cocotb.

## Try it in three commands

```bash
git clone https://github.com/rtl-buddy/rtl-buddy-project-template.git && cd rtl-buddy-project-template
uv run rb tool-check                      # tells you which EDA tools are found and which are missing
uv run rb regression -c regression.yaml   # the whole demo regression, one table
```

```text
┃ Suite                                 ┃ Test         ┃ Result ┃ Description ┃
│ verif/ip_async_fifo/tests.yaml        │ smoke        │ PASS   │ (nwrn=  0)  │
│ verif/demo_tiny_alu/tests.yaml        │ basic        │ PASS   │ (nwrn=  0)  │
│ verif/demo_tiny_alu/tests.yaml        │ random       │ PASS   │ (nwrn=  0)  │
│ verif/demo_tiny_alu_sc/tests.yaml     │ basic_sc     │ PASS   │ ED (0 errors) │
                                 Builder: verilator
```

Only Verilator is needed for that. Each further workflow needs one more tool, and `rb tool-check` names it. Pinned, validated builds of all of them are in [rtl-buddy-tools](https://github.com/rtl-buddy/rtl-buddy-tools). To add RTL Buddy to an existing project: `uv add rtl_buddy`, then follow the [Quick Start](https://rtl-buddy.github.io/rtl_buddy/latest/quickstart/).

## What you get

Each tile links to that step of the tour, with the real command and its real output.

<table>
  <tr>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#run-a-regression"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/sim-regression.png" width="110" /></a><br/>
      <b>Simulation &amp; regression</b><br/><sub><code>rb test</code> · <code>rb regression</code></sub><br/>
      <sub>SV, SystemC and cocotb suites in one table; Slurm or local-parallel dispatch</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#measure-coverage"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/ci-agent-mode.png" width="110" /></a><br/>
      <b>Coverage</b><br/><sub><code>rb cov</code></sub><br/>
      <sub>line, branch, toggle, expression and cover points per test, file and module</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#look-at-the-waveform"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/wave-debug.png" width="110" /></a><br/>
      <b>Waveforms &amp; hub</b><br/><sub><code>rb wave</code> · <code>rb hub</code></sub><br/>
      <sub>Surfer, four browser panes and Neovim, all selecting the same signal</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#lint-clock-domain-crossings"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/cdc.png" width="110" /></a><br/>
      <b>CDC lint</b><br/><sub><code>rb cdc</code></sub><br/>
      <sub>every crossing traced to its flops, with auditable waivers</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#prove-properties"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/formal.png" width="110" /></a><br/>
      <b>Formal verification</b><br/><sub><code>rb fpv</code></sub><br/>
      <sub>SymbiYosys plus vacuity, cone-of-influence and dead-assume checks</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#score-the-testbench-with-mutants"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/mutation-testing.png" width="110" /></a><br/>
      <b>Mutation testing</b><br/><sub><code>rb mut</code></sub><br/>
      <sub>a score for your properties, and which survivors they should have caught</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#synthesize"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/synth-pnr-power.png" width="110" /></a><br/>
      <b>Synth · P&amp;R · power</b><br/><sub><code>rb synth</code> · <code>rb pnr</code> · <code>rb power</code></sub><br/>
      <sub>Yosys to OpenROAD to GDS, with timing, DRC and power from real activity</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#profile-an-interconnect"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/axi-profiling.png" width="110" /></a><br/>
      <b>AXI profiling</b><br/><sub><code>rb axi-profile</code></sub><br/>
      <sub>per-channel utilization, back-pressure and latency percentiles from a trace</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#ask-the-design-questions"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/graph.png" width="110" /></a><br/>
      <b>Design knowledge graph</b><br/><sub><code>rb graph</code></sub><br/>
      <sub>hierarchy, ports and crossings as a graph an agent can query</sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/concepts/fpga/"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/fpga-implementation.png" width="110" /></a><br/>
      <b>FPGA implementation</b><br/><sub><code>rb fpga</code></sub><br/>
      <sub>Vivado or openXC7, with post-route utilization and timing as structured metrics</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/concepts/spec-traceability/"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/spec-traceability.png" width="110" /></a><br/>
      <b>Spec traceability</b><br/><sub><code>rb spec</code></sub><br/>
      <sub>spec items linked to models, tests and proofs, with the gaps listed</sub>
    </td>
    <td align="center" width="200">
      <a href="https://rtl-buddy.github.io/rtl_buddy/latest/concepts/xplr/"><img src="https://raw.githubusercontent.com/rtl-buddy/.github/main/profile/assets/xplr.png" width="110" /></a><br/>
      <b>Design-space exploration</b><br/><sub><code>rb xplr</code></sub><br/>
      <sub>a ledger of knob changes, rationale and outcomes an agent can continue from</sub>
    </td>
  </tr>
</table>

<div align="center">
<a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#place-and-route"><img src="https://raw.githubusercontent.com/rtl-buddy/rtl_buddy/main/static/img/tour/subsys-nangate45-routed.png" alt="KLayout render of the routed ALU subsystem on Nangate45" width="270" /></a>
&nbsp;
<a href="https://rtl-buddy.github.io/rtl_buddy/latest/tour/#annotate-your-editor"><img src="https://raw.githubusercontent.com/rtl-buddy/rtl_buddy/main/static/img/tour/nvim-wave-annotation.png" alt="Neovim showing the selected waveform signal's value rendered inline next to its declaration" width="600" /></a>

*Left: the template subsystem routed on Nangate45 by `rb pnr-export`. Right: the waveform cursor's value for `y` rendered inline in Neovim.*
</div>

## The ecosystem

| Repo | What it does |
|------|--------------|
| [`rtl_buddy`](https://github.com/rtl-buddy/rtl_buddy) | The CLI: tests, regressions, coverage, synthesis, P&R, power, and the hub that ties the rest together ([PyPI](https://pypi.org/project/rtl_buddy/) · [docs](https://rtl-buddy.github.io/rtl_buddy/latest/)) |
| [`rtl-buddy-project-template`](https://github.com/rtl-buddy/rtl-buddy-project-template) | A ready-to-run RTL project with every workflow wired up. Clone it to try things, or start your project from it |
| [`rtl-buddy-cdc`](https://github.com/rtl-buddy/rtl-buddy-cdc) | Clock-domain-crossing lint engine (`rb cdc`) |
| [`rtl-buddy-view`](https://github.com/rtl-buddy/rtl-buddy-view) | Hierarchy, schematic and connectivity views (`rb hier`, the hub's schematic pane) |
| [`rtl-buddy-axi-profiler`](https://github.com/rtl-buddy/rtl-buddy-axi-profiler) | AXI/APB/AHB interconnect performance profiler (`rb axi-profile`) |
| [`rtl-buddy-xeno`](https://github.com/rtl-buddy/rtl-buddy-xeno) | SystemVerilog AST mutator behind mutation testing (`rb mut`) and CDC/FPV fuzz corpora |
| [`rtl-buddy-nvim`](https://github.com/rtl-buddy/rtl-buddy-nvim) | Neovim plugin: waveform values and physical metrics annotated in the editor, selection synced with the hub |
| [`rtl-buddy-tools`](https://github.com/rtl-buddy/rtl-buddy-tools) | Pinned, validated macOS/Linux builds of every EDA tool `rtl_buddy` depends on |

<details>
<summary><b>Vendored upstream tools</b></summary>

RTL Buddy maintains lightly patched forks of several open-source EDA tools so its flows stay
reproducible across platforms. Upstream is always the canonical source; these exist only to pin
known-good builds and carry integration fixes.

[`yosys`](https://github.com/rtl-buddy/yosys) ·
[`yosys-slang`](https://github.com/rtl-buddy/yosys-slang) ·
[`surfer`](https://github.com/rtl-buddy/surfer) ·
[`verilator`](https://github.com/rtl-buddy/verilator) ·
[`PeakRDL`](https://github.com/rtl-buddy/PeakRDL) ·
[`coverview`](https://github.com/rtl-buddy/coverview)

</details>

## How it is built

RTL Buddy is an experiment in agent-built EDA tooling. The code, tests and docs across these
repos are written largely by AI coding agents under human review, and the tools are designed to
be driven by agents in turn: YAML in, JSONL out, explicit tool-readiness checks. That is how a
toolchain of this scope grows this fast, and it is also why it is fast-moving software: pin your
versions, expect rough edges, and [open an issue](https://github.com/rtl-buddy/rtl_buddy/issues)
when something cracks. Agents fixing what agents built, backed by the regression suites and the
project template as a constant end-to-end check, is the loop the project runs on.

## Documentation and license

Full docs live at **[rtl-buddy.github.io/rtl_buddy](https://rtl-buddy.github.io/rtl_buddy/latest/)**, including an
[agent-readable index](https://rtl-buddy.github.io/rtl_buddy/latest/llms.txt) of every page.

RTL Buddy's first-party tools are released under the BSD-3-Clause license.
Forked upstream projects retain their original licenses.
