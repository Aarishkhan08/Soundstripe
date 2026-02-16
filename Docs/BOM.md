# Bill of Materials (BOM)
## SoundStripe Prototype

**Project:** SoundStripe Acoustic Detection System  
**Version:** 1.0  
**Date:** February 8, 2026  
**Prepared for:** ISEF Project Documentation

---

## Table 1: Electronics Components

| Component | Qty | Unit Price (USD) | Vendor | Part/Model | Link | Justification |
|-----------|-----|------------------|--------|------------|------|---------------|
| Adafruit Feather M4 Express | 1 | $22.95 | Adafruit | PID 3857 | https://www.adafruit.com/product/3857 | Primary microcontroller with ATSAMD51 Cortex M4 processor for real-time audio signal acquisition and data logging. Native USB and CircuitPython support simplify development. |
| Electret Microphone Amplifier - MAX9814 with Auto Gain Control | 1 | $7.95 | Adafruit | PID 1713 | https://www.adafruit.com/product/1713 | High-sensitivity microphone with automatic gain control for adaptive signal capture across varying acoustic intensities in fluid impact experiments. |
| Electret Microphone Amplifier - MAX4466 with Adjustable Gain | 1 | $6.95 | Adafruit | PID 1063 | https://www.adafruit.com/product/1063 | Manually adjustable gain amplifier for controlled sensitivity testing. Enables direct comparison of AGC vs. fixed-gain performance under identical conditions. |
| Adafruit PDM MEMS Microphone Breakout | 1 | $4.95 | Adafruit | PID 4346 | https://www.adafruit.com/product/4346 | Digital PDM output microphone offering superior noise immunity. Compact footprint suitable for multi-sensor array configurations and spatial acoustic mapping. |
| Small Enclosed Piezo Element with Wires | 2 | $1.50 | Adafruit | PID 1740 | https://www.adafruit.com/product/1740 | Contact-based vibration sensors for detecting substrate-transmitted acoustic signals. Provides orthogonal sensing modality to airborne microphone detection. |
| USB Audio Adapter - Works with Raspberry Pi | 1 | $4.95 | Adafruit | PID 1475 | https://www.adafruit.com/product/1475 | External USB sound card for reference recordings and ADC performance validation. Enables comparison between on-board sampling and commercial audio digitization. |
| Lithium Ion Polymer Battery - 3.7V 2500mAh | 1 | $14.95 | Adafruit | PID 328 | https://www.adafruit.com/product/328 | Rechargeable LiPo battery for portable operation during extended data collection sessions. 2500mAh capacity provides 4–6 hours of continuous logging. |
| Adafruit Micro SD SPI or SDIO Card Breakout Board | 1 | $7.50 | Adafruit | PID 4682 | https://www.adafruit.com/product/4682 | High-speed data storage interface for timestamped acoustic recordings. SPI/SDIO dual-mode supports fast write operations during continuous sampling. |
| MicroSD Card (16–64 GB) | 1 | $8.00 | SanDisk / Amazon | Class 10 UHS-I | https://www.amazon.com | Storage media for raw audio data and processed feature vectors. 16 GB minimum for multi-session experimental datasets. |
| Half-size Breadboard | 2 | $5.00 | Adafruit | PID 64 | https://www.adafruit.com/product/64 | Solderless prototyping platform for rapid circuit iteration. Dual breadboards accommodate sensor array and signal conditioning circuits simultaneously. |
| Perma-Proto Half-sized Breadboard PCB | 1 | $4.50 | Adafruit | PID 1609 | https://www.adafruit.com/product/1609 | Solderable breadboard layout for permanent prototype assembly. Transition platform from testing to stable deployment-ready circuit. |
| Premium Male/Male Jumper Wires - 40 x 6" (150mm) | 1 | $3.95 | Adafruit | PID 1957 | https://www.adafruit.com/product/1957 | High-quality interconnect wires for reliable analog signal transmission. Premium construction minimizes contact resistance and signal degradation. |
| Project Enclosure (ABS Plastic, 100 x 60 x 25 mm) | 1 | $6.50 | Hammond / Amazon | 1551 series or equiv. | https://www.amazon.com | Protective housing for electronics assembly. Enclosed design shields circuitry from accidental fluid contact during experimental procedures. |

