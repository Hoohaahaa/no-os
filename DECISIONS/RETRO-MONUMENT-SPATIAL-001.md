# Retrospective Decision Record: Monument Spatial Engine v1

- **Record ID:** MONUMENT-SPATIAL-001
- **Status:** Partially reconstructed; implementation and some rationales require verification.
- **Record type:** Retrospective
- **Date reconstructed:** 2026-11-18
- **Product:** Monument
- **Source:** Accessible prior conversation summaries dated 2026-11-18; source coverage is incomplete.
- **Confidence:** Medium for explicit user selections; low for missing rationales and assistant-proposed stack details.

## Context and objective
Monument is exploring a spatial/AR experience that places large vertical visual surfaces and content into real-world geographic space. The v1 direction discussed a vertical geometry and a terrain-aware surface behavior.

## Recorded decisions and alternatives

### Geometry
- **Selected:** Vertical geometry.
- **Alternatives not established by available source:** Other geometry options were not recoverable from the accessible summary.
- **Reason for selection:** Unknown in the available source. Do not infer.
- **Disposition:** Selected by the user in the prior conversation.
- **Revisit trigger:** If field tests show vertical geometry does not support the intended real-world experience or content legibility.

### Surface / terrain behavior
- **Latest selected path:** Follow terrain.
- **Earlier path:** Flat was stated earlier and is superseded by the later Follow selection.
- **Reason for changing from Flat to Follow:** Unknown in the available source.
- **Important distinction:** Follow was the latest explicit user selection; the source does not preserve the user's rationale for that choice.
- **Revisit trigger:** Terrain accuracy, placement stability, editability, performance, and authoring complexity from real-device tests.

### Ground-relative vertical curtain — v1 implementation proposal
- **Proposed implementation:** A vertical curtain whose bottom edge follows terrain while maintaining a constant height relative to the ground.
- **Alternatives mentioned:** A fully terrain-conforming wall; a height referenced to a fixed absolute altitude.
- **Reason given in the prior assistant recommendation:** The ground-following curtain was described as easier to understand and edit, with lower technical risk.
- **Decision authority:** This rationale was an assistant recommendation in the prior conversation; it must not be represented as the user's own rationale or as a fully verified final implementation decision.
- **Status:** Proposed v1 direction; requires confirmation against the actual project state and tests.

### Spatial technology stack
- **Proposed:** Unity + AR Foundation + ARCore Extensions.
- **Reason stated:** A unified environment for mesh rendering, AR camera, 3D objects, and the Geospatial API.
- **Alternatives mentioned:** Web-based implementation and Android Native.
- **Why alternatives were not selected:** The complete comparison and rejection rationale are not available in the accessible source. Do not fill the gap by guessing.
- **Status:** Prior assistant recommendation / provisional architecture; user approval and current implementation status need verification.

### Spatial data and backend architecture
- **Proposed components mentioned:** DEM-driven adaptive mesh, tiled/LOD rendering, Neon Postgres, and object storage.
- **Reason and alternatives:** Incomplete in the accessible source.
- **Status:** Proposal, not verified as provisioned or operational.

## Known limitations and unresolved questions
- The original full conversation and all linked project artifacts were not available in this reconstruction.
- The exact reason for choosing Vertical and later changing Flat to Follow is unknown.
- The full comparison behind Unity vs Web vs Android Native is missing.
- Backend and storage choices need a source-backed comparison and current implementation check.
- The web preview was explicitly described as not equivalent to ARCore/VPS/world-locked AR and did not yet contain a real terrain mesh; verify current state before treating this as current truth.

## Follow-up tasks
- Recover the original Monument architecture discussion and any project documents or code that establish the actual selected stack.
- Ask the decision owner for the missing rationale behind Vertical and Follow if it remains relevant.
- Compare Unity, Web, and Android Native using current requirements and record the full trade-offs.
- Verify the current status of DEM, mesh, tiles/LOD, Neon, and object storage against repositories and provider resources.
- Add device-based validation results and revisit triggers after prototype tests.

## Provenance note
This is a best-effort retrospective record based on limited accessible prior-conversation summaries. It deliberately preserves unknowns and must be amended when primary sources are recovered.
