# Awesome Invasive BCI Decoding [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of papers, datasets, benchmarks, and tools for **invasive brain–computer interface (iBCI) neural decoding** — intracortical microelectrode arrays, ECoG, stereo-EEG, and high-density silicon probes.

Invasive BCIs record neural activity directly from the cortex (or deeper structures) and decode it into control signals, text, speech, or movement. This list focuses on the **decoding** side: the algorithms, models, datasets, and systems that turn spikes and field potentials into intended actions. Non-invasive modalities (EEG / MEG / fNIRS) are intentionally out of scope here — see [Non-Invasive (coming soon)](#non-invasive-bci-coming-soon).

**Legend:** 📄 paper · 💻 code · 📊 dataset · 🏆 benchmark · 📚 survey

> ⚠️ Maintenance note: every link is meant to point at a real paper / repo. If you find a dead link or a paper that belongs in a different bucket, please open an issue or PR — see [Contributing](#contributing).

---

## Contents

- [How This List Is Organized](#how-this-list-is-organized)
- [Surveys & Reviews](#surveys--reviews)
- [By Acquisition Modality](#1-by-acquisition-modality-采集方式)
  - [Intracortical Microelectrode Arrays](#intracortical-microelectrode-arrays-utah--microwire)
  - [ECoG (Electrocorticography)](#ecog-electrocorticography)
  - [Stereo-EEG / Depth Electrodes](#stereo-eeg--depth-electrodes)
  - [Neuropixels / High-Density Probes](#neuropixels--high-density-silicon-probes)
- [By Task](#2-by-task-任务)
  - [Motor Decoding](#motor-decoding-运动解码)
  - [Speech & Language Decoding](#speech--language-decoding-语音与语言解码)
  - [Visual Decoding & Prosthesis](#visual-decoding--prosthesis-视觉解码)
  - [Affective / Memory / Cognitive State](#affective--memory--cognitive-state-情绪记忆认知)
- [By Research Direction](#3-by-research-direction-研究方向)
  - [Decoding Algorithms & Methods](#decoding-algorithms--methods-纯解码)
  - [Neural Foundation Models](#neural-foundation-models-神经基础模型)
  - [Latent Dynamics Models](#latent-dynamics-models-神经流形与动力学)
  - [Long-Term Stability & Recalibration](#long-term-stability--recalibration-长期稳定性)
  - [Cross-Subject / Cross-Session Transfer](#cross-subject--cross-session-transfer-跨被试跨会话迁移)
  - [Self-Supervised & Representation Learning](#self-supervised--representation-learning-自监督表征学习)
  - [Neural Data Generation & Synthesis](#neural-data-generation--synthesis-数据生成)
  - [Closed-Loop & Co-Adaptation](#closed-loop--co-adaptation-闭环与协同自适应)
  - [LLM / Multimodal / Diffusion Decoding](#llm--multimodal--diffusion-decoding-大模型与多模态)
  - [Real-Time / Adaptive Systems](#real-time--adaptive-systems-实时与自适应)
  - [China Teams](#china-teams-国内团队)
- [Datasets](#datasets-数据集)
- [Benchmarks & Competitions](#benchmarks--competitions-基准与竞赛)
- [Tools & Libraries](#tools--libraries-工具与库)
- [Recommended Venues](#recommended-venues-推荐会议与期刊)
- [Non-Invasive BCI (coming soon)](#non-invasive-bci-coming-soon)
- [Contributing](#contributing)

---

## How This List Is Organized

A single paper often spans multiple axes (e.g. *Willett 2023* is **intracortical** + **speech** + a **decoding-method** contribution). To avoid forcing every paper into one box, this list is organized along **three orthogonal axes**, and landmark papers are cross-listed where it helps:

1. **[By Acquisition Modality](#1-by-acquisition-modality-采集方式)** — how the neural signal is recorded (intracortical array, ECoG, sEEG, Neuropixels).
2. **[By Task](#2-by-task-任务)** — what is being decoded (movement, speech, vision, cognitive state).
3. **[By Research Direction](#3-by-research-direction-研究方向)** — the scientific/engineering problem being tackled (pure decoding, foundation models, long-term stability, data generation, …).

If you only want the milestones, start with [Surveys & Reviews](#surveys--reviews) then [Motor Decoding](#motor-decoding-运动解码) and [Speech & Language Decoding](#speech--language-decoding-语音与语言解码).

---

## Surveys & Reviews

- 📚 **Human intracortical recording and neural decoding for brain–computer interfaces** (Brandman, Cash & Hochberg, 2017, IEEE TNSRE) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC5815832/)
- 📚 **Computation Through Neural Population Dynamics** (Vyas, Golub, Sussillo & Shenoy, 2020, Annual Review of Neuroscience) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7402639/)
- 📚 **Neural Decoding for Intracortical Brain–Computer Interfaces** (2023, Cyborg and Bionic Systems) — [paper](https://spj.science.org/doi/10.34133/cbsystems.0044)
- 📚 **The speech neuroprosthesis** (Silva, Liu & Chang, 2024, Nature Reviews Neuroscience) — [paper](https://pubmed.ncbi.nlm.nih.gov/38745103/)
- 📚 **Restoring Speech Using Brain–Computer Interfaces** (2024, Annual Review of Biomedical Engineering) — [paper](https://www.annualreviews.org/content/journals/10.1146/annurev-bioeng-110122-012818)
- 📚 **The expanding repertoire of brain–computer interfaces** (2024, Nature Medicine) — [paper](https://www.nature.com/articles/s41591-024-03440-6)
- 📚 **The speech neuroprosthesis** (Luo, Anumanchipalli & Chang, 2024, Nature Reviews Neuroscience) — review of speech-decoding BCIs and articulatory representations. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC11540306/)
- 📚 **Development of visual neuroprostheses: trends and challenges** (Fernández et al., 2020, Bioelectronic Medicine) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7098238/)
- 📚 **Implantable intracortical microelectrodes: reviewing the present with a focus on the future** (2022, Microsystems & Nanoengineering) — electrode tech, biocompatibility, longevity. [paper](https://www.nature.com/articles/s41378-022-00451-6)
- 📚 **Foundation and large-scale AI models in neuroscience** (2025, arXiv) — survey of brain foundation models & large-scale pretraining. [paper](https://arxiv.org/html/2510.16658v1)

---

## 1. By Acquisition Modality (采集方式)

### Intracortical Microelectrode Arrays (Utah / microwire)

Single-/multi-unit spikes and threshold crossings from penetrating arrays (typically M1, PMd, PPC, or speech motor cortex).

- 📄 **Neuronal ensemble control of prosthetic devices by a human with tetraplegia** (Hochberg / BrainGate, 2006, Nature) — first human Utah-array cursor + prosthetic control. [paper](https://pubmed.ncbi.nlm.nih.gov/16838014/)
- 📄 **Reach and grasp by people with tetraplegia using a neurally controlled robotic arm** (Hochberg / BrainGate, 2012, Nature) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC3640850/)
- 📄 **High-performance neuroprosthetic control by an individual with tetraplegia** (Collinger / Schwartz, 2013, The Lancet) — 7-DoF prosthetic limb. [paper](https://pubmed.ncbi.nlm.nih.gov/23253623/)
- 📄 **Decoding motor imagery from the posterior parietal cortex of a tetraplegic human** (Aflalo / Andersen, 2015, Science) — opened PPC as an implant site. [paper](https://www.science.org/doi/10.1126/science.aaa5417)
- 📄 **High-performance brain-to-text communication via handwriting** (Willett / Shenoy, 2021, Nature) — 90 char/min. [paper](https://www.nature.com/articles/s41586-021-03506-2) · [💻 code](https://github.com/fwillett/handwritingBCI)
- 📄 **A high-performance speech neuroprosthesis** (Willett / Henderson, 2023, Nature) — 62 words/min, 125k vocab. [paper](https://www.nature.com/articles/s41586-023-06377-x) · [💻 code](https://github.com/fwillett/speechBCI)
- 📄 **A Year of Telepathy — Neuralink N1 / PRIME study** (Neuralink, 2024) — first human flexible-thread implant for cursor control. [report](https://neuralink.com/updates/a-year-of-telepathy/)
- 📄 **Fully implanted brain–computer interface in a locked-in patient with ALS** (Vansteensel et al., 2016, NEJM) — first fully-implanted home-use communication BCI. [paper](https://www.nejm.org/doi/full/10.1056/NEJMoa1608085)
- 📄 **The Stentrode endovascular BCI: SWITCH study safety and feasibility** (Oxley / Opie, 2023, JAMA Neurology) — first-in-human minimally invasive endovascular (stent-mounted) BCI. [paper](https://pubmed.ncbi.nlm.nih.gov/36622685/)

### ECoG (Electrocorticography)

Subdural / surface high-density grids — broad spatial coverage of speech & sensorimotor cortex.

- 📄 **Speech synthesis from neural decoding of spoken sentences** (Anumanchipalli / Chartier / Chang, 2019, Nature) — articulatory-intermediate speech synthesis. [paper](https://www.nature.com/articles/s41586-019-1119-1)
- 📄 **Machine translation of cortical activity to text with an encoder–decoder framework** (Makin / Chang, 2020, Nature Neuroscience) — WER as low as 3%. [paper](https://pubmed.ncbi.nlm.nih.gov/32231340/)
- 📄 **Neuroprosthesis for decoding speech in a paralyzed person with anarthria** (Moses / Chang, 2021, NEJM) — first real-time sentence decoding in a paralyzed patient. [paper](https://www.nejm.org/doi/full/10.1056/NEJMoa2027540)
- 📄 **A high-performance neuroprosthesis for speech decoding and avatar control** (Metzger / Chang, 2023, Nature) — text + synthesized voice + avatar. [paper](https://www.nature.com/articles/s41586-023-06443-4)
- 📄 **Walking naturally after spinal cord injury using a brain–spine interface** (Lorach / Courtine, 2023, Nature) — ECoG-driven digital bridge to spinal stimulation. [paper](https://www.nature.com/articles/s41586-023-06094-5)

### Stereo-EEG / Depth Electrodes

Sparse depth contacts (often clinical epilepsy implants) used opportunistically for decoding.

- 📄 **Real-time synthesis of imagined speech processes from minimally invasive recordings** (Angrick / Herff, 2021, Communications Biology) — closed-loop sEEG speech synthesis. [paper](https://www.nature.com/articles/s42003-021-02578-0) · [💻 code](https://github.com/cognitive-systems-lab/closed-loop-seeg-speech-synthesis)
- 📄 **BrainBERT: self-supervised representation learning for intracranial recordings** (Wang et al., 2023, ICLR) — pretrained on unlabeled intracranial (sEEG/ECoG) recordings. [paper](https://arxiv.org/abs/2302.14367) · [💻 code](https://github.com/czlwang/BrainBERT)
- 📄 **Brant: foundation model for intracranial neural signal** (Zhang et al., 2023, NeurIPS) — large intracranial pretrained model. [paper](https://openreview.net/forum?id=DDkl9vaJyE) · [💻 code](https://zju-brainnet.github.io/Brant.github.io/)

### Neuropixels / High-Density Silicon Probes

Hundreds–thousands of channels; dominant in rodent/NHP systems neuroscience and increasingly in human research.

- 📄 **Single-neuron speech sound encoding across the depth of human cortex** (Leonard / Chang, 2023, Nature) — Neuropixels in humans reveal single-neuron speech tuning across cortical depth. [paper](https://www.nature.com/articles/s41586-023-06839-2)
- 📄 **Ultraflexible electrode arrays for months-long high-density recording** (Luan / Xie, 2022, Nature Communications) — penetrating ultraflexible arrays stably record thousands of neurons for months. [paper](https://pubmed.ncbi.nlm.nih.gov/36192597/)
- 📊 **Allen Brain Observatory — Visual Coding Neuropixels** (Allen Institute, 2019) — see [Datasets](#datasets-数据集).
- 📊 **International Brain Laboratory (IBL) brain-wide map** (IBL, 2021) — see [Datasets](#datasets-数据集).
- 💻 **Kilosort** — GPU spike sorting with drift correction for HD probes; see [Tools](#tools--libraries-工具与库).

---

## 2. By Task (任务)

### Motor Decoding (运动解码)

**Cursor / typing**

- 📄 **High-performance communication by people with paralysis using an intracortical BCI** (Pandarinath / Jarosiewicz, 2017, eLife) — point-and-click typing. [paper](https://elifesciences.org/articles/18554)
- 📄 **A high-performance neural prosthesis enabled by control algorithm design (ReFIT-KF)** (Gilja / Shenoy, 2012, Nature Neuroscience) — closed-loop intention-retrained Kalman filter. [paper](https://pubmed.ncbi.nlm.nih.gov/23160043/)
- 📄 **Advantages of closed-loop calibration in intracortical BCIs for people with tetraplegia** (Jarosiewicz et al., 2013, J. Neural Eng.) — established closed-loop > open-loop calibration. [paper](https://iopscience.iop.org/article/10.1088/1741-2560/10/4/046012/pdf)
- 📄 **Clinical translation of a high-performance neural prosthesis** (Gilja et al., 2015, Nature Medicine) — first clinical translation of ReFIT to an ALS participant. [paper](https://pubmed.ncbi.nlm.nih.gov/26413781/)
- 📄 **Rapid calibration of an intracortical BCI for people with tetraplegia** (Brandman et al., 2018, J. Neural Eng.) — sub-3-minute decoder calibration. [paper](https://pubmed.ncbi.nlm.nih.gov/29363625/)
- 📄 **Cortical control of a tablet computer by people with paralysis** (Nuyujukian et al., 2018, PLOS ONE) — iBCI control of an unmodified commercial tablet. [paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0204566)
- 📄 **Brain control of bimanual movement enabled by recurrent neural networks** (Deo / BrainGate, 2024, Scientific Reports) — two cursors via RNN. [paper](https://www.nature.com/articles/s41598-024-51617-3)

**Robotic arm / prosthesis**

- 📄 **Direct cortical control of 3D neuroprosthetic devices** (Taylor / Tillery / Schwartz, 2002, Science) — foundational 3D cortical device control. [paper](https://www.science.org/doi/10.1126/science.1070291)
- 📄 **Cortical control of a prosthetic arm for self-feeding** (Velliste / Schwartz, 2008, Nature) — [paper](https://pubmed.ncbi.nlm.nih.gov/18509337/)
- 📄 **Robust decoding of hand kinematics from entire spiking activity using deep learning** (Ahmadi / Constandinou, 2021, J. Neural Eng.) — quasi-RNN on ESA for chronically robust kinematics. [paper](https://iopscience.iop.org/article/10.1088/1741-2552/abde8a)
- 📄 **Real-time NHP BCI achieves high-velocity prosthetic finger movements** (Nason-Tomaszewski / Chestek, 2022, Nature Communications) — shallow FFN beats ReFIT-KF. [paper](https://www.nature.com/articles/s41467-022-34452-w)
- 📄 **A high-performance BCI for finger decoding and quadcopter control** (Stanford / BrainGate, 2024, Nature Medicine) — independent finger groups. [paper](https://www.nature.com/articles/s41591-024-03341-8)
- 📄 **Decoding ten-finger movements in human PPC and motor cortex** (Caltech / Andersen, 2023, J. Neural Eng.) — [paper](https://iopscience.iop.org/article/10.1088/1741-2552/acd3b1)

**Handwriting**

- 📄 **High-performance brain-to-text communication via handwriting** (Willett / Shenoy, 2021, Nature) — [paper](https://www.nature.com/articles/s41586-021-03506-2) · [💻 code](https://github.com/fwillett/handwritingBCI)

**FES / walking / somatosensory feedback**

- 📄 **Restoring cortical control of functional movement in a human with quadriplegia** (Bouton, 2016, Nature) — cortex→FES neural bypass. [paper](https://pubmed.ncbi.nlm.nih.gov/27074513/)
- 📄 **Restoration of reaching and grasping through brain-controlled muscle stimulation** (Ajiboye / Hochberg, 2017, The Lancet) — [paper](https://pubmed.ncbi.nlm.nih.gov/28363483/)
- 📄 **Intracortical microstimulation of human somatosensory cortex** (Flesher / Gaunt, 2016, Science Translational Medicine) — bidirectional BCI tactile feedback. [paper](https://www.science.org/doi/abs/10.1126/scitranslmed.aaf8083)
- 📄 **Stable, precise tactile sensations via multi-electrode ICMS of S1** (2024, Nature Biomedical Engineering) — [paper](https://www.nature.com/articles/s41551-024-01299-z)
- 📄 **Walking naturally after spinal cord injury using a brain–spine interface** (Lorach / Courtine, 2023, Nature) — ECoG-driven digital bridge to spinal stimulation. [paper](https://www.nature.com/articles/s41586-023-06094-5)

### Speech & Language Decoding (语音与语言解码)

**Speech-to-text**

*2015–2020*
- 📄 **Brain-to-text: decoding spoken phrases from phone representations** (Herff / Schultz, 2015, Frontiers in Neuroscience) — origin of the "Brain-to-Text" paradigm. [paper](https://www.frontiersin.org/journals/neuroscience/articles/10.3389/fnins.2015.00217/full)
- 📄 **Real-time decoding of question-and-answer speech dialogue using human cortical activity** (Moses / Chang, 2019, Nature Communications) — interactive perceived-question + produced-answer decoding. [paper](https://www.nature.com/articles/s41467-019-10994-4)
- 📄 **Neural ensemble dynamics in dorsal motor cortex during speech in people with paralysis** (Stavisky et al., 2019, eLife) — dorsal M1 also encodes articulator movement. [paper](https://elifesciences.org/articles/46015)
- 📄 **Decoding spoken English from intracortical arrays in dorsal precentral gyrus** (Wilson / Stavisky, 2020, J. Neural Eng.) — phoneme decoding from a non-canonical speech site. [paper](https://pubmed.ncbi.nlm.nih.gov/33236720/)

*2022–2023*
- 📄 **Generalizable spelling using a speech neuroprosthesis** (Metzger / Chang, 2022, Nature Communications) — 1152-word silent spelling. [paper](https://pubmed.ncbi.nlm.nih.gov/36347863/)
- 📄 **A high-performance speech neuroprosthesis** (Willett / Henderson, 2023, Nature) — [paper](https://www.nature.com/articles/s41586-023-06377-x) · [💻 code](https://github.com/fwillett/speechBCI)
- 📄 **High-resolution neural recordings improve the accuracy of speech decoding** (Metzger / Chang, 2023, Nature Communications) — denser ECoG grids → better speech decoding. [paper](https://www.nature.com/articles/s41467-023-42555-1)

*2024–2025*
- 📄 **An accurate and rapidly calibrating speech neuroprosthesis** (Card / Stavisky, 2024, NEJM) — 99.6% on 50 words, 30-min calibration. [paper](https://www.nejm.org/doi/full/10.1056/NEJMoa2314132)
- 📄 **A bilingual speech neuroprosthesis via shared cortical articulatory representations** (Silva / Chang, 2024, Nature Biomedical Engineering) — [paper](https://pubmed.ncbi.nlm.nih.gov/38769157/)
- 📄 **Inner speech in motor cortex and implications for speech neuroprostheses** (Kunz / Willett / Henderson, 2025, Cell) — [paper](https://pubmed.ncbi.nlm.nih.gov/40816265/)
- 📄 **Brain-to-text with context-aware neural representations and LLMs** (2025, J. Neural Eng.) — Brain-to-Text '24 winning approach. [paper](https://iopscience.iop.org/article/10.1088/1741-2552/adfab1)
- 📄 **Transfer learning via distributed brain recordings enables reliable speech BCI** (2025, Nature Communications) — distributed recordings + LLMs + transfer learning. [paper](https://www.nature.com/articles/s41467-025-63825-0)

**Speech synthesis**

- 📄 **Reconstructing speech from human auditory cortex** (Pasley et al., 2012, PLoS Biology) — origin of neural speech reconstruction. [paper](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001251)
- 📄 **Speech synthesis from ECoG using densely connected 3D CNNs** (Angrick / Herff, 2019, J. Neural Eng.) — [paper](https://pubmed.ncbi.nlm.nih.gov/30831567/)
- 📄 **A neural speech decoding framework leveraging deep learning and speech synthesis** (Chen / Wang, NYU, 2024, Nature Machine Intelligence) — [paper](https://www.nature.com/articles/s42256-024-00824-8) · [💻 code](https://github.com/flinkerlab/neural_speech_decoding)
- 📄 **A streaming brain-to-voice neuroprosthesis to restore naturalistic communication** (Littlejohn / Cho / Anumanchipalli / Chang, 2025, Nature Neuroscience) — near-real-time streaming synthesis. [paper](https://pubmed.ncbi.nlm.nih.gov/40164740/)
- 📄 **An instantaneous voice-synthesis neuroprosthesis** (Wairagkar et al., 2025, Nature) — closed-loop instantaneous brain-to-voice with audio feedback (UC Davis/BrainGate). [paper](https://pubmed.ncbi.nlm.nih.gov/40506548/) · [💻 code](https://github.com/Neuroprosthetics-Lab/brain-to-voice-2025)

**Imagined / internal speech**

- 📄 **Representation of internal speech by single neurons in human supramarginal gyrus** (Wandelt / Andersen, 2024, Nature Human Behaviour) — [paper](https://www.nature.com/articles/s41562-024-01867-y) · [💻 code](https://zenodo.org/records/10697024)

**Tonal language (Mandarin)**

- 📄 **Decoding and synthesizing tonal language speech from brain activity** (2023, Science Advances) — [paper](https://www.science.org/doi/10.1126/sciadv.adh0478)
- 📄 **A brain-to-text framework for decoding natural tonal sentences** (2024, Cell Reports) — [paper](https://www.sciencedirect.com/science/article/pii/S2211124724012750)
- 📄 **Real-time decoding of full-spectrum spoken Mandarin syllables** (2025, Science Advances) — [paper](https://www.science.org/doi/10.1126/sciadv.adz9968)

### Visual Decoding & Prosthesis (视觉解码)

> Pure image-reconstruction-from-cortex with invasive recordings is still sparse; most work here is cortical-stimulation visual prosthesis (phosphene generation).

- 📄 **Shape perception via a high-channel-count neuroprosthesis in monkey visual cortex** (Chen / Roelfsema, 2020, Science) — 1024-channel V1/V4 phosphene patterns. [paper](https://www.science.org/doi/10.1126/science.abd7435)
- 📄 **Dynamic stimulation of visual cortex produces form vision in sighted and blind humans** (Beauchamp / Yoshor, 2020, Cell) — [paper](https://www.cell.com/cell/fulltext/S0092-8674(20)30496-7)
- 📄 **MEIcoder: decoding visual stimuli from neural activity** (2025, arXiv) — reconstruction from single-cell V1 activity. [paper](https://arxiv.org/html/2510.20762v1)

### Affective / Memory / Cognitive State (情绪/记忆/认知)

- 📄 **Mood variations decoded from multi-site intracranial human brain activity** (Sani / Shanechi, 2018, Nature Biotechnology) — [paper](https://www.nature.com/articles/nbt.4200)
- 📄 **Closed-loop enhancement and neural decoding of cognitive control in humans** (Widge et al., 2022, Nature Biomedical Engineering) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC9056584/)
- 📄 **Developing a hippocampal neural prosthetic to facilitate human memory encoding and recall** (Hampson / Song / Berger, 2018, J. Neural Eng.) — MIMO memory prosthesis. [paper](https://iopscience.iop.org/article/10.1088/1741-2552/aaaed7/meta)
- 📄 **Closed-loop modulation of remote hippocampal representations** (2024, Neuron) — [paper](https://www.cell.com/neuron/fulltext/S0896-6273(24)00923-1)

---

## 3. By Research Direction (研究方向)

### Decoding Algorithms & Methods (纯解码)

Classic + modern decoders mapping neural activity → behavior.

*Classic (2002–2017)*
- 📄 **Instant neural control of a movement signal** (Serruya / Hatsopoulos / Donoghue, 2002, Nature) — foundational closed-loop primate cursor control. [paper](https://www.nature.com/articles/416141a)
- 📄 **Learning to control a brain–machine interface for reaching and grasping by primates** (Carmena / Nicolelis, 2003, PLoS Biology) — [paper](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.0000042)
- 📄 **Bayesian population decoding of motor cortical activity using a Kalman filter** (Wu et al., 2006, Neural Computation) — KF as the workhorse BCI decoder. [paper](https://pubmed.ncbi.nlm.nih.gov/16354382/)
- 📄 **A recurrent neural network for closed-loop intracortical BMI decoders** (Sussillo et al., 2012, J. Neural Eng.) — earliest RNN (echo-state) closed-loop BMI decoder. [paper](https://pubmed.ncbi.nlm.nih.gov/22427488/)
- 📄 **A high-performing BMI driven by low-frequency LFPs alone and with spikes** (Stavisky et al., 2015, J. Neural Eng.) — LFP as a stable complementary control signal. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC4457459/)
- 📄 **Making brain–machine interfaces robust to future neural variability** (Sussillo et al., 2016, Nature Communications) — multiplicative RNN decoder robust to drift. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC5159828/)
- 📄 **Augmenting iBMI with neurally driven error detectors** (Even-Chen et al., 2017, J. Neural Eng.) — closed-loop neural error correction. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC5742283/)

*Deep-learning era (2020–2025)*
- 📄 **Machine learning for neural decoding** (Glaser / Kording, 2020, eNeuro) — tutorial + benchmark of modern ML decoders vs classical. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7470933/) · [💻 code](https://github.com/KordingLab/Neural_Decoding)
- 📄 **Representation learning for neural population activity (Neural Data Transformer, NDT)** (Ye / Pandarinath, 2021) — first Transformer for spiking activity. [paper](https://arxiv.org/abs/2108.01210) · [💻 code](https://github.com/snel-repo/neural-data-transformers)
- 📄 **STNDT: spatiotemporal Transformer for neural population activity** (Le & Shlizerman, 2022, NeurIPS) — [paper](https://arxiv.org/abs/2206.04727) · [💻 code](https://github.com/trungle93/STNDT)
- 📄 **seegnificant: neural decoding from sEEG accounting for electrode variability across subjects** (2024, NeurIPS) — cross-subject training over heterogeneous sEEG layouts. [paper](https://arxiv.org/html/2411.10458v1)
- 📄 *LFADS (Pandarinath 2018) — see [Latent Dynamics Models](#latent-dynamics-models-神经流形与动力学).*

### Neural Foundation Models (神经基础模型)

Large, pretrained, transferable models for neural data.

*2023*
- 📄 **A unified, scalable framework for neural population decoding (POYO)** (Azabou et al., 2023, NeurIPS) — spike tokenization + PerceiverIO. [paper](https://arxiv.org/abs/2310.16046) · [💻 code](https://github.com/neuro-galaxy/torch_brain)
- 📄 **Neural Data Transformer 2 (NDT2): multi-context pretraining** (Ye et al., 2023, NeurIPS) — [paper](https://openreview.net/pdf?id=CBBtMnlTGq) · [💻 code](https://github.com/joel99/context_general_bci)
- 📄 **BrainBERT: self-supervised representation learning for intracranial recordings** (Wang et al., 2023, ICLR) — [paper](https://arxiv.org/abs/2302.14367) · [💻 code](https://github.com/czlwang/BrainBERT)
- 📄 **Brant: foundation model for intracranial neural signal** (Zhang et al., 2023, NeurIPS) — [paper](https://openreview.net/forum?id=DDkl9vaJyE) · [💻 code](https://zju-brainnet.github.io/Brant.github.io/)

*2024*
- 📄 **Towards a "universal translator" for neural dynamics (IBL-MtM)** (Zhang, Wang et al., 2024, NeurIPS) — multi-task masking foundation model. [paper](https://arxiv.org/html/2407.14668v1) · [💻 code](https://ibl-mtm.github.io/)
- 📄 **Neuroformer: multimodal & multitask generative pretraining for brain data** (Antoniades et al., 2024, ICLR) — [paper](https://arxiv.org/abs/2311.00136) · [💻 code](https://github.com/a-antoniades/Neuroformer)
- 📄 **Brant-2: foundation model for brain signals** (ZJU-BrainNet, 2024) — extends Brant to multi-modal (sEEG + EEG) with broader cross-subject coverage. [paper](https://arxiv.org/html/2402.10251v3)

*2025*
- 📄 **POYO+: multi-session, multi-task decoding across cell-types & regions** (Azabou et al., 2025, ICLR) — [paper](https://openreview.net/forum?id=IuU0wcO0mo) · [💻 code](https://poyo-plus.github.io/)
- 📄 **Neural Data Transformer 3 (NDT3): a generalist intracortical motor decoder** (Ye et al., 2025, bioRxiv) — pretrained on ~2000 h. [paper](https://www.biorxiv.org/content/10.1101/2025.02.02.634313v1) · [💻 code](https://github.com/joel99/ndt3)
- 📄 **Population Transformer (PopT): population-level representations of neural activity** (Chau et al., 2025, ICLR) — [paper](https://arxiv.org/abs/2406.03044) · [💻 code](https://glchau.github.io/population-transformer/)
- 📄 **POSSM: generalizable, real-time neural decoding with hybrid state-space models** (Ryoo, Azabou et al., 2025) — [paper](https://arxiv.org/abs/2506.05320)
- 📄 **NEDS: neural encoding and decoding at scale** (Zhang et al. / IBL, 2025, ICML, Spotlight) — multimodal multi-task joint encoding+decoding pretrained across animals. [paper](https://arxiv.org/abs/2504.08201)
- 📄 **NeurIPT: foundation model for neural interfaces** (2025, NeurIPS) — general pretraining spanning clinical diagnosis to BCI decoding. [paper](https://papers.nips.cc/paper_files/paper/2025/file/dd9c5ce8803e1898d438e636fbae0236-Paper-Conference.pdf)
- 📄 **NuCLR: learning neuron identity from population context** (2025, NeurIPS) — self-supervised neuron-level representations from raw population activity. [paper](https://neurips.cc/virtual/2025/poster/115008)

### Latent Dynamics Models (神经流形与动力学)

*Foundations (2012–2018)*
- 📄 **Neural population dynamics during reaching** (Churchland / Cunningham / Shenoy, 2012, Nature) — dynamical-systems view of motor cortex that underpins modern decoders. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC3393826/)
- 📄 **LFADS: latent factor analysis via dynamical systems (original)** (Sussillo / Pandarinath, 2016) — [paper](https://arxiv.org/abs/1608.06315) · [💻 code](https://github.com/lfads/models)
- 📄 **Inferring single-trial neural population dynamics using sequential autoencoders (LFADS)** (Pandarinath et al., 2018, Nature Methods) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC6380887/) · [💻 code](https://github.com/lfads/models)

*2020–2022*
- 📄 **pi-VAE: identifiable & interpretable latent models of neural activity** (Zhou & Wei, 2020, NeurIPS) — [paper](https://arxiv.org/abs/2011.04798) · [💻 code](https://github.com/zhd96/pi-vae)
- 📄 **Recurrent switching dynamical systems for multiple populations (mp-rSLDS)** (Glaser / Linderman, 2020, NeurIPS) — joint switching dynamics across interacting populations. [paper](https://proceedings.neurips.cc/paper/2020/hash/aa1f5f73327ba40d47ebce155e785aaf-Abstract.html)
- 📄 **A general recurrent state-space framework for decision-making neural dynamics** (Zoltowski / Pillow / Linderman, 2020, ICML) — recurrent SSM subsuming drift-diffusion models. [paper](https://proceedings.mlr.press/v119/zoltowski20a.html)
- 📄 **Inferring latent dynamics via Poisson Latent Neural ODEs (PLNDE)** (Kim / Pillow / Brody, 2021, ICML) — nonlinear latent dynamics of spike trains via neural ODEs. [paper](https://proceedings.mlr.press/v139/kim21h/kim21h.pdf)
- 📄 **AutoLFADS: large-scale auto-tuned single-trial dynamics estimation** (Keshtkaran / Sedler / Pandarinath, 2022, Nature Methods) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC9825111/) · [💻 code](https://snel.ai/resources/lfads/)

*2023–2025*
- 📄 **iLDS: infinite recurrent switching linear dynamical systems** (Lee et al., 2023, ICLR) — [paper](https://openreview.net/forum?id=YIls9HEa52)
- 📄 **gpSLDS: Gaussian-process switching linear dynamical systems** (Hu et al., 2024, NeurIPS) — [paper](https://arxiv.org/html/2408.03330v3)
- 📄 **irSLDS: parsing neural dynamics with infinite recurrent switching LDS** (Geadah / IBL / Pillow, 2024, ICLR) — auto-discovers number of dynamical regimes. [paper](https://iclr.cc/virtual/2024/poster/18427)
- 📄 **cc-GPFA: conditionally-conjugate GPFA for spike-count data** (Nadew / Quinn, 2024, ICML) — Pólya-Gamma augmented GPFA with closed-form inference. [paper](https://icml.cc/virtual/2024/poster/32621)
- 📄 **FINDR: flow-field inference from neural data using deep recurrent networks** (Kim et al., 2025, ICML) — unsupervised nonlinear stochastic flow fields. [paper](https://icml.cc/virtual/2025/poster/44862)
- 📄 **iSSM: identifying neural dynamics using interventional state-space models** (Macke lab, 2025, ICML) — leverages perturbations to recover causal dynamics. [paper](https://icml.cc/virtual/2025/poster/44119)

### Long-Term Stability & Recalibration (长期稳定性)

Keeping a decoder working over months/years despite neural drift and electrode degradation. **This is the deepest section of the list** — organized into the manifold-stability foundations, manifold-alignment stabilizers, domain-adaptation / adversarial alignment, clinical self-calibration, and the instability-measurement / benchmark works that ground them.

**Neural-manifold foundations of stability**
- 📄 **Neural manifolds for the control of movement** (Gallego / Perich / Solla / Miller, 2017, Neuron) — defines "neural modes" / the manifold framework; conceptual basis for treating the manifold as the stable substrate. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC6122849/)
- 📄 **Cortical population activity within a preserved neural manifold underlies multiple motor behaviors** (Gallego / Perich / Miller, 2018, Nature Communications) — one preserved manifold supports many behaviors. [paper](https://www.nature.com/articles/s41467-018-06560-z)
- 📄 **A neural population mechanism for rapid learning** (Perich / Gallego / Miller, 2018, Neuron) — new output without changing within-manifold structure → manifold as stable scaffold. [paper](https://www.sciencedirect.com/science/article/pii/S0896627318308328)
- 📄 **Learning by neural reassociation** (Golub / Yu / Chase / Batista, 2018, Nature Neuroscience) — short-term BCI learning recombines fixed activity patterns. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC5876156/)
- 📄 **Long-term stability of cortical population dynamics underlying consistent behavior** (Gallego / Perich / Miller, 2020, Nature Neuroscience) — **cornerstone**: latent dynamics stay stable across years, enabling manifold-based decoders that survive while unit-based decoders fail. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC7007364/)
- 📄 **Preserved neural dynamics across animals performing similar behaviour** (Safaie / Gallego / Miller, 2023, Nature) — CCA-aligned latent dynamics transfer across individuals. [paper](https://www.nature.com/articles/s41586-023-06714-0) · [💻 code](https://github.com/BeNeuroLab/2022-preserved-dynamics)
- 📄 **Aligning latent representations of neural activity** (Gallego group, 2022, Nature Reviews Neuroscience) — review: low-dim latent alignment as the principled way to compare neural activity across time/neurons/individuals. [paper](https://pubmed.ncbi.nlm.nih.gov/36443379/)

**Manifold-alignment stabilizers & recalibration**
- 📄 **Stabilization of a BCI via alignment of low-dimensional neural spaces** (Degenhart / Bishop / Yu, 2020, Nature Biomedical Engineering) — unsupervised manifold-alignment stabilizer. [paper](https://users.ece.cmu.edu/~byronyu/papers/DegenhartBishopNatBME2020.pdf) · [💻 code](https://github.com/alandegenhart/stabilizedbci)
- 📄 **Stabilizing BCIs through alignment of latent dynamics (NoMAD)** (Karpowicz / Pandarinath, 2025, Nature Communications) — LFADS + unsupervised distribution alignment. [paper](https://www.nature.com/articles/s41467-025-59652-y) · [💻 code](https://github.com/snel-repo/nomad)
- 📄 **Plug-and-play stability for intracortical BCIs** (2024, IEEE) — [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC11086983/)
- 📄 **Plug-and-play stability: a one-year demonstration of seamless brain-to-text** (Fan et al., 2023, NeurIPS) — unsupervised self-recalibration, 93.84% over a year. [paper](https://proceedings.neurips.cc/paper_files/paper/2023/hash/83a14a36de4502bac5b580db36e81858-Abstract-Conference.html) · [📊 data](https://datadryad.org/dataset/doi:10.5061/dryad.hqbzkh1p6)
- 📄 **Long-term unsupervised recalibration of cursor-based intracortical BCIs (HMM)** (Wilson et al. / Stanford, 2025, Nature Biomedical Engineering) — HMM infers intended targets to retrain without calibration blocks. [paper](https://www.nature.com/articles/s41551-025-01536-z)
- 📄 **Closed-loop decoder adaptation shapes neural plasticity for skillful neuroprosthetic control** (Orsborn / Carmena, 2014, Neuron) — classic CLDA co-adaptation paradigm. [paper](https://pubmed.ncbi.nlm.nih.gov/24945777/)

**Domain adaptation & adversarial alignment**
- 📄 **Adversarial domain adaptation for stable brain-machine interfaces (ADAN)** (Farshchian / Gallego / Bengio / Miller, 2019, ICLR) — seminal adversarial latent-distribution alignment for BMI stability. [paper](https://arxiv.org/abs/1810.00045) · [💻 code](https://github.com/farshchian/ADAN)
- 📄 **Using adversarial networks to extend BCI decoding accuracy over time (Cycle-GAN aligner)** (Ma et al. / Miller Lab, 2023, eLife) — cycle-consistent full-dimensional alignment across days; outperforms ADAN. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC10446822/) · [💻 code](https://github.com/limblab/adversarial_BCI)
- 📄 **Robust alignment of cross-session recordings by behaviour via unsupervised domain adaptation** (Jude / Hennig, 2022, ICML) — seqVAE + UDA for stable cross-session latents. [paper](https://proceedings.mlr.press/v162/jude22a/jude22a.pdf)
- 📄 **ERDiff: latent dynamics alignment with diffusion models** (Wang et al. / Georgia Tech, 2023, NeurIPS) — source-free distribution alignment using a diffusion prior. [paper](https://arxiv.org/abs/2306.06138) · [💻 code](https://papers.neurips.cc/paper_files/paper/2023/file/7abbcb05a5d55157ede410bb718e32d7-Paper-Conference.pdf)
- 📄 **A cryptography-based approach for movement decoding** (Dyer et al., 2017, Nature Biomedical Engineering) — label-free cross-time/subject alignment, early recalibration paradigm. [paper](https://pubmed.ncbi.nlm.nih.gov/31015712/)
- 📄 **SeSA: speed-enhanced subdomain adaptation for long-term stable neural decoding** (Wang / Wang et al. / ZJU, 2024) — subdomain-alignment regression for long-term stability. [paper](https://arxiv.org/html/2407.17758v1)
- 📄 **Partial domain adaptation for stable neural decoding in intracortical BCIs** (Wang / Qi et al. / ZJU, 2025) — partial DA for stable cross-day representations. [paper](https://pubmed.ncbi.nlm.nih.gov/40522806/)
- 📄 **T-TIME: test-time information-maximization ensemble for plug-and-play BCIs** (2024) — fully-online label-free test-time adaptation. [paper](https://arxiv.org/html/2412.07228v1)

**Clinical self-calibration (intent-inference)**
- 📄 **Virtual typing by people with tetraplegia using a self-calibrating intracortical BCI** (Jarosiewicz / BrainGate, 2015, Science Translational Medicine) — retrospective target inference (RTI) auto-compensates nonstationarity. [paper](https://pubmed.ncbi.nlm.nih.gov/26560357/)
- 📄 **Retrospectively supervised click-decoder calibration for self-calibrating point-and-click BCIs** (BrainGate, 2017) — recalibrate clicks from real usage data. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC5591042/)

**Measuring instability, longevity & benchmarks**
- 📄 **Intra-day signal instabilities affect decoding performance in an intracortical neural interface** (Perge / BrainGate, 2013, J. Neural Eng.) — foundational characterization of why recalibration is needed. [paper](https://pubmed.ncbi.nlm.nih.gov/23574741/)
- 📄 **MINDFUL: measuring instability in chronic human intracortical recordings** (2024, Communications Biology) — label-free instability metric to decide when to recalibrate. [paper](https://www.nature.com/articles/s42003-024-06784-4)
- 📄 **FALCON: few-shot algorithms for consistent neural decoding** (SNEL / Pandarinath, 2024, NeurIPS D&B) — first unified benchmark for stable long-term decoding. [paper](https://proceedings.neurips.cc/paper_files/paper/2024/file/8c2e6bb15be1894b8fb4e0f9bcad1739-Paper-Datasets_and_Benchmarks_Track.pdf)
- 📄 **LINK: long-term intracortical neural activity & kinematics** (Temmar / Willsey, 2025, NeurIPS D&B) — 303 sessions / 117k trials of chronic finger movement for drift & stability research. [paper](https://neurips.cc/virtual/2025/poster/121631)
- 📄 **Longevity and reliability of chronic unit recordings using Utah arrays** (2021, J. Neural Eng.) — [paper](https://iopscience.iop.org/article/10.1088/1741-2552/ac3eaf)

### Cross-Subject / Cross-Session Transfer (跨被试/跨会话迁移)

- 📄 **MYOW: mine your own view — self-supervised representation learning** (Azabou / Dyer, 2021) — generalizes across V1/CA1/motor cortex. [paper](https://arxiv.org/abs/2102.10106) · [💻 code](https://nerdslab.github.io/myow/)
- 📄 **Robust alignment of cross-session recordings via behaviour (UDA + seqVAE)** (2022) — unsupervised domain adaptation for stable cross-session decoding. [paper](https://arxiv.org/abs/2202.06159)
- 📄 **Neural Latent Aligner (NLA): cross-trial alignment of neural representations** (Cho et al., 2023, ICML) — unsupervised cross-trial latent alignment for speech/neural data. [paper](https://proceedings.mlr.press/v202/cho23a/cho23a.pdf)
- 📄 **Leveraging generative models for unsupervised alignment of neural time series** (2024, ICLR) — source-free seqVAE reuse to stabilize decoders across sessions. [paper](https://openreview.net/forum?id=9zhHVyLY4K)
- 📄 **FDA: flow matching for few-trial neural adaptation with stable latent dynamics** (Wang et al., 2025, ICML) — flow-matching distribution alignment for fast decoder adaptation. [paper](https://icml.cc/virtual/2025/poster/44109) · [💻 code](https://github.com/wangpuli/FDA)
- 📄 **Neural Embeddings Rank (NER): aligning 3D latent dynamics with movements** (2024, NeurIPS) — rank-preserving embedding for stable long-term M1/PMd decoding. [paper](https://neurips.cc/virtual/2024/poster/95804)
- 📄 **MINT: simple decoding of behavior from a complicated neural manifold** (Perkins / Cunningham / Churchland, 2024, eLife) — interpretable manifold-based decoder, robust in stereotyped BCI settings. [paper](https://elifesciences.org/reviewed-preprints/89421v1)
- 📄 **Transfer learning in BCIs with adversarial variational autoencoders** (Özdenizci et al. / MERL, 2018) — adversarial VAE for invariant cross-subject/session features. [paper](https://www.merl.com/publications/docs/TR2018-184.pdf)
- 📄 *(see also POYO, NDT2, PopT under [Foundation Models](#neural-foundation-models-神经基础模型); and the [Long-Term Stability](#long-term-stability--recalibration-长期稳定性) section, whose manifold-alignment / domain-adaptation methods directly target cross-session transfer)*

### Self-Supervised & Representation Learning (自监督表征学习)

- 📄 **CEBRA: learnable latent embeddings for joint behavioural & neural analysis** (Schneider / Lee / Mathis, 2023, Nature) — [paper](https://www.nature.com/articles/s41586-023-06031-6) · [💻 code](https://github.com/AdaptiveMotorControlLab/CEBRA)
- 📄 **Swap-VAE: drop, swap, and generate — disentangling neural activity** (Liu / Azabou / Dyer, 2021, NeurIPS) — [paper](https://arxiv.org/abs/2111.02338)

### Neural Data Generation & Synthesis (数据生成)

- 📄 **LDNS: latent diffusion for neural spiking data** (Kapoor / Macke, 2024, NeurIPS) — [paper](https://arxiv.org/html/2407.08751v1) · [💻 code](https://github.com/mackelab/LDNS)
- 📄 **Spike-GAN: synthesizing realistic neural population activity with GANs** (Molano-Mazón / Panzeri, 2018, ICLR) — [paper](https://openreview.net/forum?id=r1VVsebAZ)
- 📄 **Spiking GANs with a neural network discriminator** (Rosenfeld / Simeone, 2022, IEEE TC) — [paper](https://arxiv.org/abs/2111.01750)
- 📄 **Diffusion-based generation of neural activity from disentangled latent codes** (McCart / Sedler / Pandarinath, 2024) — conditional diffusion for unsupervised disentangled spiking codes. [paper](https://arxiv.org/abs/2407.21195)
- 📄 **BeNeDiff: behavior-relevant & disentangled neural dynamics via diffusion** (Wu et al., 2024, NeurIPS) — isolates and generates behavior-relevant neural dynamics. [paper](https://openreview.net/forum?id=jL0EsbfbAV)
- 📄 **Generative modeling of neural dynamics via latent stochastic differential equations** (2024) — latent SDE with state/input-dependent drift & diffusion. [paper](https://arxiv.org/html/2412.12112v1)
- 📄 **LangevinFlow: Langevin flows for modeling neural latent dynamics** (Song et al., 2025) — physics-inspired seqVAE with underdamped Langevin latents. [paper](https://arxiv.org/abs/2507.11531)

### Closed-Loop & Co-Adaptation (闭环与协同自适应)

- 📄 **Pain control by co-adaptive learning in a brain–machine interface** (Zhang / Hu, 2020, Current Biology) — [paper](https://www.sciencedirect.com/science/article/pii/S0960982220310915)
- 📄 **BRAND: backend for realtime asynchronous neural decoding** (Ali et al. / SNEL, 2024) — real-time closed-loop platform; see [Tools](#tools--libraries-工具与库). [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC11021878/)
- 📄 **Closed-loop control of theta oscillations enhances human episodic memory** (2025, Nature Communications) — [paper](https://www.nature.com/articles/s41467-025-59417-7)
- 📄 **Machine-learning-based brain-signal decoding for adaptive DBS** (2022, Experimental Neurology) — ML decoding of neural biomarkers driving adaptive DBS (PD/ET/dystonia). [paper](https://www.sciencedirect.com/science/article/pii/S0014488622000188)
- 📄 **Closed-loop deep brain stimulation with reinforcement learning and neural simulation** (2024, IEEE TNSRE) — RL-optimized stimulation parameters for Parkinson's aDBS. [paper](https://www.embs.org/tnsre/articles/closed-loop-deep-brain-stimulation-with-reinforcement-learning-and-neural-simulation-2/)

### LLM / Multimodal / Diffusion Decoding (大模型与多模态)

Emerging direction coupling neural decoders with large language models, multimodal fusion, and diffusion generative models.

- 📄 **Towards an end-to-end framework for invasive brain signal decoding with LLMs** (2024, Interspeech) — couples LLMs with end-to-end speech neuroprosthesis decoding. [paper](https://arxiv.org/html/2406.11568v1)
- 📄 **LLMs help alleviate cross-subject variability in brain signal decoding** (2025) — LLM embeddings to align neural signals with language representations across subjects. [paper](https://arxiv.org/html/2501.02621v1)
- 📄 **Progress, challenges and future of linguistic neural decoding with LLMs** (2025, Communications Biology) — survey of LLM-driven brain-to-text decoding. [paper](https://www.nature.com/articles/s42003-025-08511-z)
- 📄 **Transformer-based neural speech decoding from surface and depth electrodes** (2025, J. Neural Eng.) — Transformer over non-grid surface + depth intracranial electrodes. [paper](https://iopscience.iop.org/article/10.1088/1741-2552/adab21)
- 📄 *(see also BrainBERT, Brant, Neuroformer, NEDS under [Foundation Models](#neural-foundation-models-神经基础模型))*

### Real-Time / Adaptive Systems (实时与自适应)

- 📄 **Tailoring deep learning for real-time BCIs (RAP)** (2025) — real-time adaptive pooling retrofits offline deep models for online decoding. [paper](https://arxiv.org/abs/2507.06779)
- 📄 **EDAPT: towards calibration-free BCIs with continual online adaptation** (2025, J. Neural Eng.) — task/model-agnostic continual online learning. [paper](https://arxiv.org/html/2508.10474v1)
- 📄 **Low-latency neural inference on an edge device for real-time imagined handwriting** (2025, Scientific Reports) — edge-device low-latency imagined-handwriting recognition. [paper](https://arxiv.org/abs/2510.19832)
- 📄 *(see also [BRAND](#tools--libraries-工具与库) real-time platform under Tools)*

### China Teams (国内团队)

Selected invasive-BCI decoding work from Chinese groups (Tsinghua, NeuCyber/SIMIT, Fudan, etc.). Entries without a peer-reviewed paper are marked as preprint/report.

- 📄 **Fine-grained 2D cursor control with an epidural minimally invasive BCI (NEO)** (Tsinghua / Hong Bo, 2025, medRxiv preprint) — 8-contact epidural ECoG (NEO) for fine 2D cursor control in tetraplegia. [paper](https://www.medrxiv.org/content/10.1101/2025.10.06.25337264v1)
- 📄 **Real-time decoding of full-spectrum spoken Mandarin** (NeuCyber / SIMIT, 2025, Science Advances) — see [Speech → Mandarin](#speech--language-decoding-语音与语言解码). [paper](https://www.science.org/doi/10.1126/sciadv.adz9968)
- 📄 **SEEG-audio contrastive matching for Chinese speech decoding** (2025) — Mandarin sEEG speech-decoding paradigm with contrastive audio alignment. [paper](https://arxiv.org/html/2505.19652v1)
- 📄 **Decoding handwriting trajectories from intracortical brain signals** (2025, Advanced Science) — continuous handwriting-trajectory decoding from cortex. [paper](https://advanced.onlinelibrary.wiley.com/doi/10.1002/advs.202505492)
- 📄 **Brant: foundation model for intracranial neural signal** (Zhejiang Univ. / ZJU-BrainNet, 2023, NeurIPS) — see [Foundation Models](#neural-foundation-models-神经基础模型). [paper](https://openreview.net/forum?id=DDkl9vaJyE)

---

## Datasets (数据集)

- 📊 **Neural Latents Benchmark '21 — MC_Maze / MC_RTT / Area2_Bump / DMFC_RSG** (Pei et al., 2021) — curated intracortical spiking datasets. [data](https://neurallatents.github.io/datasets.html) · [💻 tools](https://github.com/neurallatents/nlb_tools)
- 📊 **Sabes Lab — NHP reaching with sensorimotor arrays** (O'Doherty / Sabes, 2017) — ~20k macaque reaches with M1/S1 spikes + LFP. [data](https://zenodo.org/records/583331)
- 📊 **AJILE12 — long-term naturalistic human ECoG** (Peterson et al., 2022) — 55 days of ECoG + pose across 12 subjects. [paper](https://www.nature.com/articles/s41597-022-01280-y) · [data](https://neural.cs.washington.edu/research/data)
- 📊 **Willett et al. speech neuroprosthesis data** (Stanford / BrainGate, 2023) — intracortical spiking during attempted speech (~12k sentences). [data](https://datadryad.org/dataset/doi:10.5061/dryad.x69p8czpq)
- 📊 **Allen Brain Observatory — Visual Coding Neuropixels** (Allen Institute, 2019) — [data](https://knowledge.brain-map.org/data/4YYLRZZGK82FQ85NIH8) · [💻 SDK](https://allensdk.readthedocs.io/en/latest/visual_coding_neuropixels.html)
- 📊 **International Brain Laboratory (IBL) brain-wide map** (IBL, 2021) — standardized Neuropixels across many labs. [paper](https://elifesciences.org/articles/63711) · [data](https://viz.internationalbrainlab.org/)
- 📊 **DANDI Archive** (BRAIN Initiative) — NWB-formatted neurophysiology archive incl. human single-unit & Neuropixels. [data](https://about.dandiarchive.org/)
- 📊 **Willett handwriting BCI dataset** (Stanford / Dryad, 2021) — intracortical spiking during attempted handwriting. [data](https://datadryad.org/dataset/doi:10.5061/dryad.wh70rxwmv)
- 📊 **Flint center-out reaching (CRCNS pmd-1)** (Flint / Slutzky, Northwestern) — macaque M1/PMd spikes + LFP; common kinematic-decoding benchmark. [data](https://crcns.org/data-sets/motor-cortex/pmd-1/about-pmd-1)
- 📊 **O'Doherty/Makin/Sabes NHP reaching (Indy/Loco)** (2020) — multichannel M1/S1 self-paced grid reaching; used in decoder-stability studies. [data](https://zenodo.org/records/3854034)
- 📊 **Kai Miller human ECoG library** (Miller, Stanford, 2016/2019) — curated human ECoG across 16 behavioral experiments. [data](https://purl.stanford.edu/zk881ps0522)
- 📊 **Neurotycho macaque ECoG** (Fujii / Nagasaka, RIKEN) — long-duration multichannel macaque ECoG with synchronized behavior. [data](https://neurotycho.org/download)
- 📊 **IEEG.org — International Epilepsy Electrophysiology Portal** (Litt Lab, UPenn) — large-scale human intracranial EEG/ECoG with tools + API. [portal](https://www.ieeg.org/)
- 📊 **Epilepsy-iEEG multicenter dataset (OpenNeuro ds003029)** — standardized BIDS-iEEG human intracranial recordings. [data](https://openneuro.org/datasets/ds003029/versions/1.0.7)
- 📊 **Human single-neuron Sternberg working-memory dataset** (Rutishauser group, 2024, Scientific Data) — rare human single-unit recordings with behavior. [data](https://www.nature.com/articles/s41597-024-02943-8)

---

## Benchmarks & Competitions (基准与竞赛)

- 🏆 **Neural Latents Benchmark '21** (Pei et al., 2021, NeurIPS D&B) — latent-variable models of spiking activity. [paper](https://arxiv.org/abs/2109.04463) · [💻 code](https://github.com/neurallatents/nlb_tools)
- 🏆 **FALCON — few-shot algorithms for consistent neural decoding** (Karpowicz et al. / SNEL, 2024, NeurIPS D&B) — decoder stability across sessions. [paper](https://proceedings.neurips.cc/paper_files/paper/2024/file/8c2e6bb15be1894b8fb4e0f9bcad1739-Paper-Datasets_and_Benchmarks_Track.pdf) · [site](https://snel-repo.github.io/falcon/)
- 🏆 **Brain-to-Text Benchmark '24** (Willett et al. / BrainGate, 2024) — attempted-speech → text. [paper](https://arxiv.org/html/2412.17227v1) · [site](https://eval.ai/web/challenges/challenge-page/2099/overview)
- 🏆 **Brain-to-Text '25 (Kaggle)** (Willett et al. / BrainGate, 2025) — [site](https://www.kaggle.com/competitions/brain-to-text-25/overview)

---

## Tools & Libraries (工具与库)

- 💻 **CEBRA** — consistent latent embeddings from neural + behavioral data. [code](https://github.com/AdaptiveMotorControlLab/CEBRA)
- 💻 **POYO / torch_brain** — unified transformer framework for population decoding. [code](https://github.com/neuro-galaxy/torch_brain)
- 💻 **SpikeInterface** — unified Python framework wrapping many spike sorters. [code](https://github.com/SpikeInterface/spikeinterface)
- 💻 **Kilosort** — GPU template-matching spike sorter with drift correction. [code](https://github.com/MouseLand/Kilosort)
- 💻 **Neo** — common object model + readers/writers for electrophysiology formats. [code](https://github.com/NeuralEnsemble/python-neo)
- 💻 **Neurodata Without Borders (NWB)** — standardized neurophysiology data format & ecosystem. [paper](https://www.sciencedirect.com/science/article/pii/S0896627315009198)
- 💻 **BRAND** — graph-of-nodes platform for low-latency real-time closed-loop BCI. [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC11021878/)
- 💻 **nlb_tools** — loading & evaluation for the Neural Latents Benchmark. [code](https://github.com/neurallatents/nlb_tools)
- 💻 **falcon-challenge** — submit/evaluate decoders on the FALCON few-shot benchmark. [code](https://github.com/snel-repo/falcon-challenge)
- 💻 **KordingLab Neural_Decoding** — classic + ML/deep decoders (Wiener, Kalman, LSTM, XGBoost). [code](https://github.com/KordingLab/Neural_Decoding)
- 💻 **lfads-torch** — PyTorch reimplementation of LFADS. [code](https://github.com/arsedler9/lfads-torch)
- 💻 **autolfads-tf2** — TF2 AutoLFADS with population-based hyperparameter tuning. [code](https://github.com/snel-repo/autolfads-tf2)
- 💻 **MountainSort5** — density-based spike sorter (Flatiron Institute). [code](https://github.com/flatironinstitute/mountainsort5)
- 💻 **Tridesclous** — offline + real-time spike sorter. [code](https://github.com/tridesclous/tridesclous)
- 💻 **Elephant** — electrophysiology analysis toolkit (spikes, LFP) on Neo. [code](https://github.com/neuralensemble/elephant)
- 💻 **Pynapple** — lightweight time-series analysis for systems neuroscience. [code](https://github.com/pynapple-org/pynapple)
- 💻 **MNE-Python** — human neurophysiology toolkit incl. iEEG/ECoG analysis. [code](https://github.com/mne-tools)

---

## Recommended Venues (推荐会议与期刊)

A submission / tracking guide for this cross-disciplinary field — top **conferences** and **journals** across AI/ML, neuroscience, biomedical & neural engineering, clinical medicine, and the Nature/Science sub-journal family, annotated with **CCF** and **Tsinghua (THU)** ranks where they apply.

➡️ **See the full list in [VENUES.md](VENUES.md).**

Quick orientation:
- **Method / algorithm work** → NeurIPS · ICML · ICLR · AAAI (CCF-A); speech → ACL · ICASSP · Interspeech.
- **Decoding systems / devices / clinical** → *J. Neural Eng.* · *IEEE TNSRE* · *IEEE TBME*; conferences IEEE EMBC · NER · BCI Meeting.
- **Landmark demonstrations** → *Nature* · *Science* · *NEJM* · *Nat. Biomed. Eng.* · *Nat. Neurosci.* · *Science Robotics*.

---

## Non-Invasive BCI (coming soon)

🚧 **Coming soon.** Non-invasive modalities (EEG, MEG, fNIRS, fMRI) are out of scope for this list today. A companion section / sibling list is planned. Contributions welcome — see [Contributing](#contributing).

---

## Contributing

Contributions are very welcome! Please:

1. Keep the focus **invasive** (intracortical / ECoG / sEEG / depth / HD probes). Non-invasive work belongs in the future companion list.
2. Use the entry format: `<emoji> **Title** (First-author / Lab, Year, Venue) — one-line contribution. [paper](url) · [💻 code](url) · [📊 data](url)`
3. Place the paper under the axis that best fits; cross-list a landmark paper only when it genuinely helps discovery.
4. Verify every link resolves before submitting.
5. Prefer official DOIs / publisher pages / lab pages over aggregators when available.

Open an [issue](../../issues) for discussion or a [pull request](../../pulls) to add entries.

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the maintainers have waived all copyright and related rights to this work (CC0 1.0). The linked papers and resources remain under their respective licenses.
