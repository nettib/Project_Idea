# Waste Sorting App — Team Brief (Single-Photo Classification)

## 1. What We Build
A Flutter mobile app. User takes a photo of one piece of waste. 
App runs an image classification model on-device and shows one label — 
the correct bin category. Works offline, no backend.

## 2. Four Categories (Ethiopia-Adapted)
| Category     | Examples                                      |
|--------------|-----------------------------------------------|
| Organic      | Food scraps, peels, garden waste              |
| Recyclable   | Clean plastic, paper, metal, glass            |
| Hazardous    | Batteries, e-waste, expired medicine          |
| Residual     | Dirty bags, composite packaging               |

**Value:** User knows it's a bottle. They don't know which bin. We answer that.

## 3. Model: Image Classification (Not Object Detection)
- Input: one photo → output: one label (dominant item).
- Limitation: fails on mixed waste in one photo.
- Lightweight model (MobileNet-based) → export to .tflite.

## 4. Free Stack (No Credit Card)
| Step           | Tool                                              | Cost |
|----------------|---------------------------------------------------|------|
| Dataset        | RealWaste or Kaggle Garbage Classification        | Free |
| Label remapping| Organize images into 4 folders                    | Free |
| Training       | TensorFlow Lite Model Maker (laptop, no GPU)      | Free |
| Model export   | Model Maker → .tflite + labels.txt                | Free |
| App            | Flutter + camera + tflite_flutter                 | Free |
| Distribution   | APK on phone / emulator. No app store.            | Free |

## 5. Pipeline
1. Download public dataset → remap material labels into 4 categories by folder.
2. Train with Model Maker (few lines of Python, few hours on laptop).
3. Export .tflite + labels.txt → drop into Flutter project.
4. User taps shutter → frame sent to model → label returned → show result.

## 6. Work Split
- A: Dataset download + folder remapping
- B: Model Maker training + export + accuracy check
- C: Flutter app (camera screen + result screen + TFLite load)
- All: Collect 20–30 local Ethiopian waste photos for test set

## 7. Defense Story
"We built a disposal decision service, not a material classifier. 
User photographs waste; app tells them the correct bin — Organic, 
Recyclable, Hazardous, or Residual — using an on-device AI model 
trained on public data remapped to Ethiopia's waste reality. 
Works offline, zero cost."

## 8. Risks
- Foreign dataset mismatch → test on local photos, mention fine-tuning.
- Mixed waste in one photo → acknowledge limitation; YOLO as future upgrade.
- Model accuracy → report confusion matrix honestly; don't overpromise 99%.





# Waste Sorting App — Team Brief (Real-Time Object Detection)

## 1. What We Build
A Flutter mobile app. User points camera at mixed waste. App draws 
bounding boxes around each item and labels it with the correct bin 
category in real time. Runs on-device, works offline.

## 2. Four Categories (Ethiopia-Adapted)
| Category     | Examples                                      |
|--------------|-----------------------------------------------|
| Organic      | Food scraps, peels, garden waste              |
| Recyclable   | Clean plastic, paper, metal, glass            |
| Hazardous    | Batteries, e-waste, expired medicine          |
| Residual     | Dirty bags, composite packaging               |

**Value:** User knows it's a bottle. They don't know which bin. We answer that.

## 3. Model: YOLO Object Detection (Not Classification)
- Classification = one label per photo. Fails on mixed waste.
- YOLO = multiple boxes + labels per frame. Correct for our use case.
- Lightweight variant (YOLO nano) → export to .tflite.

## 4. Free Stack (No Credit Card)
| Step           | Tool                                              | Cost |
|----------------|---------------------------------------------------|------|
| Annotation     | Lannotex or AlchemyAnnotate (offline, open-source)| Free |
| Training       | Kaggle GPU (30 hrs/week, phone verification only) | Free |
| Model export   | Ultralytics → TFLite                              | Free |
| App            | Flutter + camera + tflite_flutter                 | Free |
| Distribution   | APK on phone / emulator. No app store.            | Free |

## 5. Pipeline
1. Collect/remap waste images → annotate boxes → YOLO format.
2. Train YOLO nano on Kaggle GPU.
3. Export .tflite → drop into Flutter project.
4. Camera stream → model inference → draw boxes + labels on screen.

## 6. Work Split
- A: Dataset + annotation (Lannotex)
- B: YOLO training on Kaggle + export
- C: Flutter app (camera + TFLite + UI)
- All: Collect 20–30 local Ethiopian waste photos for test set

## 7. Defense Story
"We built a disposal decision service, not a material classifier. 
Real-time YOLO detection on-device, four Ethiopia-relevant categories, 
zero cost, works offline."

## 8. Risks
- Annotation is tedious → split across team, few hundred images enough.
- Foreign dataset mismatch → test on local photos, mention fine-tuning.
- Real-time battery drain → demo short sessions, mention optimization.





# Comparison: Two Implementation Paths

| Feature              | Single-Photo Classification | Real-Time Object Detection |
|----------------------|-----------------------------|----------------------------|
| Input                | One photo, one item         | Live camera, multiple items|
| Output               | One label                   | Multiple boxes + labels    |
| Training             | Model Maker, laptop, hours  | YOLO on Kaggle GPU         |
| Annotation           | None (folder structure)     | Bounding boxes (Lannotex)  |
| Difficulty           | Low                         | Medium                     |
| Demo Impact          | Good                        | Strong                     |
| Handles Mixed Waste  | No                          | Yes                        |
| Recommended          | Build first (safe deliverable)| Upgrade if time permits  |
