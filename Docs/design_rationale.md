SoundStripe Design Rationale
SoundStripe is a low-cost immunoacoustic sensing platform for decentralized biofluid analysis in resource-limited settings. This document explains the engineering decisions behind the prototype hardware.
Design Objectives

Multi-modal acoustic sensing: Capture bulk acoustic properties (piezo) and airborne signatures (microphones) to analyze fluid viscosity, density, and immunochemical binding
Cost accessibility: Target BOM under $100 for replication in academic labs and field settings
Reproducibility: High SNR, calibrated gain stages, and reliable data logging for publishable results
ISEF safety compliance: Low voltage (≤12V), safe battery chemistry, no high-pressure/temperature components

Microcontroller: Feather M4 Express (ATSAMD51)

12-bit ADC at 1 MSPS: Handles audio sampling (44.1 kHz) without external ADC hardware
Native PDM interface: Hardware I2S/PDM support for direct microphone connection, no external clock generation
2MB QSPI flash + UF2 bootloader: Store calibration data and enable drag-and-drop USB programming without specialized hardware
Integrated LiPo management: Built-in charging circuitry reduces design complexity and fire risk vs. custom battery solutions

Rejected: Arduino Uno/Nano lack ADC resolution (10-bit), PDM support, and battery management. Cost savings negated by required peripherals.
Sensors: Piezo + Microphones
Piezoelectric Transducers (Enclosed Piezos)

Direct mechanical coupling: Transduce container vibrations, sensitive to acoustic impedance, viscosity, and resonance changes from immunochemical binding
High output voltage: Generate hundreds of mV without pre-amplification, simplifying analog front-end
Robustness and cost: <$1 each, mechanically durable, wide temperature range, ideal for field deployment
Reproducible mounting: Enclosed elements have consistent properties and standard dimensions for cross-lab replication

Rejected: Accelerometers (ADXL335, MPU6050) miss high-frequency acoustic signatures and add I2C complexity without performance benefit.
Acoustic Microphones
Electret microphones (MAX9814 AGC, MAX4466 adjustable): Analog outputs map directly to ADC, straightforward acquisition.

MAX9814 AGC: Automatic gain handles wide dynamic range without clipping, ideal for field deployment with varied signal levels
MAX4466 adjustable: Manual potentiometer enables precise gain calibration (25×–125×) for reproducible laboratory experiments
Cost efficiency: <$10 each, integrate mic element, pre-amp, biasing, and filtering—no custom analog design needed
Safety: 3.3V–5V operation, ISEF compliant

Adafruit PDM microphone: Digital-first approach.

High SNR (>60 dB): Digital bitstream immune to analog noise (power ripple, EMI, ground loops)
Hardware decoding: ATSAMD51 I2S peripheral handles PDM, producing clean 16-bit samples
Cable length flexibility: Digital signal less sensitive to capacitance/noise vs. analog
Future-proof: Simplifies PCB layout, reduces component count for productization

Rejected: I2S/I2C MEMS (ICS-43434, SPH0645) have negligible performance difference; PDM better documented in Adafruit ecosystem.
ADC vs. PDM: Dual Approach Rationale

Validation through redundancy: Independent acquisition pathways allow cross-validation—features appearing in both electret-ADC and PDM recordings increase confidence
Different noise profiles: Electret (analog front-end noise, ADC quantization) vs. PDM (jitter, decimation artifacts) help distinguish genuine signals from acquisition artifacts
Experimental flexibility: AGC for variable signal levels, fixed gain for calibration, high-SNR PDM for faint binding events—all available without hardware redesign
Educational value: Teaches analog vs. digital signal acquisition tradeoffs for ISEF/academic contexts

Rejected: Digital-only (PDM alone) limits experimental flexibility and eliminates cross-method validation critical for novel sensing research.
Amplifier Tradeoffs
MAX9814 AGC:

Automatically adjusts gain to prevent clipping/quantization noise, optimal for field use with unpredictable signals
Reduces operator burden—no electronics expertise needed
May introduce gain-pumping artifacts; variable noise floor complicates SNR analysis

MAX4466 Adjustable:

Fixed gain (25×–125×) ensures reproducible measurements across sessions
Optimizable for specific assays, maximizes ADC effective bits
Requires manual calibration but enables quantitative comparisons

Design philosophy: Both amplifiers accommodate exploratory field work (AGC) and rigorous lab validation (fixed gain). Users select based on experimental goals or run both in parallel.
Rejected: Programmable gain amplifiers (PGA2311, MCP6S21) add SPI complexity, cost, and potential firmware bugs. Hardware potentiometers provide simpler, more reliable control for research prototypes.
Data Logging: SD Card + USB
SD Card (autonomous logging):

Untethered field operation without computer dependency
High capacity (4GB = thousands of audio files), inexpensive ($5–10)
Faster data transfer than USB serial for large datasets
Structured file organization with metadata for complex experiments

USB Serial (PC tethering):

Real-time visualization during development/debugging
Streamlined lab workflow—data flows directly to analysis scripts
Lower power (no SD write bursts), better for long-duration experiments
Bidirectional control—PC can send commands without reflashing firmware

