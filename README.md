# Quantum Circuit Anomaly Detection Against Adversarial Attacks

This Python code demonstrates a quantum anomaly detection approach using the Cirq library, designed to detect adversarial attacks on quantum circuits. The code simulates adversarial attacks by introducing noise in the form of random rotations on qubits, mimicking potential real-world attack scenarios.

## Quantum Circuit Design

The quantum circuit used for anomaly detection is built upon the following steps:

1. **Data Encoding**: The input data (e.g., MNIST handwritten digit images) is flattened and scaled to the range [0, π]. Each scaled value is encoded as a rotation around the Y-axis (`cirq.ry`) on a corresponding qubit.

2. **Superposition Creation**: A Hadamard gate (`cirq.H`) is applied to each qubit, creating an equal superposition of all possible states.

3. **Adversarial Attack Simulation**: To simulate an adversarial attack, random rotations around the Y-axis (`cirq.ry`) are applied to a subset of qubits with a specified probability (`noise_probability`). These random rotations represent the injected noise or errors.

4. **Measurement**: Finally, all qubits are measured using the `cirq.measure` operation, and the measurement results are stored under the key 'result'.

The quantum circuit is designed to be sensitive to changes in the input data and the simulated adversarial attacks. By analyzing the non-zero amplitudes of the final state vector, the anomaly detection model can identify deviations from the expected behavior, indicating potential anomalies or adversarial attacks.

## Anomaly Detection Algorithm

The anomaly detection algorithm calculates an anomaly score based on the non-zero amplitudes of the final state vector after applying the quantum circuit. A higher anomaly score indicates a potential anomaly or adversarial attack.

By comparing the results of the anomaly detection model with and without the simulated adversarial attacks (random rotations), the code demonstrates how quantum computing can potentially enhance the detection of adversarial attacks on quantum circuits.

## Significance and Applications

Detecting and mitigating adversarial attacks on quantum systems is crucial for ensuring the reliability and security of quantum computations. Quantum anomaly detection techniques can play a vital role in:

- **Cybersecurity**: Identifying and preventing adversarial attacks on quantum systems, which could compromise sensitive data or computations.
- **Quantum Algorithm Integrity**: Ensuring the correct execution of quantum algorithms by detecting and mitigating adversarial attacks or noise.
- **Quantum Hardware Protection**: Detecting and mitigating attacks or errors in quantum hardware, such as noise in qubits or control errors.

The quantum advantage in anomaly detection lies in the ability of quantum computers to process and analyze data in a fundamentally different way than classical computers, potentially leading to improved performance and accuracy in detecting adversarial attacks.

## Usage

The code provides functions to test the anomaly detection model with and without the simulated adversarial attacks, visualize the quantum circuits, and print a comparison table between the two approaches. Additionally, it includes utilities for loading and preprocessing the MNIST dataset.

To run the code, follow these steps:

1. Install the required dependencies: `cirq`, `tensorflow`, `numpy`, `matplotlib`, and `tabulate`.
2. Set the desired parameters, such as the number of qubits, batch size, and noise probability.
3. Run the `main()` function to execute the anomaly detection pipeline.

## Contributions

Contributions to this project are welcome! If you have any improvements, bug fixes, or new features to propose, please open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
