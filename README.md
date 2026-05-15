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

class KalmanFilter:
    def __init__(self, F, H, Q, R, x0, P0):
        self.F = F
        self.H = H
        self.Q = Q
        self.R = R
        self.x = x0
        self.P = P0

    def predict(self):
        self.x = np.dot(self.F, self.x)
        self.P = np.dot(np.dot(self.F, self.P), self.F.T) + self.Q

    def update(self, z):
        y = z - np.dot(self.H, self.x)
        S = np.dot(np.dot(self.H, self.P), self.H.T) + self.R
        K = np.dot(np.dot(self.P, self.H.T), np.linalg.inv(S))
        self.x = self.x + np.dot(K, y)

dt = 0.1

F = np.array([
    [1, dt],
    [0, 1]
])

H = np.array([
    [1, 0]
])

Q = np.diag([0.1, 0.1])

R = np.array([
    [1]
])

x0 = np.array([0, 0])

P0 = np.diag([1, 1])

kf = KalmanFilter(F, H, Q, R, x0, P0)

true_states = []
measurements = []

for i in range(100):
    true_states.append([i * dt, 1])
    measurements.append(i * dt + np.random.normal(scale=1))

est_states = []

for z in measurements:
    kf.predict()
    kf.update(np.array([z]))
    est_states.append(kf.x)

plt.plot([s[0] for s in true_states], label='True')
plt.plot([s[0] for s in est_states], label='Estimate')

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
