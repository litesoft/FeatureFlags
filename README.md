# FeatureFlags
Commentary/Thoughts on Feature Flags 

Each type of Flag should support: 
* Activation Limited based on User Groups: By user characteristics &/ companies (supports Progressive/Ring deployments)
* Activation Limited based on Environment: Dev, QA, UAT, Prod-Blue, Prod-Green
* Expiration Dates

## Types of Flags:

1. A/B Enhancement Testing: Short-term
2. Migration Support (behaviour same -- code changed): Short-term
3. New Feature: Medium-term (often heavily Environment based)
4. Custom Feature Disablement/Enablement (e.g. Detail Level of Errors): Long-term (possibly permanent)
5. Safety Valves (Circuit Breakers / Kill Switches): Permanent


> Note: Each of the above *Types* should have its own Enum in the application (the enum name is the combination: {Enum type}.{Enum entry name} )