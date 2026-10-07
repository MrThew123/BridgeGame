# Techquity Bridge Lab

Open `index.html` in a modern browser. The game is self-contained and works offline. The interface uses Techquity purple (#5a108f) and the actual logo from the electronics site, with a mission selector, contextual parts and separate test bar.

## Building and testing

Click two marked joints or drag between them to place a part. Road and reinforced road connect circle joints. Wood and metal beams connect marked joints into trusses or ground-supported frames. Crossing lines do not create joints.

Click an existing beam with another support material selected to change it. Click a road section with Strong road selected to reinforce it, or Road to downgrade it. Placement and upgrades are blocked if they exceed the budget. Erase, clear, undo and redo remain available while building.

Each success opens a learning dialogue showing the concept, what happened in this design and what comes next. Inspect bridge closes the dialogue. Next mission carries compatible parts into the following challenge. Selecting a mission from the menu starts it fresh. Teacher maths stays optional.

## Progression

| Mission | New challenge or component | Car | Drive at hinge |
| --- | --- | --- | --- |
| 1 First span | Road, 2 m gap | 55 kg | 2 kN·m |
| 2 Triangles | Wood trusses, 4 m gap | 55 kg | 6.5 kN·m |
| 3 Balance | 50 kg counterweights | 55 kg | 5.5 kN·m |
| 4 Leverage | Near or far position, one weight | 55 kg | 5.15 kN·m |
| 5 Heavier car | Reinforced road; budget $310 | 220 kg | 6.5 kN·m |
| 6 Less material | Metal beams, fewer upper joints, budget $232 | 220 kg | 5.15 kN·m |
| 7 Raised bank | Right bank 0.75 m higher | 200 kg | Fixed bridge |
| 8 Rock anchors | Uneven ground anchors, both carry load | 350 kg | Fixed bridge |
| 9 Mixed materials | Shallow anchors, budget $200 | 550 kg | Fixed bridge |
| Expert 1 Strength without excess | Two truss joints, one 50 kg counterweight, budget $285 | 650 kg | 5.25 kN·m |
| Expert 2 Uneven foundations | 0.5 m uphill road, two uneven rock anchors, budget $248 | 700 kg | Fixed bridge |
| Expert 3 Final balancing act | Unequal truss heights, one 50 kg counterweight, budget $365 | 800 kg | 6.55 kN·m |

## Expert extensions

The mission picker separates the nine core missions from three Expert Extensions. Completing core mission 9 offers **Enter expert extensions**. Each extension starts with an empty workbench and displays a persistent Expert Extension banner plus its geometry and component limits. All materials are unlocked, while counterweights remain available only on lifting bridges.

Expert 1 combines a heavy car, sparse truss joints, selective metal upgrades and a limited drive. Expert 2 combines a sloping road, unequal rock supports and selective deck reinforcement; both anchors must actually carry load. Expert 3 combines an asymmetric truss, mixed wood and metal, selective road reinforcement, counterweight position and a fixed torque limit. The final extension tests strength and lifting separately.

Budgets are hard placement and upgrade limits. The drive rating and car mass cannot be changed. Each lifting extension allows at most one 50 kg counterweight. The fixed extension has no lifting test. Reference designs have been checked within every limit; cheap all-wood shortcuts fail, and reference lifting designs with the nearer counterweight carry the car but fail to open. Reference designs are evidence of playability, not restrictions on alternative solutions.

The heavier-car mission is easier than the previous revision: load reduced from 350 kg to 220 kg at the new scale, budget increased from $285 to $310, a higher-output drive, and reinforced road available as an alternative way to control bending. An unsupported long road still fails.

Game costs scale with length: road $12, reinforced road $18, wood $6 and metal $14 per 0.5 m. Reinforced road is stiffer and heavier. Wood is cheap and light; metal is stronger, heavier and dearer.

## Lifting mechanism

This revision replaces the microservo illustration with a bank-mounted geared actuator and axle. Its rating is the idealised output torque at the hinge, in kN·m.

In missions 1–6, both banks support the leaf during crossing. The car leaves before opening; the right rest then releases. The deck and its attached truss lift together as one moving leaf. A rear balance arm turns with the leaf, so its counterweight opposes the bridge's gravitational moment. The drive and banks remain fixed. These trusses belong to the leaf, rather than being fixed ground supports.

Missions 7–9 are ground-supported fixed bridges. Rock anchors remain fixed, their members carry load into the ground, and no lifting test occurs.

The geometry, moving masses, stiffnesses, strengths and torque calculation were rescaled together. The spans are now 2–4 m, loads are in kg, and counterweights are 50 kg. Material properties, costs and drive ratings are calibrated classroom game settings, not hardware specifications.

The simplified elastic-frame model includes distributed member weight, two moving axle loads and member stiffness/strength. Opening assumes a rigid connected leaf and compares the horizontal gravity moment with available drive torque. The counterweight arm is idealised as rigid and massless. It does not simulate buckling, fatigue, actuator gearing losses or safety factors.

## Controls

Pause and playback speed affect the test. Edit preserves the design. Arrow keys select joints in the focused building area; Enter selects an endpoint; Escape cancels. Tests start at 2×.

## Assets

- `index.html`: complete game with wheel-less car body and Techquity logo embedded.
- `car-body.png`: transparent wheel-less car body used by the game. The renderer adds two rotating wheels, aligned with the empty arches; there are no baked-in wheels underneath them.
- `car.png`: earlier original sprite, kept as a source reference.
- `bridge-parts.svg`: reusable road, reinforced road, wood and metal beams, rock anchors, hinge, counterweight, geared drive, bank, water and broken deck.

The wheel-less body was edited with the built-in image-generation tool, then trimmed and resized. Edit prompt: “Remove BOTH wheels completely, including every tyre, rim, hub and spoke. Leave clean empty transparent wheel arches at exactly the original wheel centres. Keep the teal body silhouette, windows, headlights, proportions, perspective and original body artwork unchanged. No new wheels, no ground or shadows, no logos or text. Preserve transparency. The game will draw separate rotating wheels inside these empty wheel arches.”

`techquity-logo.png` is the actual header logo retrieved from https://www.electronics.techquity.co.nz/ on 6 October 2026. It is embedded in the game so hosting does not depend on the site's image URL. Brand purple #5a108f comes from the site's HTML. The logo remains Techquity's branding; its inclusion does not grant rights to third parties. Bridge and drive artwork is original code-native vector/canvas artwork. The Poly Bridge reference informed the build-test-revise interaction: https://polybridgegame.com/poly-bridge-4/

## Verification

Automated checks passed for reference designs in all nine missions, material unlock restrictions, the easier heavier-car mission, reinforced road reducing deflection while adding mass, scaled torque and counterweight calculations, learning-dialogue opening/closing/next flow, real car-load reactions at both rock anchors, failure of the all-wood final reference, success of the mixed-material reference within budget, upgrades, undo/redo, drag building, pause/edit and slope/lift animation consistency.

The wheel-less sprite and composed canvas drawing were visually inspected. Full browser and mobile layout checks remain unavailable because this execution environment has no browser executable.

## GitHub Pages and Google Sites

This project is hosted in `MrThew123/BridgeGame`. No build step or package installation is needed.

1. Create the repository in the intended GitHub account. A public repository supports GitHub Pages on GitHub Free.
2. Upload the bundle contents to the repository root, including `index.html` and `.nojekyll`.
3. Under Settings → Pages, select **Deploy from a branch**, **main**, and **/(root)**, then Save.
4. Wait for deployment and open the Pages URL shown in those settings.
5. In Google Sites, choose Insert → Embed → By URL and paste the Pages URL. Give the game enough vertical space for its toolbar and feedback.

Official setup reference: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

Edit `index.html` to update the game. `README.md` contains these notes. `.nojekyll` serves the static files without Jekyll processing. GitHub Pages deploys the repository's main branch after each update.
