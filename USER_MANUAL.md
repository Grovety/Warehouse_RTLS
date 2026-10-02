# User Manual

## Start the Application

After installation and restart, the panel opens the Warehouse Flow Title screen.

1. Tap **INTERACTIVE HMI** to open the warehouse and start its simulation.
2. Alternatively, tap **GUIDED DEMO** to watch the presentation.
3. During the presentation, tap the screen to reveal **OPEN INTERACTIVE HMI**, then tap that action to enter the warehouse.

The warehouse operates automatically. You can inspect its state without assigning tasks or controlling vehicles.

## Warehouse Overview

Tap **Overview** in the top bar to view the warehouse map.

1. Review **Inbound Queue**, **Active Tasks**, **Outbound Queue**, and **Exceptions**.
2. Tap a zone to inspect its inventory and activity.
3. Tap a vehicle to inspect its load and current operation.
4. Tap **Task Queue** near the bottom of the map to inspect the work list.

An active zone-associated exception is shown with a red zone outline and an alarm marker. Tap the marker to open the related event. The **Exceptions** indicator provides another route to active events.

[![Overview with an active exception at Dock 5](images/warehouse-overview-exception.png)](images/warehouse-overview-exception.png)

This example highlights Dock 5. The map identifies the affected place; open the event to read its cause.

## Zone Overview

Tap a zone on the map.

1. Check **Status** and **Stored Pallets**.
2. Review **Arrived** and **Departed** on the ten-minute time rail.
3. Review the **Assets** list and **Recent Activity**.
4. Tap a pallet row to open its detail panel. Drag the list to scroll when needed.
5. If the zone's Status shows an active **Exception**, tap that block to inspect the related event.
6. Use the panel's close button to return to the map.

[![Cold Storage B inventory and recent arrivals and departures](images/zone-overview.png)](images/zone-overview.png)

The illustrated zone is Cold Storage B. Its pallet list and activity are live projections of the simulation.

## Vehicle Detail

Tap a forklift or pallet truck on the map.

- Check the vehicle ID and operating state.
- Follow **Pickup**, **Load**, **Transport**, and **Unload** progress.
- Review the current pallet, **From**, **To**, and **Recent Activity**.
- Tap a linked load card or loaded vehicle image to open the pallet.
- Tap linked source/destination cards to open the corresponding zone.

In the illustrated example in the [Project Description](description/description.md#vehicle--pallet-context), FL-02 is transporting P-706 from Receiving to Inbound. A vehicle with no load has no active pallet link.

## Pallet Detail

Open a pallet from a zone's Assets list, a vehicle's load card, or an ordinary Task Queue row.

- Check the pallet's status and lifecycle.
- Read **Current Location** and **Next Step**.
- Follow the available links to its vehicle or zone.
- Read **Movement History** to understand how it reached its current position.
- Use an available back arrow to return to the previous context panel, or close the panel to return to the map.

The pallet screenshot shows P-732 on pallet truck PT-02, with Cold Storage B as its next step. It is a different example from FL-02/P-706.

## Task Queue

Tap **Task Queue** on Overview.

1. Review the **Active** and **Waiting** groups. **Exceptions** appears when relevant task exceptions are present.
2. An amber clock identifies delayed waiting work; it does not mean the task has failed.
3. Tap an ordinary task row to inspect its pallet.
4. Tap an exception row to inspect its associated event.
5. Drag the list to scroll when it overflows; close the panel when finished.

[![Task Queue showing active and waiting work](images/task-queue.png)](images/task-queue.png)

The screenshot includes a delayed waiting row for P-357. Queue membership changes as work progresses.

## Live Events

Tap **Events** in the top bar.

1. Select **All**, **Inbound**, **Storage**, or **Outbound** to choose the history scope.
2. Enable **Exceptions Only** to restrict history to exceptions; disable it to include ordinary operations.
3. Scroll the history to inspect available records.
4. Tap an exception row to expand its explanation.

[![Live Events showing deliveries across warehouse processes](images/live-events.png)](images/live-events.png)

Active exceptions remain visible above history regardless of its filters. **All** means all retained process scopes, not an unlimited archive.

## Investigate an Exception

Start from a map marker, the Exceptions indicator, an exception task row, a zone's Exception status, or the Events section.

1. Open the active event and expand its row if it is not already expanded.
2. Read the summary to identify the mismatch or unavailable condition.
3. Follow the timestamped evidence to understand what happened.
4. After the condition resolves, find the event in history and expand it again to inspect the completed sequence.

[![Active Storage Mismatch for pallet P-364 and task TASK-132](images/exception-active.png)](images/exception-active.png)

Here P-364 was stored in Cold A instead of its assigned Cold B. The explanation reports assignment reconciliation in progress.

[![Resolved Storage Mismatch with assignment updated to Cold A](images/exception-resolved.png)](images/exception-resolved.png)

The same event later shows **Resolved**, with **Assignment updated** and **Issue resolved** evidence. The assignment was reconciled to Cold A; this example does not show a return transport to Cold B.

Tap the selected row again or outside its explanation to close it. These screens observe the simulation; there is no manual recovery button.

## Return to the Presentation

Tap **< DEMO** in the upper-left corner to return to the Title screen, then choose Guided Demo or Interactive HMI.

The running warehouse pauses while the presentation is open and resumes when you return. There is no separate Demo tab or Auto/Manual scenario selector inside Interactive HMI.

## Settings and Installation

The Settings button currently displays a placeholder. Wi-Fi, brightness, time, and volume controls are not configured in this release.

For package requirements, installation, and COM-port troubleshooting, see the [README](README.md).
