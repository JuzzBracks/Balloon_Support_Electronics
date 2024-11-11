15 Feb 2023, testing with Shubh, James, Justin at MIL/UofAZ

- **The debouncing capacitors (on the relays) should be connected between VS and RTN.  The board design has them connected between VS and GND, which causes coupling between the various circuits.  Not clear if the *value* is optimal.**  We should make this change even if we plan to connect GND and RTN so that this works even without that change.
- Currently installed version of the current sensor seems to work, but we have the 2U current sensor (100 mV/A) installed; the schematic shows the 3U model.  We should boost the gain to the 400 mV/A version, since we're not going to run more than 10 A per circuit.
- The current monitor has a big offset (~500 mV).  Not clear from the data sheet if this is expected or whether there is something to fix it.  Doesn't matter that the power supply for the current monitor is the 5 V running the LabJack (relative to GND) but it is reading current from the Vicor (voltage relative to RTN).
- When RTN and GND are connected (referenced to same level), the voltage monitor behaves as expected.  Is there a way to make this happen when RTN and GND aren't connected?  The fundamental problem is that we want to measure VS-RTN (Vicor output) and the measuring circuit needs to have its ground referenced to RTN if we do the measurement single-ended.
Three possible solutions:
- Connect RTN and GND and the sensor only reads properly when these are connected.
- Differential amplifier for VS-RTN, and that amplifier is on the same power as LabJack.  
- separate the battery voltage to only power the Darlingtons and everything else on the relay board is referenced to RTN.

- Silkscreen for in the input is mislabeled: RTN -> GND, LJ-VCC -> RTN, VCC -> LJ-OUT (label -> reality)
- 