**Subtotal (Electronics):** $99.65

---

## Table 2: Lab and Experimental Setup

| Component | Qty | Unit Price (USD) | Vendor | Part/Model | Link | Justification |
|-----------|-----|------------------|--------|------------|------|---------------|
| Chromatography Paper Strips (50-pack, 20 x 20 cm) | 1 pack | $18.95 | Fisher Scientific / Amazon | Whatman 3MM CHR | https://www.fishersci.com | Porous cellulose substrate for controlled acoustic propagation studies. Standardized material ensures reproducible experimental conditions across trials. |
| Laboratory Chain Clamp Holder with Stand | 1 set | $15.00 | Carolina Biological / Amazon | Universal Support Stand | https://www.carolina.com | Adjustable mounting system for sensor positioning and chromatography paper strip suspension. Enables precise control of drop height and impact geometry. |
| Adjustable Volume Pipettor (1000–5000 µL) | 1 | $45.00 | Fisher Scientific / Labsupplies | Eppendorf-style | https://www.fishersci.com | Precision liquid delivery for reproducible droplet generation across viscosity ranges. Variable volume accommodates testing protocols from 1–5 mL dispensing. |
| Digital Precision Scale (0.1 g resolution, 100 g capacity) | 1 | $22.00 | Amazon / Lab suppliers | AWS-100 or similar | https://www.amazon.com | Accurate mass measurement for fluid density characterization and solution preparation. 0.1 g precision enables verification of dispensed droplet mass. |
| Distilled Water (1 L) | 1 | $3.00 | Grocery / Pharmacy | N/A | Local retail | Baseline low-viscosity test fluid. Distilled grade minimizes contaminants that could affect acoustic properties or surface tension. |
| Glycerol USP Grade (500 mL) | 1 | $12.00 | Pharmacy / Amazon | USP/Food Grade | https://www.amazon.com | High-viscosity agent for glycerol-water solution preparation. Enables systematic viscosity variation across 1–50 cP range for classification experiments. |
| Whole Milk (1 quart) | 1 | $4.50 | Grocery store | N/A | Local retail | Complex emulsion test fluid with intermediate viscosity and protein content. Represents real-world biological fluid for sensor validation. |
| Unflavored Gelatin Powder (4 oz) | 1 | $5.50 | Grocery store | Knox or equivalent | Local retail | Gelling agent for viscoelastic fluid preparation. Concentration-dependent viscosity allows simulation of mucus-like consistency. |
| Micropipette Tips (200–1000 µL, 1000-pack) | 1 pack | $12.95 | Fisher Scientific / Amazon | Universal fit | https://www.fishersci.com | Disposable tips for contamination-free liquid handling between fluids. Large quantity supports extensive multi-fluid testing protocols. |
| Nitrile Gloves (100-pack, size M/L) | 1 box | $8.00 | Amazon / Pharmacy | Powder-free | https://www.amazon.com | Personal protective equipment and contamination prevention during fluid handling. Nitrile resists glycerol and other organic solvents. |
| Small Containers (10-pack, 50 mL) | 1 pack | $6.50 | Amazon / Lab suppliers | Polypropylene vials | https://www.amazon.com | Storage vessels for prepared solutions and intermediate fluid mixtures. Clear plastic enables visual inspection of homogeneity. |

**Subtotal (Lab/Experimental):** $153.40

---

## Table 3: Software and Development Tools

