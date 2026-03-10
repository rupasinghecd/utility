# System Integration Checklist

## Purpose
Ensure a new microservice or MFE is introduced with clear integration, ownership, and runtime expectations.

## Checklist

### Architecture
- [ ] ownership boundary is clear
- [ ] APIs/routes/events are defined
- [ ] data ownership is defined
- [ ] alternatives were considered

### Security / Control
- [ ] entitlement model considered
- [ ] sensitive data handling considered
- [ ] audit requirements considered

### Integration
- [ ] upstream callers identified
- [ ] downstream dependencies identified
- [ ] event and API contract expectations defined
- [ ] compatibility concerns noted

### Delivery
- [ ] repo/module naming agreed
- [ ] setup/scaffold plan exists
- [ ] implementation tasks are sequenced
- [ ] rollout and rollback notes exist

### Operations
- [ ] logging expectations defined
- [ ] monitoring/watchpoints defined
- [ ] support ownership known
- [ ] release verification steps identified