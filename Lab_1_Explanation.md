Definitions of Agents in the Sequence System

1. `Part`

- Definition: The item or component that's undergoing the manufacturing process. It moves along the conveyor, is manipulated by various robotic systems, undergoes quality inspection, and is the primary object of interest in the production flow.

2. `Sensor`

- Definition: A device that detects or measures a physical property and records, indicates, or otherwise responds to it. In this context, it is used to detect the presence or position of the Part on the conveyor belt and may be involved in quality checks.

3. `Conveyor Belt`

- Definition: A mechanical system that moves the Part from one point to another within the manufacturing setup. It's a continuous loop of material that rotates over pulleys, facilitating the movement and positioning of the Part throughout various stages of the manufacturing process.

4. `Robotic Arm`

- Definition: An automated arm-like mechanism equipped with special tools or attachments. It can perform tasks such as picking up the Part, placing it in the assembly station, or moving it to various points in the manufacturing process. It follows commands sent from control systems or sensors.

5. `Assembly Robot (or Assembly Robotic Arm)`

- Definition: A specialized robot or robotic mechanism designed to assemble parts. In the context of this sequence, it collaborates with the standard Robotic Arm to assemble the Part. Its functions might include attaching components, soldering, screwing, and other assembly tasks.

6. `Operator`

- Definition: A human overseer or technician responsible for ensuring the smooth operation of the manufacturing process. The operator intervenes when alerted about malfunctions or issues, makes decisions on how to address problems, and may perform tasks like recalibration, maintenance, or manual inspections.

# Automated Part Production Flow Breakdown

## 1. Conveyor Movement

### Start of Conveyor

The `Part` requests the `Conveyor Belt` to start.

#### Failure Scenario

- The `Part` alerts the `Operator` regarding a conveyor issue.
- Maintenance steps in to address the issue.
- Once the issue is resolved, the `Operator` informs the `Part`.

## 2. Sensor Activation

### Part Detection by Sensor

- The `Sensor` detects the `Part` and sends a message to it.
- The `Part` then sends a command to the `Conveyor Belt` to stop.

#### Failure Scenario

- The `Part` alerts the `Operator` of a sensor issue.
- The sensor may need recalibration or replacement.
- Once the issue is resolved, the `Operator` informs the `Part`.

## 3. Robotic Arm Movement for Initial Handling

### Robotic Arm Handling

- The `Part` sends a command to the `Robotic Arm` to pick it up.
- The `Robotic Arm` acknowledges the command received.
- The `Part` then sends another command to the `Robotic Arm` to place it in the assembly station.
- The `Robotic Arm` confirms that the part has been placed.

#### Failure Scenario

- The `Part` alerts the `Operator` about the malfunction.
- Maintenance or rerouting is done to address the issue.
- Once resolved, the `Operator` informs the `Part`.

## 4. Part Assembly

### Start of Assembly

- The `Part` sends a command to the `Robotic Arm` to start the assembly.
- The `Robotic Arm` initiates assembly with the `Assembly Robot`.
- Once assembly is completed, the `Assembly Robot` informs the `Part`.

#### Failure Scenario

- The `Part` alerts the `Operator` about the assembly robot failure.
- The operator might intervene or reroute the process.
- Once resolved, the `Operator` informs the `Part`.

## 5. Quality Inspection

### Robotic Arm Movement for Quality Inspection

- The `Part` sends a command to the `Robotic Arm` to pick it up from the assembly station.
- The `Robotic Arm` acknowledges that the part has been picked.
- The `Part` then commands the `Robotic Arm` to move it to the `Sensor` for inspection.
- The `Robotic Arm` places the `Part` for inspection by the `Sensor`.

### Quality Check by Sensor

- The `Part` requests the `Sensor` to perform a quality check.
- The `Sensor` sends back the quality assessment result.

#### Success Scenario

- The `Part` commands the `Robotic Arm` to move it to the collection point.
- The `Robotic Arm` then delivers the `Part` to the final delivery location on the `Conveyor Belt`.

#### Exception Handling for Quality Issues

##### Assembly Error (like missing parts)

- The system tries sourcing the missing part from nearby storage.
- The part is buffered, allowing the system to handle other parts.
- The part is returned to the conveyor for reprocessing.

##### Improper Assembly

- The assembly robot attempts immediate rework.
- The part is flagged for manual inspection or repair.
- The part is returned to the assembly robot for reassembly.

##### Other Quality Issues

- The part is flagged for detailed inspection post conveyor cycle.
- The part is marked and set aside for future analysis.
- The part is rerouted back to the conveyor start for reprocessing.

![LAB_1 Solution to Autmoation Design into a UML](/out/Lab_1_order_flow/ManufacturingProcess.png)
