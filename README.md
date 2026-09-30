# Monotron Duo Controller

Experimental firmware and interface hardware for controlling a Korg monotron
DUO from an M5Stack Cardputer-ADV.

The first usable version will turn the Cardputer keyboard into a calibrated
pitch-and-gate controller. Later slices add sequencing, BLE MIDI input, and USB
MIDI host support without changing the Monotron-facing interface.

## Intended signal path

```text
Cardputer keyboard / BLE MIDI / USB MIDI
                    |
                    v
             note and gate events
                    |
          +---------+----------+
          |                    |
          v                    v
      MCP4725 DAC         protected GPIO
          |                    |
          v                    v
     monotron Vrib        monotron Gate
```

The project treats the monotron DUO as an instrument, the MIDI transports as
event sources, and the MCP4725/Gate circuit as a hardware output backend.

## Safety boundary

- Never connect an unmeasured Monotron test point directly to an ESP32 GPIO.
- Establish a common ground only after confirming the relevant voltages.
- Use series resistance and a buffered/protected gate interface.
- Start every DAC test at zero output and raise it gradually.
- Do not power the Monotron through this project during the first experiments.
- Remove batteries and external power before soldering or changing wiring.

## Plan

The staged implementation plan and the acceptance criteria for every slice are
in [docs/plan.md](docs/plan.md).

## Status

Slice 0: project plan created; hardware characterization has not started.

