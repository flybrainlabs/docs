# Model cache and recovery

The browser keeps verified model resources and scientific records so that a later session can reuse them. These objects have different lifetimes and meanings. A model chunk is reusable execution input; a candidate output is the evidence of a particular computation; a snapshot is a recovery checkpoint.

## What is stored

| Object | Purpose | Important boundary |
| --- | --- | --- |
| Verified resource chunks | Avoid repeated complete downloads | Must match the expected digest and resource identity |
| Constructed model | Prepare execution efficiently | Must agree with graph and parameter roots |
| Background/result records | Preserve actual completed work | Retain original scope and numerical bytes |
| Pending output | Recover unfinished local delivery | Persistence alone does not prove server acceptance |
| V3 snapshot | Resume compatible computation state | Requires complete step boundaries and compatible identity |
| Wallet/session state | Scope browser actions | Separate from scientific results and economic beneficiary |

Persistent storage uses browser facilities, including the Origin Private File System where supported. It belongs to the site's origin and browser profile. A different browser, profile or origin is not automatically the same storage location.

## Download integrity and reuse

Resources are keyed with the expected digest so that an older cached representation cannot masquerade as the new one. The preparation path preserves a necessary full integrity check and chunk checks. Reusing a verified model does not waive integrity; it avoids fetching the same successful input again.

A digest mismatch should identify the affected resource and expected revision. The correct repair is a targeted resource check/retry. Clearing every model and result is not the default recovery operation.

## Save, export and restore

Use explicit save/export controls when you want a portable record. Retain the package and its declared task/model identities. A snapshot describes the actually completed step boundary; partial buffers are not a complete scientific result.

Restore only a compatible snapshot. If the model, numerical contract or task differs, keep the historical record and start a separate compatible path rather than silently rewriting the identity. Historical viewing reads stored observations and does not automatically launch new computation.

## Browser storage limitations

Storage quota depends on the browser, device and available disk. Private browsing may remove data when its session ends. Browser cleanup tools and operating-system storage pressure can evict site data. A browser permission to persist storage is not a backup of all your records.

When quota is low, stop adding new work, retain the currently saved evidence and export recoverable records if possible. Read the visible error and available storage before changing the worker count or retrying preparation. Repeated full downloads can make the situation worse.

## Local recovery versus server archives

The browser's cache and the authority's private archive are independent. A local output may still await upload; a retained server claim may still await verification or financial reconciliation. Use IDs to compare the two states.

Cloud backup/restart and synthetic browser recovery checks have passed in the documented scope. Recovery of a particular user's physical Android storage and the complete disaster-recovery drill remain separate acceptance items. See [Operations and recovery](/docs/operations/).