| Component | Qty | Unit Price (USD) | Vendor | Part/Model | Link | Justification |
|-----------|-----|------------------|--------|------------|------|---------------|
| Python 3 (with pip package manager) | 1 | Free | Python.org | Python 3.10+ | https://www.python.org | Core programming environment for signal processing, feature extraction, and machine learning pipeline development. Open-source and cross-platform. |
| NumPy | 1 | Free | PyPI | Latest stable | https://numpy.org | Fundamental library for numerical array operations and FFT-based spectral analysis of acoustic waveforms. |
| SciPy | 1 | Free | PyPI | Latest stable | https://scipy.org | Scientific computing library providing signal processing functions (filtering, spectrogram generation, peak detection) essential for audio feature extraction. |
| librosa | 1 | Free | PyPI | 0.10+ | https://librosa.org | Audio analysis library with MFCCs, spectral features, and onset detection algorithms. Industry-standard toolkit for acoustic machine learning. |
| Pandas | 1 | Free | PyPI | Latest stable | https://pandas.pydata.org | Data manipulation framework for organizing experimental metadata, feature matrices, and time-series acoustic measurements. |
| scikit-learn | 1 | Free | PyPI | 1.3+ | https://scikit-learn.org | Machine learning library for supervised classification (SVM, Random Forest, k-NN) and regression models. Includes train/test splitting and cross-validation utilities. |
| TensorFlow (optional, for deep learning) | 1 | Free | PyPI | 2.13+ | https://www.tensorflow.org | Deep learning framework for neural network-based acoustic classifiers. Optional alternative to scikit-learn for advanced pattern recognition. |
| Arduino IDE | 1 | Free | Arduino.cc | 2.0+ | https://www.arduino.cc | Integrated development environment for Feather M4 firmware programming. Supports direct microcontroller flashing and serial debugging. |
| CircuitPython (for Feather M4) | 1 | Free | Adafruit | 8.0+ | https://circuitpython.org | Python-based embedded firmware for rapid prototyping on Feather M4. Simplifies sensor interfacing and data logging without C/C++ compilation. |
| Mu Editor (optional, for CircuitPython) | 1 | Free | Mu Editor | Latest stable | https://codewith.mu | Beginner-friendly code editor with built-in serial console for CircuitPython development. Streamlines microcontroller code-test-debug workflow. |

**Subtotal (Software):** $0.00 (All open-source/free)

---

## Cost Summary

| Category | Subtotal (USD) |
|----------|----------------|
| Electronics Components | $99.65 |
| Lab and Experimental Setup | $153.40 |
| Software and Development Tools | $0.00 |
| **Estimated Total** | **$253.05** |

---

## Notes

1. **Multi-Modal Acoustic Sensing:** Three microphone types (MAX9814 AGC, MAX4466 manual gain, PDM digital) enable comparative performance analysis under varying signal conditions. Piezo sensors provide contact-mode vibration detection for substrate-coupled acoustics.

2. **Viscosity Testing Protocol:** Glycerol-water solutions enable systematic viscosity gradients (1–50 cP). Milk and gelatin solutions represent complex biological fluids with non-Newtonian rheology for real-world validation.

3. **Data Pipeline:** Feather M4 captures raw audio → MicroSD storage → Python/librosa feature extraction → scikit-learn classification. USB audio adapter serves as reference standard for validating on-board ADC performance.

4. **Experimental Design:** Chromatography paper provides consistent porous substrate. Adjustable pipettor ensures reproducible droplet volumes (1–5 mL). Clamp stand controls drop height for impact energy variation.

5. **Software Ecosystem:** Open-source Python stack (NumPy, SciPy, librosa, scikit-learn) provides professional-grade audio analysis without licensing costs. TensorFlow optional for deep learning approaches.

6. **CircuitPython Advantage:** High-level Python syntax on Feather M4 accelerates firmware development compared to Arduino C++. Ideal for rapid sensor integration and logging algorithm iteration.

7. **Safety and Contamination Control:** Nitrile gloves protect against skin contact with glycerol and test fluids. Disposable pipette tips prevent cross-contamination between solutions.

8. **Budget Compliance:** Total hardware cost $253.05 maintains accessibility for student research while incorporating professional data acquisition and multiple sensor modalities.
