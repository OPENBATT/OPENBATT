# OPENBATT master CAD platform: Fusion

Decided 21 Nov 2026. Copied here from the team's Claude doc on 21 Nov 2026.

## Decision

Fusion is the OPENBATT master CAD platform. On the final weights (AI agent depth 25%, community 10%, GitHub 10%, core CAD 55%) it scores 85/100, 13 points clear of Onshape and FreeCAD, which both score 72.

Fusion is the only tool that scores 4 or 5 on every criterion. It has the deepest official AI agent connection, native apps for Mac and Windows, native files that can be committed to GitHub, and solid electrical and simulation tools.

**Publishing rule:** every release commits the native .f3d files to GitHub, plus STEP, so Linux users and other CAD tools are covered.

## Scoring rubric

Each tool is scored 1 to 5 on seven criteria. The weighted total is out of 100. Core CAD is 55%, split evenly across its four parts.

| Criterion | Weight | 1 = | 5 = |
| --- | --- | --- | --- |
| AI agent / MCP depth | 25% | No server, or a hobby project | Official, vendor-maintained, live modelling plus data access |
| Community reach | 10% | Few users, paid licence to open files | Millions of users, free access to native files |
| GitHub and open publishing | 10% | Native files can't live in a repo, manual export only | Native files in the repo in an open format, exports scriptable from CI |
| Core CAD: modelling and workflow | 13.75% | Not parametric, or weak assemblies | Parametric timeline, assemblies, drawings, CAM and 3D-print export |
| Core CAD: electrical integration | 13.75% | Mechanical only | PCB sync with ECAD tools plus harness routing |
| Core CAD: simulation | 13.75% | None built in | Structural, thermal and flow analysis included |
| Core CAD: native desktop apps | 13.75% | Browser only, or one operating system | Native apps for Mac, Windows and Linux, works offline |

Cost is not scored; it appears in the Fusion vs Onshape comparison. Scores are a judgement as of November 2026, based on the vendor documentation and reviews listed under Sources. Fusion is the only tool tested hands-on, through its MCP connection.

## Scores

Fusion is the only tool with no score below 4. Onshape loses ground on native apps and GitHub; FreeCAD on AI and modelling; SolidWorks on AI, GitHub and native apps.

| Tool | Total /100 | AI / MCP (25%) | Community (10%) | GitHub (10%) | Modelling | Electrical | Simulation | Native apps |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Fusion** | **85** | **5** | **4** | **4** | **4** | **4** | **4** | **4** |
| Onshape | 72 | 4 | 5 | 3 | 4 | 4 | 3 | 2 |
| FreeCAD | 72 | 3 | 4 | 5 | 3 | 3 | 3 | 5 |
| SolidWorks | 69 | 2 | 4 | 2 | 5 | 5 | 5 | 2 |
| NX | 60 | 1 | 2 | 2 | 5 | 5 | 5 | 2 |
| Creo | 60 | 1 | 2 | 2 | 5 | 5 | 5 | 2 |
| Rhino | 57 | 4 | 3 | 3 | 2 | 1 | 2 | 4 |
| Solid Edge | 57 | 2 | 2 | 2 | 4 | 4 | 4 | 2 |
| CATIA | 57 | 1 | 2 | 2 | 5 | 4 | 5 | 2 |

The four core CAD columns are 13.75% each.

**Notes on the scores:**

