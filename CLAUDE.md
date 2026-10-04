# Qiosk toolset conversion

This repository is being converted into a Qiosk toolset: an MCP server, over
streamable HTTP, deployed as a sidecar beside the iQ Client MCP Gateway.

**The guide is the specification.** Read, in full, before doing anything:
`~/repos/iquantiv/iq-client-mcp-gateway/docs/toolset-authoring.md`
Read only that file from that repository. Do not read or change anything else
there, and do not edit the guide.

- This repository: `~/repos/google_workspace_mcp`, row `5` of the guide's section 13.
  Convert this repository only.
- Toolset id (proposed): `google-workspace`

Rules that override anything else in this file:

1. Follow the guide's section 6 procedure, in order, on branch `qiosk/google-workspace`.
   Never push to the default branch.
2. The existing Arcade toolkit stays as it is and keeps working. Add the Qiosk
   sidecar beside it under `qiosk/`, with its own packaging, Dockerfile and image.
   Do not edit, move or remove the toolkit's code, packaging, deployment or Arcade
   registration, and do not retire the Arcade server: that is the orchestrator's
   later step. Its existing tests and entry point must still pass unchanged (C24).
3. Obey the guide's **Deployment gate** line. While it reads ORCHESTRATOR-RUN, stop
   at the guide's section 9: do not push an image, call the console API, install
   or deploy anything.
4. The sidecar holds no secret and mints no token. It forwards the caller's
   `Authorization: Bearer` value unchanged (guide sections 2 and 4).
5. Run every check in the guide's section 7. A failing check is fixed, not
   reported as acceptable.
6. Hand back exactly the guide's section 9 report to the orchestrator: repository,
   branch, commit SHA, CI run, image ID and base digest, the evidence that the
   existing toolkit is unchanged, toolset id, the tool list with proposed
   categories and scopes, the auth kind (or "none fits"), the install request, the
   conformance report, and every open question.
