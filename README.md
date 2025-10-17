<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: Saravanan N</h3>
<h3>Register Number/Staff Id: TSML006</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
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
<h3>PROGRAM</h3>

```
python
import random
rooms = {
    "Room1": {"temperature": random.uniform(97, 102), "treated": False},
    "Room2": {"temperature": random.uniform(97, 102), "treated": False}
}

performance = 0
class MedicineAgent:
    def __init__(self):
        self.current_room = "Room1"
    def sense_temperature(self, room):
        return rooms[room]["temperature"]
    def treat_patient(self, room):
        global performance
        temp = self.sense_temperature(room)
        print(f"\nChecking {room}: Temperature = {temp:.2f}°F")

        if temp > 98.5:
            print(f"Patient in {room} has fever. Prescribing medicine...")
            rooms[room]["treated"] = True
            performance += 10  # increase for treatment
        else:
            print(f"Patient in {room} is healthy. No medicine needed.")
    def move_to(self, new_room):
        global performance
        if self.current_room != new_room:
            print(f"\nMoving from {self.current_room} to {new_room}...")
            self.current_room = new_room
            performance -= 1 
agent = MedicineAgent()
for room in rooms:
    agent.treat_patient(room)
    if room == "Room1":
        agent.move_to("Room2")
print("\nFinal Performance:", performance)
print("Room Status:", rooms)

```
<h3>OUTPUT</h3>
<img width="1508" height="351" alt="image" src="https://github.com/user-attachments/assets/c6bfb333-eb86-4d9b-9b23-56cd3d88ad33" />