Implementation: Firmware supports both modes (compile-time or runtime selectable). Field researchers use SD logging; lab researchers use USB streaming; validation studies can run both simultaneously.
Rejected: WiFi/Bluetooth (ESP32, HC-05) add cost ($10–20), power draw (>100 mA), security concerns, and require network infrastructure absent in resource-limited settings.
Mechanical Mounting
Binder clip mounting:

Reproducible contact pressure via spring mechanism reduces measurement variability
Minimizes air gaps and acoustic impedance mismatches for better signal fidelity
Easy replication (standardized clip size/force)
Risk of over-damping high frequencies if too stiff

Tape/slack mounting:

Reduces mechanical loading, allows freer container vibration
Simple assembly, no tools required
Variable contact pressure causes drift and positioning sensitivity
Lower cost (no mechanical parts)

Recommended: Standardized binder clip protocol (documented size, placement, orientation) for research reproducibility. Design remains compatible with alternative mounting for exploratory work.
Rejected: Permanent epoxy bonding makes sensors single-use and prevents adjustment—incompatible with iterative research.
Power: LiPo Battery + USB
LiPo battery (3.7V):

Untethered field operation where electrical infrastructure is unavailable
1000 mAh provides several hours runtime (system draws ~70 mA nominal)
Integrated Feather M4 charging (MCP73831)—no external charger needed
ISEF compliant with built-in protection circuits (over-charge, over-discharge, over-current)

USB power:

Indefinite runtime for long-duration experiments
Simplifies development/debugging workflow
Ubiquitous availability (computer, wall adapter, USB battery pack)
Avoids LiPo wear during stationary lab use

Implementation: Feather M4 automatically switches between USB and battery, prioritizing USB. Battery charges when USB connected, seamlessly takes over if USB fails.
Rejected: Wall adapter with linear regulator (LM7805) eliminates portability, wastes power as heat, requires users to source correct supplies.
Prototyping Platform
Breadboard: Rapid reconfiguration during iteration, no soldering skill required, zero cost. Contact resistance can introduce intermittent noise.
Perma-Proto: Soldered connections ensure reliability for field deployment. Breadboard-compatible layout minimizes redesign. Sufficient for low-volume production (<100 units). Moderate cost ($5–8).
Workflow: Breadboard prototyping → breadboard validation → Perma-Proto transfer → custom PCB (if productized).
Rejected: Custom PCB from start requires upfront design investment ($50–200), weeks per iteration cycle—too rigid for evolving research design.
Enclosure: Weatherproof Housing

Fluid spill protection: Prevents electronics damage and ensures biosafety with biohazardous samples
Field deployment: IP54/IP65 rating enables operation in humid, dusty, or outdoor environments
Reproducibility: Standardized enclosure model documents cable routing and mounting for cross-lab replication
Professional appearance: Inspires confidence for demonstrations and clinical deployment

Cable pass-throughs via rubber grommets maintain environmental sealing. Transparent/easily opened lids enable inspection without disassembly.
Rejected: 3D-printed custom enclosure requires CAD design, iterative printing, and 3D printing access. Commodity enclosures are faster, cheaper, easier to replicate.
Key Alternatives Rejected
Raspberry Pi: Higher power (~500 mA vs. 40 mA), requires Linux OS, costs more ($35+ vs. $20), needs external ADC (no GPIO analog). Microcontroller more appropriate for low-power battery operation.
External ADCs (ADS1115, MCP3008): ATSAMD51's 12-bit ADC sufficient for amplified audio signals. External ADCs add cost, complexity, board space without meaningful performance gain.
Environmental sensors (DHT22, SHT31): Temperature/humidity monitoring deferred to later versions. Researchers can manually log ambient conditions if needed.
Wireless (ESP32, nRF52): Power draw (>100 mA), software complexity, security concerns, infrastructure dependency. Wired USB and SD logging simpler and more reliable for research prototype.
Built-in display (OLED, LCD): Adds power (20–50 mA), cost ($5–15), GUI development. Single LED status indicator sufficient for data acquisition focus.
GPS module: Geolocation valuable for field studies but adds cost ($15–30), power (~50 mA), requires sky view. Manual logging adequate for lab-focused prototype.
Reproducibility and Productization
These design choices support both research reproducibility and eventual productization. Commodity components (Adafruit breakouts, standard binder clips, common SD cards) enable cross-lab replication with identical hardware. Well-supported platforms (Feather M4, Arduino ecosystem) allow firmware sharing without modification. Breadboard/Perma-Proto transparency makes circuit verification straightforward.
The low-cost BOM ($80–100) demonstrates feasibility for resource-limited settings. Battery-powered SD logging proves autonomous field operation. Dual sensor modalities provide validation and robustness. Weatherproofing and LiPo safety consider real-world deployment from the outset.
Productization would consolidate breadboard circuitry onto custom PCB, integrate ATSAMD51 on-board, potentially eliminate redundant microphone pathways, and use injection-molded enclosures. However, the core architecture—low-power MCU, piezo + acoustic sensors, SD logging, LiPo power—remains unchanged, ensuring continuity from prototype to product.
