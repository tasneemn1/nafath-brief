Version: NAFATH-V2
Track:  Cybersecurity 

## Overview
Reliable 5G service for emergency response teams relies on coordinated decision-making to ensure availability during periods of congestion, cyberattacks, or infrastructure failures. Software engineering ensures that network-connected applications handle failed requests safely and restore service efficiently. Artificial intelligence enables congestion prediction, though its forecasts must be tested against novel data to enhance accuracy. Mobile applications designed for offline use must preserve essential data and accurately synchronize records once connectivity is restored. Networks utilize 5G network slicing technology to prioritize and allocate resources for emergency communications. Meanwhile, cybersecurity teams prepare to respond to incidents, repel attacks, contain threats, and restore operations. Finally, data engineering leverages regional and daily usage logs, enabling personnel to monitor demand and plan capacity as needed. These disciplines work in concert to ensure service continuity, informed decision-making, and secure emergency responses.
## Software
Safe HTTP methods—such as GET and HEAD—are characterized by being read-only. Idempotent methods include GET, HEAD, OPTIONS, TRACE, PUT, and DELETE; this means that repeating the same request produces the same intended effect as executing it once. This distinction is crucial in the event of connection failures, as automatically retrying operations that lack this property such as POST can lead to the repeated execution of actions. Consequently, operators should adopt appropriate retry policies and implement specific controls to ensure idempotency, particularly when handling sensitive requests.

Resource: IETF (2022), RFC 9110: HTTP Semantics, Sections 9.2.1–9.2.2. - https://www.rfc-editor.org/info/rfc9110/#section-9.2.1

## AI
Overfitting occurs during training when a machine learning model learns the training data too precisely, resulting in poor performance under unfamiliar network conditions. Repeatedly training and evaluating the model on different subsets of data—a process known as cross-validation—helps detect this issue. To predict congestion, the operator should evaluate performance across various time intervals and traffic levels. Temporal validation and a separate final test set can help assess the model's ability to generalize predictions to future network conditions.

Resource: Scikit-learn, Cross-validation: Evaluating Estimator Performance. -https://scikit-learn.org/stable/modules/cross_validation.html

## Mobile
The response application should be designed to function offline, enabling access to cached essential information and securely saving permitted updates locally during connectivity outages. Upon reconnection, the application must automatically synchronize queued changes, retry failed operations, and detect conflicting updates. Version numbers, timestamps, and clear conflict-resolution rules help maintain consistency. The user interface must clearly distinguish between saved, pending, and confirmed updates so that responders do not confuse unsynchronized information with data confirmed by the server.

Resource: Android Developers, Build an Offline-First App, sections on data synchronization and conflict resolution. - https://developer.android.com/topic/architecture/data-layer/offline-first
A Disaster Management System with Offline OSM Caching, Conflict- Aware Synchronization, and QR Code-based Emergency Location - https://ieeexplore.ieee.org/abstract/document/11708139

## Networking
5G network slicing technology enables the creation of logical networks with distinct capabilities and service requirements over a shared physical infrastructure. It allows operators to allocate a dedicated slice to emergency response teams—defining appropriate Quality of Service (QoS) targets, prioritizing data traffic, and isolating it from standard user traffic—thereby enhancing communication performance during congestion and increasing efficiency. However, slicing alone does not guarantee the prevention of all failures; operators must also protect the shared infrastructure and provide reliable power sources, transport links, and backup systems to ensure continuity.

Resource: 3GPP, TS 28.530: Management and Orchestration; Concepts, Use Cases and Requirements, Section 4.1.1. - https://www.etsi.org/deliver/etsi_ts/128500_128599/128530/17.06.00_60/ts_128530v170600p.pdf

## Cybersecurity
Incident response helps the operator manage cyberattacks and restore critical communications. Under NIST CSF 2.0, the relevant functions are Govern, Identify, Protect, Detect, Respond, and Recover. During an attack, the operator should detect suspicious activity, investigate its scope, contain affected systems, remove the threat, restore services safely, and review lessons learned. Preparation, clear responsibilities and tested recovery procedures help reduce downtime and prevent similar incidents from causing further disruption.

Resource: Nelson, A., Rekhi, S., Souppaya, M., & Scarfone, K. (2025). NIST SP 800-61 Rev. 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management. - https://csrc.nist.gov/pubs/sp/800/61/r3/final

## Data
A star schema stores measurable events in a central fact table connected directly to dimension tables, such as date and region. A snowflake schema normalizes dimensions into additional related tables, reducing some redundancy but requiring more joins. For daily regional service-usage reports, a star schema is generally preferable because its simpler structure supports straightforward queries and efficient business intelligence reporting. The fact table could record usage volume, date keys and region keys.

Resource: Levene, M., & Loizou, G. (2003). Why is the snowflake schema a good data warehouse design? Information Systems, 28(3), 225–240. - https://doi.org/10.1016/S0306-4379(02)00021-2

## Misconception in My Track
A common misconception in my track “Cyber Security”
 is that incident response ends once a cyberattack has been stopped. In reality, effective incident response also requires detecting and analyzing the incident, containing its impact, restoring affected services, and learning lessons to improve future security. For the emergency 5G service, stopping an attack is not enough if responders still cannot communicate reliably. The operator must verify service recovery and improve its defenses to reduce the risk of similar incidents. NIST SP 800-61 Rev. 3 supports this approach by emphasizing detection, response, recovery, and continuous improvement.

Resource: Nelson, A., Rekhi, S., Souppaya, M., & Scarfone, K. (2025). NIST SP 800-61 Rev. 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management. Section 2.1, “Incident Response Life Cycle Model,” PDF p. 5.- https://doi.org/10.6028/NIST.SP.800-61r3

## Open Question
How can a 5G emergency network defend itself against a sophisticated cyberattack while maintaining communications, even when its security systems are under attack?
