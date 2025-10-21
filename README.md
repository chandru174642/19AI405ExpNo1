<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: CHANDRU.P</h3>
<h3>Register Number: 212223110007 </h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h2>Theory</h2>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

## program:
```python
import random
import time

class HealthMonitoringAgent:
    def __init__(self, rooms):
        self.rooms = rooms                     # Environment (list of rooms with patients)
        self.performance = 0                   # Performance score

    def sense_environment(self, room):
        """Sense the current room and get patient data"""
        patient = room["patient"]
        print(f"\n➡️ Checking Room {room['room_no']} - Patient: {patient['name']}")
        return patient

    def choose_action(self, patient):
        """Decide action based on temperature"""
        if patient["temperature"] > 38.0:
            return "Prescribe medicine"
        else:
            return "No treatment needed"

    def act(self, action, patient):
        """Perform the chosen action and update performance"""
        if action == "Prescribe medicine":
            print(f"💊 {patient['name']} has fever ({patient['temperature']}°C) → Medicine prescribed.")
            self.performance += 1
        else:
            print(f"✅ {patient['name']} is healthy ({patient['temperature']}°C) → No action taken.")
            self.performance -= 1  # Slight penalty for unnecessary movement

    def run(self):
        """Run the agent — visit each room once"""
        print("🏥 Starting Health Monitoring Agent...\n")

        for room in self.rooms:  # Visit each room once
            patient = self.sense_environment(room)
            action = self.choose_action(patient)
            self.act(action, patient)
            time.sleep(1)

        print("\n📊 Monitoring Complete!")
        print(f"🧾 Final Performance Score: {self.performance}")


# -------- Environment Setup --------

def generate_patients(num_rooms):
    """Generate random patients with temperatures"""
    rooms = []
    for i in range(1, num_rooms + 1):
        patient = {
            "name": f"Patient_{i}",
            "temperature": round(random.uniform(36.0, 39.5), 1)
        }
        rooms.append({"room_no": i, "patient": patient})
    return rooms


if __name__ == "__main__":
    # Create environment with random patient data
    rooms = generate_patients(5)

    # Initialize and run agent
    agent = HealthMonitoringAgent(rooms)
    agent.run()

```
## Output:
<img width="841" height="752" alt="Screenshot 2025-10-21 094802" src="https://github.com/user-attachments/assets/3be776e9-c23f-43d0-bdb3-1c503afeeab4" />

## Result :
Thus the code is executed successfully
