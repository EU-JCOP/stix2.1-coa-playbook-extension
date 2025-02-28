## A STIX 2.1 Extension Definition for Sharing Machine-Readable Security Playbooks through the Course of Action SDO

**This repository includes a STIX 2.1 nested property extension that augments the Course of Action (COA) STIX Domain Object (SDO) type with properties that allow describing, embedding, and sharing machine-readable security playbooks**. 

The decision to extend the Course of Action SDO was based on the facts that the terms security playbook and course of action are semantically very close (i.e., security playbook can be a subclass of course of action) and that extending an object allows making use of the existing specification-defined relationships, such as the ones between the Course of Action and other objects. In addition, a nested property extension allows a Course of Action instance to accommodate multiple playbooks of the same or different formats and creators and can be easily revoked or updated at a sub-component level when needed.


![](https://github.com/fovea-research/stix2.1-coa-playbook-extension/blob/main/images/STIX2.1-nested-property-extension.jpg)

The illustration above concisely explains what comprises an Extension Definition. The blue rectangles represent an instance of a COA SDO type with an extension. The red rectangle represents the associated Extension Definition object that provides information about the new or extended object type. The amber rectangle captures the normative definition of the extension, and it is a JSON schema.

### Reading Material

A technical report that explains in detail the extension can be found [HERE](https://docs.google.com/document/d/1KzEgviVLolA6Yt7YWfAv9f6TSMD33WgSo-US3YSHtyc/edit?usp=sharing).

### Extension Definition Files:
- [Example Instances](https://github.com/fovea-research/stix2.1-coa-playbook-extension/tree/main/examples)
- [Extension Definition Object](https://github.com/fovea-research/stix2.1-coa-playbook-extension/tree/main/extension-definition)
- [Normative Definition of the Extension - JSON Schema](https://github.com/fovea-research/stix2.1-coa-playbook-extension/tree/main/schema)

### Properties that Comprise the Nested Property Extension of the COA SDO to Support Sharing Machine-Readable Security Playbooks
| Property Name | Data Type | Description |
| :--- | :--- |:--- |
| **type** (required)| `string` | The value of this property **MUST** be `playbook`. |
| **extension_type** (required) | `string` | The value of this property **MUST** be `property-extension`. |
| **playbook_id** (required)| `string` | A value that (uniquely) identifies the playbook. If the playbook itself embeds an identifier then the `playbook_id` **SHOULD** use the same identifier (value). If not, the producer needs to generate a UUIDv4 for the playbook. |
| **created** (required)| `timestamp` | The time at which the extension (sub-component instance) was created. This may be different from the time at which the "parent" COA object instance was created. |
| **modified** (required)| `timestamp` | The time that this particular version of the extension (sub-component instance) was last modified. |
| **revoked** (optional)| `boolean` | A boolean that identifies if the extension (sub-component instance) is no longer valid. |
| **creator** (required)| `identifier` | The identifier of the entity that created this playbook. |
| **valid_from** (optional)| `timestamp` | The time from which the playbook is considered valid and the steps that it contains can be executed. |
| **valid_until** (optional)| `timestamp` | The time at which this playbook should no longer be considered a valid playbook to be executed. |
| **description** (optional)| `string` | An explanation, details, and more context about what this playbook does and tries to accomplish. |
| **labels** (optional)| `list` of type `string` | A set of labels for the playbook. |
| **playbook_impact** (optional)| `integer` | From 0 to 100, an integer representing the impact the playbook has on the organization. A value of 0 means specifically undefined. Values range from 1, the lowest impact, to a value of 100, the highest. For example, a purely investigative playbook that is non-invasive would have a low impact value of 1. In contrast, a playbook that performs changes such as adding rules into a firewall would have a higher impact value. |
| **playbook_severity** (optional)| `integer` | From 0 to 100, an integer representing the seriousness of the conditions that this playbook addresses. A value of 0 means specifically undefined. Values range from 1, the lowest severity, to a value of 100, the highest. |
| **playbook_priority** (optional)| `integer` | From 0 to 100, an integer representing the priority of this playbook relative to other defined playbooks. A value of 0 means specifically undefined. Values range from 1, the highest priority, to a value of 100, the lowest. |
| **organization_type** (optional)| `list` of type `open-vocab` | The type of organization that the playbook is intended for. The value for this property **SHOULD** come from the `industry-sector-ov` open vocabulary.|
| **playbook_type** (optional)| `list` of type `open-vocab` | The security-related functions the playbook addresses. A playbook may account for multiple types (e.g., detection and investigation). Open Vocabulary: `[notification, detection, investigation, prevention, mitigation, remediation,attack]` |
| **playbook_standard** (required)| `string` | The standard/format/nota tion the playbook conforms to (e.g., CACAO). |
| **playbook_abstraction** (optional)| `open-vocab` | The playbook’s level of abstraction. Open Vocabulary: `[template, executable]` |
| **playbook** (optional)| `string` | The entire playbook in its native format (e.g., CACAO JSON). Security playbook producers and consumers use this property to share and retrieve playbooks. |
| **playbook_base64** (optional)| `binary` | The entire playbook encoded in base64. Security playbook producers and consumers of playbooks use this property to share and retrieve playbooks.



## Maintainers
- Vasileios Mavroeidis

- Mateusz Zych
