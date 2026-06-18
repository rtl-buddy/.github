# RTL Buddy

**Open-source tooling for SystemVerilog/Verilog design and verification — built to work well for both humans and AI agents.**

RTL Buddy is an ecosystem of tools centered on [`rtl_buddy`](https://github.com/rtl-buddy/rtl_buddy),
a Python CLI that gives RTL projects a single, repeatable control plane for everyday
design and verification work: simulator-driven tests and randomized regressions, filelist
generation, synthesis, place-and-route, power analysis, CDC lint, formal property
verification, mutation testing, waveform viewing, hierarchy rendering, AXI interconnect
profiling, and spec traceability.

It sits on top of the open-source tools your project already uses — Verilator, Yosys,
OpenROAD, SymbiYosys, Surfer, Verible — giving you a cleaner interface, structured
machine-readable output for CI and coding agents, and rich formatted output for people.

## Start here

- 📦 **[`rtl_buddy`](https://github.com/rtl-buddy/rtl_buddy)** — the flagship CLI ([PyPI](https://pypi.org/project/rtl_buddy/) · [docs](https://rtl-buddy.github.io/rtl_buddy/))
- 🚀 **[rtl-buddy-project-template](https://github.com/rtl-buddy/rtl-buddy-project-template)** — a ready-to-run RTL project with example designs, tests, and full integration; the fastest way to try it

```bash
uv add rtl_buddy
uv run rb test basic        # run a single test
uv run rb regression        # run the full regression
uv run rb cdc -c cdc/sandbox/cdc.yaml
```

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

RTL Buddy maintains lightly-patched forks of several open-source EDA tools so its flows
stay reproducible across platforms. Upstream is always the canonical source — these exist
only to pin known-good builds and carry integration fixes.

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
