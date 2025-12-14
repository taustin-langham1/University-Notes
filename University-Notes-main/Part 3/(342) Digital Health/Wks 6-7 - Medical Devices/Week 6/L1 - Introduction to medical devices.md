
## Taxonomy of medical devices and equipment


purpose?  - why? to detect/diagnose condition + guide initial  treatment plan 
how? one-off periodic or continuous measurement


**setting**
clinical - provided in a clinical setting - by professionals
outside formal healthcare environments including self-care & home-based treatment

**Purpose**
Assessment Devices - Assistive Devices - Therapeutic Devices - Surgical Devices
**Type**
Stationary/Fixed - Portable/Mobile - Wearable - Implantable

## What is / isn't an embedded system?

### is

specialised, directed system embedded in the hardware?

special type of computer system, which may be a subsystem

task specific - not general purpose:
	form factor
	Specific hardware features
	real-time response from input-to-output
	user interface
	operating environment / context of use

single application
often very long-lived

### isn't
a clinicians computer, tablet and/or phone


## whats inside an embedded system?

Often, a microcontroller
- cpu with RAM and non-volatile memory
- code to be executed, which we call firmware
- input and output ports with dedicated hardware in silicon to operate them
Other electronic components
- power supply
- sensors and/or actuators
- display and/or buttons
- communications

we often abbreviate microcontroller (unit) as MCU
sophisticated MCUs are sometimes called systems-on-chip (SoCs)


CODAL C++, CODAL runtime, Nordic NRF5 SDK, Hardware
i^2 C

CODAL provides: 
- eventing subsystem maps asynchronous hardware and software events to handlers
- non-preemptive fibre scheduler enables concurrency
- simple memory management system enables managed types
- drivers that abstract hardware features as software components
- parameterised object model that combines components to represent the micro:bit
