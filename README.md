# Project Overview: Cross-modal Mapping Between Histopathology and MRI in Prostate Cancer

## 1. Background & Motivation
Magnetic Resonance Imaging (MRI) provides non-invasive, macroscopic information about the prostate, but lacks cellular-level specificity. Histopathology slides, on the other hand, reveal microscopic cancer morphology but are only available after surgery or biopsy. Bridging these two modalities could allow MRI to approximate histopathologic insights — enabling earlier, less invasive cancer assessment.

However, this task is challenging: histology and MRI differ in resolution, geometry, and scale. Our institution does not yet have a dedicated cancer pathology imaging center, so this research uses publicly available datasets (e.g., TCIA Prostate-Fused-MRI-Pathology and Prostate-MRI-US-Biopsy) to build a reproducible cross-modal framework.

## 2. Research Question
How can we spatially and semantically align histopathology slides with MRI volumes, under limited data availability, to enable MRI-based prediction of pathological structures and cancerous regions?

The long-term goal is to create a reproducible 3D cross-modal representation that captures structural and semantic correspondences between MRI and pathology.

## 3. Current Progress

### 3.1 Slide-level (2D Mapping)
- Extracted **coordinates and embeddings** for each pathology slide using Virchow/Vit-H14 models.  
- **Resized and aligned embedding maps** to match corresponding MRI slices based on histo-MRI correspondence CSV.  
- Verified 2D overlays — pathology embeddings and MRI slices are spatially consistent.  
- Generated initial 2D visualizations demonstrating structural correlation between modalities.

### 3.2 3D Pathology Volume Reconstruction
- Began stacking individual pathology slides (A–I) along the z-axis to create a continuous **3D pathology embedding volume**.  
- Implemented interpolation for missing layers and coordinate alignment based on histo-MRI mapping.  
- The resulting 3D pathology volume preserves semantic continuity across slices.

### 3.3 Cross-modal Registration
- Planned rigid + deformable registration between 3D pathology volume and MRI volume (T2 / DCE).  
- Target output: an **aligned histo-MRI 3D volume** enabling voxel-wise correspondence analysis.  
- This stage will complete the 3D spatial mapping pipeline.

## 4. Next Steps
1. Complete 3D registration and visualize aligned pathology–MRI volume pairs.  
2. Integrate **biopsy data** (core-level Gleason scores and coordinates) as reference anchors for biological validation.  
3. Evaluate the **correspondence between pathology and MRI embeddings** around biopsy sites.  
4. Develop a preliminary **cross-modal learning model**: predicting pathology embeddings directly from MRI.  

## 5. Challenges & Notes
- Large scale difference between WSI (microns) and MRI (millimeters).  
- Incomplete histo–MRI mapping: not all slides (e.g., A–I) have reliable MRI counterparts.  
- 3D reconstruction requires balancing semantic continuity with geometric accuracy.  
- Limited dataset availability → emphasize reproducibility and methodological generality.  

## 6. Milestones

| Phase | Task | Status / Target |
|-------|------|----------------|
| 1 | 2D slide–MRI overlay (embedding maps) | Completed |
| 2 | 3D pathology reconstruction | November 2025 |
| 3 | MRI–pathology 3D registration | December 2025 |
| 4 | Biopsy data integration and validation | January 2026 |
| 5 | Cross-modal prediction and model training | Spring 2026 |

