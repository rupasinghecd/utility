# Library Consumer Checklist

## Purpose
Ensure a Spring library is safe and practical for consuming services.

## Checklist

### Design
- [ ] library purpose is clear
- [ ] public API is small and understandable
- [ ] responsibilities between library and consumer are clear

### Spring Behavior
- [ ] configuration properties are documented
- [ ] autoconfiguration is conditional and predictable
- [ ] consumers can override where needed
- [ ] startup/runtime behavior is explicit

### Dependencies
- [ ] transitive dependencies are acceptable
- [ ] no service-specific domain dependency leaked
- [ ] Java/Spring compatibility is clear

### Safety
- [ ] logging does not expose sensitive data
- [ ] audit/security behavior is explicit
- [ ] misconfiguration fails clearly

### Adoption
- [ ] first pilot consumer identified
- [ ] upgrade path is defined
- [ ] versioning strategy is defined
- [ ] rollback/removal path is understood

### Testing
- [ ] unit tests exist
- [ ] Spring integration tests exist
- [ ] sample consumer validation exists