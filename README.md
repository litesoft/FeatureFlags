# FeatureFlags
Commentary/Thoughts on Feature Flags 

Feature Flags can be categorized on three dimensions:
1. How often will it need to deliver different outcomes based on context changes (e.g. by user / organization / groupings) -- its **dynamism**.
2. Who (role) should be responsible for managing the flag -- its **ownership**.
3. How long will it have to exist (creation thru removal) -- its **longevity**.  The Types below are placed in one of the following longevity buckets:
   1. Short-term
   2. Medium-term
   3. Long-term
   4. Permanent

Each type of Flag should support: 
* Activation Limited based on Random Users (percentage), or User Groups: By user characteristics &/ companies (supports Progressive/Ring deployments)
* Activation Limited based on Environment: Dev, QA, UAT, Prod-Group1, Prod-Group2
* Expiration Dates (except permanent ones: "Safety Valves", "DevOps Controls", & possibly "Permissioning")

## Types of Flags:

1. Experiment (A/B Enhancement Testing): Short-term (It is nice to allow users to opt-out of the testing -- if testing a proposed improved user experience -- this option can be inappropriate, e.g. statistic based testing for engagement enhancement).
2. Release (New Feature): Medium-term (often heavily Environment based)
3. Sunsetting (Old Feature): Medium-term
4. Permissioning (Custom Feature Disablement/Enablement) (e.g. Newbie vs Power User, Detail Level of Errors, or Free Trials): Long-term (possibly permanent)
>DevOps Group:
5. Migration Support (behaviour same -- code changed): Short-term
6. Safety Valves (Circuit Breakers / Kill Switches / Maintenance Window Shutdown Warnings): Permanent
7. DevOps Controls (e.g. Logging (two binary flags by code area): LoggingEnabled, LoggingVerbose): Permanent (until the "code area" is removed) 

> Note: Each of the above *Types* should have its own Enum in the application (the flag name is the combination: {Enum type}.{Enum entry name} )

General Questions:

* Do we need "Multivariate Flags" (non-binary, e.g. Logging about that has 3 options: Disabled, Regular, & Verbose)?
* Who are the stakeholders besides developers? (Ops, Product, Business, Sales, etc)
* Do we need scheduled flag change
* With "expiration dates" on most of the flags, should we create "time bombs" which will fail a test if a feature flag is still around after its expiration date.
* ...

Custom Built/Augmentation Questions:

* Should we support "Group Control Flags"? -- Flags that are not visible to the code, but reference a Group of other (binary) flags AND forces all the Group members to have the same value as the Group Control Flag (by definition a binary flag).
* Should we support "Cascading Flags"? -- “This flag is evaluated only if another flag is true.”
* Do we need both scheduled timed release of flag changes and emergency release (minimize flag value variation in production)? 
* ...


Feature Flag Glossary: https://featureflags.io/feature-flag-glossary/

See Graphs: https://martinfowler.com/articles/feature-toggles.html