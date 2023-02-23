# FeatureFlags
Commentary/Thoughts on Feature Flags 

Each type of Flag should support: 
* Activation Limited based on User Groups: By user characteristics &/ companies (supports Progressive/Ring deployments)
* Activation Limited based on Environment: Dev, QA, UAT, Prod-Group1, Prod-Group2
* Expiration Dates (except )

## Types of Flags:

1. A/B Enhancement Testing (Experiment): Short-term (It is nice to allow users to opt-out of the testing -- if testing a proposed improved user experience -- this option can be inappropriate, e.g. statistic based testing for engagement enhancement).
2. Migration Support (Ops) (behaviour same -- code changed): Short-term
3. Sunsetting a Feature: Short-term
4. New Feature (Release): Medium-term (often heavily Environment based)
5. Custom Feature Disablement/Enablement (Permission) (e.g. Newbie vs Power User, Detail Level of Errors, or Free Trials): Long-term (possibly permanent)
6. Safety Valves (Ops) (Circuit Breakers / Kill Switches / Maintenance Window Shutdown Warnings): Permanent
7. DevOps Controls (Ops) (e.g. Logging (two binary flags by code area): LoggingEnabled, LoggingVerbose): Permanent (until the "code area" is removed) 


> Note: Each of the above *Types* should have its own Enum in the application (the flag name is the combination: {Enum type}.{Enum entry name} )

General Questions:

* Do we need "Multivariate Flags" (non-binary, e.g. Logging about that has 3 options: Disabled, Regular, & Verbose)?
* Who are the stakeholders besides developers? (Ops, Product, Business, Sales, etc)
* Do we need scheduled flag change
* ...

Custom Built/Augmentation Questions:

* Should we support "Group Control Flags"? -- Flags that are not visible to the code, but reference a Group of other (binary) flags AND forces all the Group members to have the same value as the Group Control Flag (by definition a binary flag).
* Should we support "Cascading Flags"? -- “This flag is evaluated only if another flag is true.”
* Do we need both scheduled timed release of flag changes and emergency release (minimize flag value variation in production)? 
* ...


Feature Flag Glossary: https://featureflags.io/feature-flag-glossary/