- **Native desktop apps.**
  - Onshape scores 2: it runs only in a browser (plus iOS and Android apps) and needs internet at all times ([Onshape](https://onshape.com/en/enterprise/faq)).
  - Fusion scores 4: native on Mac and Windows, but not Linux ([Autodesk](https://autodesk.com/support/technical/article/Is-there-any-way-to-install-Fusion-360-in-Linux)).
  - FreeCAD scores 5: native on all three ([FreeCAD](https://wiki.freecad.org/Download/tr)).
  - SolidWorks, NX, Creo, CATIA and Solid Edge score 2: Windows-centric; interactive NX no longer runs on Linux ([Siemens](https://support.sw.siemens.com/en-US/okba/PL8823520/NX-2412-is-available-for-download/index.html)).
- **GitHub asks whether the native files can live in the repo.**
  - Onshape scores 3: its native model can't be exported as a file, so GitHub only ever gets STEP exports or a link to a public document. Built-in branching and CI exports still count.
  - Fusion scores 4: .f3d files can be committed, though as binaries without line-by-line diffs, and Fusion Compute MCP can run exports in the cloud ([Autodesk](https://www.autodesk.com/products/fusion-360/blog/fusion-compute-mcp/)).
  - The Windows desktop tools score 2: their native files can be committed, but automating exports needs a licensed Windows machine.
- **Electrical credits ECAD sync and harness routing, not just built-in PCB design.**
  - SolidWorks scores 5: CircuitWorks two-way sync is in every tier ([SolidWorks](https://blogs.solidworks.com/solidworksblog/2025/06/whats-new-in-solidworks-ecad-mcad-collaboration.html)), and Premium adds harness routing ([3DS store](https://www.3ds.com/store/solidworks-design)).
  - Onshape scores 4: PCB Studio with Altium 365 sync ([Onshape](https://www.onshape.com/en/features/pcb-studio)).
  - Fusion scores 4: built-in PCB design, but no harness routing on a par with SolidWorks.
- **Community counts free access to native files, not just user numbers.**
  - Onshape scores 5: public documents anyone can view and copy ([Onshape](https://cad.onshape.com/help/Content/managing_accounts.htm)).
  - SolidWorks scores 4: 3 million+ users, but its native files need a paid licence.
- **Weights were set by John:** AI 25%, community 10%, GitHub 10%, core CAD 55%.

## Fusion vs Onshape, head to head

Onshape is the strongest challenger, but Fusion wins six of the eight factors that separate them. Onshape wins only on free community access.

| Factor | Fusion | Onshape | Edge |
| --- | --- | --- | --- |
| AI agent modelling | Three official MCP servers, including live modelling; proven on our own enclosure build ([Autodesk](https://help.autodesk.com/cloudhelp/ENU/Fusion-MCP/files/FMCP-OVERVIEW.htm)) | Official MCP writes FeatureScript only; full REST API for everything else ([PTC](https://www.ptc.com/en/news/2026/onshape-launches-featurescript-mcp-server)) | Fusion |
| Native apps | Mac and Windows; works offline | Browser only, plus mobile apps; needs internet at all times | Fusion |
| Native files in GitHub | .f3d committed to the repo (binary, no line diffs) | Not possible: the model never leaves Onshape, so the repo gets STEP only | Fusion |
| Community access | Free personal licence for hobbyists earning under US$1,000 a year from it; desktop install | Free public documents anyone can view and copy in a browser | Onshape |
| Electrical | Built-in PCB design, Altium CoDesigner | PCB Studio with Altium 365 cloud sync | Tie |
| Simulation | Static stress included; advanced studies in an extension | In the Professional plan | Fusion, slightly |
| Cost per seat | US$680 a year ([Autodesk](https://www.autodesk.com/products/fusion-360/personal/compare)) | US$1,500 Standard; US$2,500 Professional for simulation and ECAD exchange ([Onshape](https://www.onshape.com/en/pricing?in=usd)) | Fusion |
| Switching cost | None: OPENBATT Parametric already lives here | Full rebuild; Fusion timelines don't transfer, only STEP geometry | Fusion |

Onshape would only win if free browser access for outside contributors outweighed everything else. With AI at 25% and native apps inside core CAD, it doesn't.

## Why the others are secondary

The rest trail by 13 points or more. Some are excellent engineering tools, but each has a blocker for an AI-driven, Mac-based, open-publishing project.

| Tool | Real strengths | Blocker for OPENBATT | Supporting role |
| --- | --- | --- | --- |
| FreeCAD | Free for everyone, including commercial use; open file format; native on Mac, Windows and Linux; KiCad two-way sync | No vendor MCP, only community servers ([GitHub](https://github.com/spkane/freecad-addon-robust-mcp-server)); less polished for production work | Test every STEP release opens cleanly in it |
| SolidWorks | Best-in-class electrical: CircuitWorks two-way sync in every tier, harness routing in Premium; top-tier simulation; 3 million+ users | No official MCP ([Leo AI](https://www.getleo.ai/blog/cad-mcp-server-comparison-2026)); Windows-only, so a Mac needs Parallels; US$2,820–4,716 a year ([3DS store](https://www.3ds.com/store/solidworks-design)); native files need a paid licence | Make sure STEP imports cleanly for the many engineers who use it |
| NX, Creo | Top-tier simulation, harness design and Altium CoDesigner support | No official MCP; enterprise pricing; Windows-centric | Partners import STEP |
| Solid Edge | Solid mid-range feature set | No official MCP, one community server ([vibecad.nl](https://vibecad.nl/en/which-cad-programs-support-mcp-in-2026/)); Windows-only | None |
| Rhino | Official MCP, Mac-native | Surface modeller, not parametric mechanical CAD; MCP still a work-in-progress plugin ([McNeel](https://github.com/mcneel/RhinoAI/releases)) | Industrial-design surfacing only |
| CATIA | Aerospace-grade CAD and simulation | No official MCP; enterprise pricing and platform | None |

## Risks and publishing rules

The main risk is depending on one vendor. Four publishing rules keep the standard independent of Autodesk.

| Risk | Mitigation |
| --- | --- |
| Autodesk changes licensing or pricing | Every release also ships STEP, drawings (PDF) and a parameter table, so the standard never depends on Fusion |
| Free licence limits: personal use is for people earning under US$1,000 a year from it ([Autodesk](https://www.autodesk.com/products/fusion-360/blog/fusion-for-personal-use-vs-autodesk-fusion/)) | Commercial contributors work from STEP, or use the startup licence |
| .f3d binaries can't be diffed in GitHub | Release notes list every dimension change; the parameter table is a text file that diffs cleanly |
| MCP behaviour shifts between Fusion updates | Keep export and check scripts in the repo and rerun them after each Fusion update |
| An outside contributor community forms and wants to fork in the browser | Review the switch to Onshape at that point; STEP releases keep the geometry portable, though Fusion timelines would need rebuilding |

**Publishing rules for every release:**

1. Native .f3d of every part and assembly, tagged with the release version.
2. STEP of every part and assembly.
3. Drawings as PDF, with critical interface dimensions and tolerances.
4. A CSV parameter table, exported from Fusion's user parameters.

## Sources

- [Autodesk Fusion MCPs overview](https://help.autodesk.com/cloudhelp/ENU/Fusion-MCP/files/FMCP-OVERVIEW.htm)
- [Autodesk: Fusion Compute MCP](https://www.autodesk.com/products/fusion-360/blog/fusion-compute-mcp/)
- [Autodesk: Fusion can't be installed on Linux](https://autodesk.com/support/technical/article/Is-there-any-way-to-install-Fusion-360-in-Linux)
- [Autodesk: Fusion licence types](https://www.autodesk.com/products/fusion-360/blog/fusion-360-license-types/)
- [Autodesk: Fusion for personal use vs Autodesk Fusion](https://www.autodesk.com/products/fusion-360/blog/fusion-for-personal-use-vs-autodesk-fusion/)
- [Autodesk: personal vs commercial comparison and pricing](https://www.autodesk.com/products/fusion-360/personal/compare)
- [Autodesk: Fusion 10-year anniversary](https://autodesk.com/products/fusion-360/blog/?p=62809)
- [Autodesk: Fusion plans and extensions](https://www.autodesk.com/uk/products/fusion-360?panel=buy)
- [PTC: Onshape FeatureScript MCP Server launch](https://www.ptc.com/en/news/2026/onshape-launches-featurescript-mcp-server)
- [Onshape: platform support](https://onshape.com/en/enterprise/faq)
- [Onshape: pricing](https://www.onshape.com/en/pricing?in=usd)
- [Onshape: managing plans and public documents](https://cad.onshape.com/help/Content/managing_accounts.htm)
- [Onshape: PCB Studio](https://www.onshape.com/en/features/pcb-studio)
- [Onshape: REST API automation](https://www.onshape.com/en/blog/cloud-native-cad-rest-api)
- [SolidWorks: ECAD-MCAD collaboration updates](https://blogs.solidworks.com/solidworksblog/2025/06/whats-new-in-solidworks-ecad-mcad-collaboration.html)
- [3DS store: SolidWorks Design plans](https://www.3ds.com/store/solidworks-design)
- [SolidWorks: company information](https://www.solidworks.com/sw/183_ENU_HTML.htm)
- [Siemens: NX 2412 release, interactive NX dropped on Linux](https://support.sw.siemens.com/en-US/okba/PL8823520/NX-2412-is-available-for-download/index.html)
- [FreeCAD: download and supported platforms](https://wiki.freecad.org/Download/tr)
- [Altium: MCAD CoDesigner supported versions](https://www.altium.com/documentation/altium-codesigner/new)
- [Leo AI: MCP for CAD in 2026](https://www.getleo.ai/blog/cad-mcp-server-comparison-2026)
- [vibecad.nl: Which CAD programs support MCP in 2026?](https://vibecad.nl/en/which-cad-programs-support-mcp-in-2026/)
- [FreeCAD Robust MCP Server](https://github.com/spkane/freecad-addon-robust-mcp-server)
- [McNeel RhinoAI releases](https://github.com/mcneel/RhinoAI/releases)
- [FusionToGitHub script](https://github.com/zcohenld/FusionToGitHub)
