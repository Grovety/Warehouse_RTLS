# System Overview

## Purpose

Warehouse Flow RTLS Demo is a warehouse HMI for Elecrow CrowPanel Advanced ESP32-P4 panels. Its main user is a supervisor or dispatcher observing the operation from a Warehouse Control Center.

The application connects the position of an asset with its role in the process: which load a vehicle is carrying, where it is going, what movement has occurred, and whether the result matches the intended operation.

**Location → Movement → Context → Event → Explanation → Corrected Flow**

The operator can move from the complete warehouse to one zone, vehicle, or pallet, then investigate the history behind an event.

## Warehouse Model

The demonstration represents a food distribution warehouse with cold storage areas.

| Area | Role |
| --- | --- |
| Receiving | Accepts incoming loads into the warehouse |
| Inbound Staging | Holds received pallets before storage |
| Cold Storage A / B | Stores pallets between handling operations |
| Outbound Staging | Collects loads before shipping |
| Dock 1–5 | Receives loads for shipment |

Normal internal transfers follow **Receiving → Inbound Staging → Cold Storage A/B → Outbound Staging → Dock**.

The model contains **25 pallet identities, four forklifts, and two pallet trucks**. Pallets move between zones and vehicles through pickup, transport, and unloading. Shipping and replenishment allow the operation to continue through successive cycles.

Vehicles, tasks, loads, and events belong to one connected simulation. Movement follows warehouse routes and task execution rather than independent random motion.

## Application Structure

### Title and Guided Demo

The startup Title screen offers two choices:

- **Guided Demo** starts a repeating presentation of warehouse movement, operational context, and RTLS location.
- **Interactive HMI** opens the warehouse interface and starts the simulation on the first entry.

The presentation uses its own visual examples. When entered from a running HMI, it pauses the warehouse operation and retains its state. Returning to the HMI continues that operation without advancing it by the time spent in the presentation.

### Interactive HMI

The two main sections are **Overview** and **Events**. Zone, vehicle, pallet, and Task Queue panels provide context within the interface. The **< DEMO** button returns to the startup presentation choices.

| View | Information |
| --- | --- |
| Warehouse Overview | Warehouse map, vehicle movement, queue indicators, active tasks, and exception markers |
| Zone Overview | Zone status, stored pallets, arrivals, departures, and recent activity |
| Vehicle Detail | Vehicle state, load, source, destination, transport progress, and recent activity |
| Pallet Detail | Pallet state and lifecycle, location, next step, and movement history |
| Task Queue | Exception, active, and waiting work, with links to the corresponding event or pallet |
| Live Events | Warehouse-wide event history, active exceptions, filters, and inline explanations |

## Queue Indicators and Tasks

The Overview strip contains **Inbound Queue**, **Active Tasks**, **Outbound Queue**, and **Exceptions**.

Inbound Queue describes queued inbound work at Inbound Staging; Outbound Queue describes queued shipping work at Outbound Staging. These indicators account for staged inventory and waiting work without counting the same pallet twice. They are not counts of all pallets or all vehicles in the warehouse.

The Task Queue separates **Exceptions**, **Active**, and **Waiting** work. An amber clock marks delayed waiting work. A delay is not automatically an exception, and a normal traffic wait does not by itself mean that a task has failed.

## Events and Explanation

Movement History belongs to one pallet. Live Events records significant operations across the whole warehouse, including deliveries, receiving, shipping, and exceptions.

Active exceptions remain visible separately from the filtered event history. A zone-associated exception highlights its location on Overview. Opening the event reveals a causal summary and a chronological evidence sequence.

The simulation introduces controlled deviations automatically. Examples include a destination becoming unavailable, delivery to the wrong destination, and a mismatch between actual storage and the assigned storage area.

Resolution follows the underlying condition. A wrong destination can require corrective transport; a storage mismatch can resolve by reconciling the assignment with the actual compatible storage area. The interface displays the outcome and evidence. Viewing a panel does not issue a recovery command.

## RTLS Technology Context

In a real deployment, mobile **UWB tags** and fixed **anchors** provide measurements to a locating engine, which calculates asset positions. A location hub can then supply that information to applications.

**omlox Hub** provides a common location model and REST/WebSocket interfaces across positioning technologies. Its vocabulary includes trackables, location providers, zones, and fences. **Open Location Hub** is a potential integration direction for adapting this concept to a real warehouse.

These are technology and integration concepts, not a connection implemented by the supplied demo package. The current application generates its warehouse data locally.

See the official descriptions of [omlox Core Zone](https://omlox.com/omlox-explained/omlox-core-zone-and-air-interface) and [omlox Hub and API](https://omlox.com/omlox-explained/omlox-hub-and-api).

## Current Boundaries

The demo is a concept prototype for evaluating a touchscreen warehouse interface. It does not include a real RTLS connection, production WMS integration, map editing, Event Replay, or manual scenario/recovery controls.

There is no separate Demo section inside Interactive HMI. Guided Demo is the startup presentation. The Settings button currently opens a placeholder; device settings are not configured in this release.

The public Windows package contains firmware **v1.7 for hardware V1.2**. Installation is described in the [README](README.md); practical operation is described in the [User Manual](USER_MANUAL.md).
