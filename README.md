# Quantum Circuit Anomaly Detection Against Adversarial Attacks

This Python code demonstrates a quantum anomaly detection approach using the Cirq and PennyLane libraries, designed to detect adversarial attacks on quantum circuits. The code simulates adversarial attacks by introducing noise in the form of random rotations on qubits, mimicking potential real-world attack scenarios. Additionally, it includes features for adjusting the anomaly detection threshold and exploring the impact of noise on quantum circuits.

## Quantum Circuit Design

The quantum circuit used for anomaly detection is built upon the following steps:

1. **Data Encoding**: The input data (e.g., MNIST handwritten digit images) is flattened and scaled to the range [0, π]. Each scaled value is encoded as a rotation around the Y-axis (`cirq.ry` or `qml.RY`) on a corresponding qubit.

2. **Superposition Creation**: A Hadamard gate (`cirq.H` or `qml.Hadamard`) is applied to each qubit, creating an equal superposition of all possible states.

3. **Adversarial Attack Simulation**: To simulate an adversarial attack, random rotations around the Y-axis (`cirq.ry` or `qml.RY`) are applied to a subset of qubits with a specified probability (`noise_probability`). These random rotations represent the injected noise or errors.

4. **Measurement**: In the Cirq implementation, all qubits are measured using the `cirq.measure` operation, and the measurement results are stored under the key 'result'. In the PennyLane implementation, the probabilities of measuring each computational basis state are obtained using `qml.probs`.

## Anomaly Detection Algorithm

The anomaly detection algorithm calculates an anomaly score based on the non-zero amplitudes (Cirq) or probabilities (PennyLane) of the final state vector or computational basis states after applying the quantum circuit. A higher anomaly score indicates a potential anomaly or adversarial attack.

**Cirq and Pennylane Example - Without Anomaly Detection:**

![Quantum Circuit Prediction Without Anomaly Detection](https://github.com/ericyoc/quantum-circuit-anomaly-detection/blob/main/without_det_qan_circ.jpg)


**Cirq and Pennylane Example - With Anomaly Detection:**

![Quantum Circuit Prediction With Anomaly Detection](https://github.com/ericyoc/quantum-circuit-anomaly-detection/blob/main/with_det_qant_cir.jpg)

The code includes a configurable threshold value (`threshold`) for classifying data points as anomalies or not. If the calculated anomaly score is greater than or equal to the threshold, the data point is classified as an "Anomaly". The threshold value can be adjusted to balance the trade-off between detecting anomalies and avoiding false positives.

**Cirq Detection Outcomes**

![Cirq - Quantum Circuit Anomaly Detection Outcomes](https://github.com/ericyoc/quantum-circuit-anomaly-detection/blob/main/quant_circ_anom_det_table.jpg) 


**Pennylane Detection Outcomes**

![Pennylane Quantum Circuit Anomaly Detection Outcomes](https://github.com/ericyoc/quantum-circuit-anomaly-detection/blob/main/pennylane_table.jpg) 



## Simulating Adversarial Attacks

Adversarial attacks on quantum circuits are simulated by introducing random rotations around the Y-axis (`cirq.ry` or `qml.RY`) with random angles to a subset of qubits. This noise operation can disrupt the quantum state of the qubits, mimicking the effects of an adversarial attack.

The impact of noise or adversarial attacks can differ between the model with anomaly detection and the model without anomaly detection:

- **Model without Anomaly Detection**: Noise may lead to errors or inconsistencies in the predicted labels, but the impact is limited to the accuracy of the predictions.

- **Model with Anomaly Detection**: Noise can significantly affect the calculation of anomaly scores, potentially leading to incorrect anomaly classifications (false positives or false negatives).

## Mitigating Adversarial Attacks

To mitigate the impact of noise and adversarial attacks on quantum circuits, various techniques can be employed:

- **Error Correction and Fault-Tolerant Quantum Computing**: Implementing error correction schemes and fault-tolerant techniques to detect and correct errors introduced by noise or attacks.

- **Quantum Circuit Hardening**: Designing quantum circuits that are more resilient to noise and attacks, such as using robust gate implementations or incorporating randomization techniques.

- **Adversarial Training**: Training the quantum anomaly detection model with adversarial examples to improve its robustness against adversarial attacks.

- **Quantum-Secure Cryptographic Protocols**: Employing quantum-secure cryptographic protocols to protect the communication and data exchange between the classical and quantum components of the system.

## Significance and Applications

Detecting and mitigating adversarial attacks on quantum systems is crucial for ensuring the reliability and security of quantum computations. Quantum anomaly detection techniques can play a vital role in:

- **Cybersecurity**: Identifying and preventing adversarial attacks on quantum systems, which could compromise sensitive data or computations.
- **Quantum Algorithm Integrity**: Ensuring the correct execution of quantum algorithms by detecting and mitigating adversarial attacks or noise.
- **Quantum Hardware Protection**: Detecting and mitigating attacks or errors in quantum hardware, such as noise in qubits or control errors.

The quantum advantage in anomaly detection lies in the ability of quantum computers to process and analyze data in a fundamentally different way than classical computers, potentially leading to improved performance and accuracy in detecting adversarial attacks.

## Usage

The code provides functions to test the anomaly detection model with and without the simulated adversarial attacks, visualize the quantum circuits (Cirq), and print a comparison table between the two approaches. Additionally, it includes utilities for loading and preprocessing the MNIST dataset.

To run the code, follow these steps:

1. Install the required dependencies: `cirq`, `pennylane`, `tensorflow`, `numpy`, `matplotlib`, and `tabulate`.
2. Set the desired parameters, such as the number of qubits, batch size, noise probability, and anomaly detection threshold.
3. Run the `main()` function to execute the anomaly detection pipeline.

## Results

The code generates a comparison table that showcases the performance of the quantum anomaly detection model with and without adversarial attacks. The table includes the following columns:

- **Image**: The index of the test image.
- **Original Label**: The true label of the test image.
- **Predicted Label (Without Anomaly)**: The predicted label of the test image without anomaly detection.
- **Predicted Label (With Anomaly)**: The predicted label of the test image with anomaly detection.
- **Anomaly Score**: The calculated anomaly score for the test image.

In the Cirq implementation, the code also visualizes the quantum circuits with and without anomaly detection using Cirq's `CircuitDiagramInfo`.

## Contributions

Contributions to this project are welcome! If you have any improvements, bug fixes, or new features to propose, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
Contributions to this project are welcome! If you have any improvements, bug fixes, or new features to propose, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
