# System Map Extraction Policy

## Purpose
Define how architecture maps are bootstrapped from an MFE entrypoint when no service catalog exists.

## Inputs
One or more of:
- MFE repo/module name
- route path
- page/component path
- screen name
- API client file

## Extraction Order
1. Identify MFE entry boundary
2. Identify routes and screen ownership
3. Identify outbound API/integration calls
4. Map calls to backend services
5. Inspect backend services for downstream dependencies
6. Group findings into domains and journeys
7. Generate architecture map files

## Required Outputs
- mfe-catalog.md
- service-catalog.md
- domain-to-system-map.md
- journey-to-system-map.md
- repo-to-system-map.md

## Confidence Levels
- High: directly evidenced by code or config
- Medium: strongly inferred from naming and usage
- Low: possible secondary impact requiring confirmation

## Rules
- separate confirmed from inferred mappings
- include evidence for every generated mapping
- prefer route/client/controller evidence over naming guesses
- do not hide uncertainty