# RCJ_SOCCERSIM-AQIVERSION
Custom RCJ Soccer Sim (Webots) featuring a tactical 2-1 formation. Includes aggressive Proportional Control strikers with smooth curving, smart midfielders with kick-off delay support, and advanced sliding goalies with Heading Lock &amp; GPS clamping. Optimized for stability and coordination.


This repository contains the complete source code and configuration for a customized RoboCupJunior Soccer Simulation (RCJ SoccerSim) environment built on Webots. The project includes modifications to robot logic, team strategies, and referee rules, making it easier to understand, edit, and extend the simulation.

Each robot program (B1, Y1, B2, Y2, B3, Y3) is located in the controllers/ directory. The structure is modular. The Blue Team is inside controllers/rcj_soccer_team_blue/, and the Yellow Team is inside controllers/rcj_soccer_team_yellow/. In each folder, the file rcj_soccer_team_blue.py or rcj_soccer_team_yellow.py works as a router. It reads the robot’s name from the simulator and forwards the execution to the correct logic file: robot1.py for the Striker, robot2.py for the Midfielder, and robot3.py for the Goalie.

Every robot uses a combination of Infrared sensors to detect the ball, a Compass for orientation, and GPS for position tracking. Each role uses its own logic.

The Striker (Robot 1) relies on Proportional Control. It constantly measures the ball’s angle relative to its body and adjusts wheel speeds proportionally. This lets the robot chase the ball aggressively with smooth curving motion, creating a fast, “Brazil-style” attacking behavior.

The Midfielder (Robot 2) follows a Support & Delay logic. At kick-off, it intentionally starts slowly to give the Striker room. Throughout the match, it focuses on keeping distance and only moves in aggressively when the ball enters its defensive radius.

The Goalie (Robot 3) uses Lateral Tracking and Heading Lock. The robot stands sideways and maintains its orientation using compass data. When the ball enters the goal area, the robot slides left and right to block it, while GPS keeps it from leaving the goal zone.

Match rules are controlled by the Referee Supervisor, located in controllers/rcj_soccer_referee_supervisor/ and the referee/ module. Initial positions and formations are defined in referee/consts.py. Penalties, goal detection, “Lack of Progress,” and general game flow are handled inside referee/referee.py. Team names and match duration can be adjusted through rcj_soccer_referee_supervisor.py or environment variables. In this customized version, the referee logic has been tweaked, for example preventing unwanted goalie resets and allowing strikers to search for the ball without penalties.

If you only want to watch the match, the latest revised files are available on the provided website.

You can also customize each robot’s visual appearance. The simplest method is replacing the default texture files (such as blue.png or yellow.png) in worlds/soccer/ with your own images using the same filename. Alternatively, open soccer.wbt in Webots, locate the robot node, and change the ImageTexture URL to point to your custom image.

All these modifications make the simulation more expressive, both in strategy and appearance, and give you plenty of room to refine team behavior or experiment with new ideas.
