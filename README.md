<H3>Name: DEEPIKA R</H3>
<H3>Register No: 212223230038</H3>
<H3>Experiment: 5</H3>
<H3>Date: </H3>
<H1 ALIGN =CENTER> Implementation of Kalman Filter</H1>

## Aim:
To Construct a Python code to implement the Kalman filter to predict the position and velocity of an object

## Algorithm:
<b>Step 1:</b> Define the state transition model F, the observation model H, the process noise covariance Q, the measurement noise covariance R, the initial state estimate x0, and the initial error covariance P0

<b>Step 2:</b> Create a KalmanFilter object with these parameters

<b>Step 3:</b> Simulate the movement of the object for a number of time steps, generating true states and measurements

<b>Step 3:</b> For each measurement, predict the next state using kf.predict()

<b>Step 4:</b> Update the state estimate based on the measurement using kf.update()

<b>Step 5:</b> Store the estimated state in a list

<b>Step 6:</b> Plot the true and estimated positions

## Program:
```python
import numpy as np
import matplotlib.pyplot as plt

dt = 0.1

F = np.array([[1, dt],
              [0, 1]])

H = np.array([[1, 0]])

Q = np.eye(2) * 0.1
R = np.array([[1]])

x = np.array([0, 0])
P = np.eye(2)

true_pos = []
measurements = []
estimates = []

for i in range(100):
    true_position = i * dt
    z = true_position + np.random.normal(0, 1)

    x = np.dot(F, x)
    P = np.dot(np.dot(F, P), F.T) + Q

    y = z - np.dot(H, x)
    S = np.dot(np.dot(H, P), H.T) + R
    K = np.dot(np.dot(P, H.T), np.linalg.inv(S))

    x = x + np.dot(K, y).flatten()

    true_pos.append(true_position)
    measurements.append(z)
    estimates.append(x[0])

plt.plot(true_pos, label="True")
plt.plot(measurements, label="Measurement")
plt.plot(estimates, label="Estimate")

plt.legend()

print("NAME: DEEPIKA R")
print("212223230038")

plt.show()
```

## Output:
<img width="565" height="456" alt="image" src="https://github.com/user-attachments/assets/68f0841b-a4c3-4045-9df3-40e0d071d123" />

## Result:
Thus, Kalman filter is implemented to predict the next position and velocity in Python

## Result:
Thus, Kalman filter is implemented to predict the next position and velocity in Python

## Result:
Thus, Kalman filter is implemented to predict the next position and velocity in Python
