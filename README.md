# LipSync-AI-Model

Lip & Voice Sync Anomaly Detector
📌 Overview

The Lip & Voice Sync Anomaly Detector is a real-time computer vision and audio analysis system designed to detect lip–voice synchronization anomalies.
It identifies situations where voice activity does not match visible lip movement, detects voice inconsistencies, lip occlusion, and face absence, and logs all anomalies with timestamps.

This system is suitable for:

Online exam proctoring

Interview monitoring

Cheating detection

Identity & liveness verification

Media authenticity checks (deepfake prevention)

🚀 Key Features
👄 Lip Movement Detection

Uses MediaPipe FaceMesh

Calculates:

Mouth open ratio

Residual lip motion

Applies EMA smoothing + hysteresis for stability

Robust to small head movements

🎙️ Voice Activity Detection

Uses Silero VAD (PyTorch-based)

Adaptive RMS thresholding

Noise floor calibration

Differentiates between:

Primary voice

Different voice detected

Detects:

Sudden voice pattern changes

Unnaturally consistent audio (possible playback)

Voice spikes (audio injection)

🧠 Visual Speaking Detection

Determines if the user is visually speaking

Combines:

Mouth openness

Lip motion intensity

Classifies states:

Mouth closed

Slightly open

Speaking

🚩 Sync Anomaly Detection

Flags critical cases such as:

Voice detected but lips not moving

Different voice while lips are closed

Voice present but face not visible

Voice detected while lips are covered

Lip movement without voice

Severity levels:

✅ OK

⚠️ WARNING

🚩 FLAG

❗ ANOMALY

🔴 CRITICAL

👁️ Lips Visibility & Occlusion

Detects:

Lips visible

Lips out of frame

Lips covered (hand occlusion via MediaPipe Hands)

Closed lips are treated as visible, not covered

📊 HUD Overlay

Displays real-time information:

Lip movement status

Lips visibility

Mouth state

Voice status

Sync/anomaly message

FPS

Session anomaly counter

📝 Anomaly Logging

Logs all flagged events to CSV

Each entry includes:

Timestamp

Anomaly type

Description

Duration

Voice detected

Lips moving

Face detected

Lips visible

Mouth state

Voice status

New CSV created per session

🛠️ Tech Stack

Python 3.8+

OpenCV

MediaPipe (FaceMesh & Hands)

PyTorch

Silero VAD

NumPy

SoundDevice

Threading & Queue (real-time audio processing)
