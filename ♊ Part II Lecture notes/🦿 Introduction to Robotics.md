- Lecture 1 - Introduction
    - What is a Robot?
        - A robot is an {{autonomous system}} that exists in the {{physical world}}, can {{sense it's environment}} and act {{on that environment}} to achieve some goal/s. 
        - Autonomous robots makes its own decisions and is not controlled by a human.
        - Building robots is becoming more affordable due to 3D printing and cheaper parts.
        - Robots are useful in the 3 D's - dirty, dull or dangerous. These are tasks **a human doesn't want to do **but need to be done. - So she says 
        - How does optimization improve robots' usefulness?―Giving robots a task means that process becomes computable and can be optimized over - this can make a task more efficient, safe and fast. 
For example, automated vehicles working together to optimize driving. Similarly, truck platoons to reduce drag & increase fuel efficiency.
    - What this course is about
        - The basics of autonomy are―Perception, decision making and action - these are controlled by the control architecture. 
These are instantiated in different ways for different types of robots. For example in mobile autonomous vehicles - Perception ⇒ location control, action ⇒ motion control,  decision making ⇒ Reacting now and planning later
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/4dLjRk7hmirbCLzLJaLnTx3rsKAsq2TVamuf1HFR2UEmehiakpdaB9jP4lBqdn6mToxKo3RsjiPPNH_bRGCHk9IpLsBAUOCEhk37opMZLwzzA-m9E64hbOZEQgiNKRiq.png)
        - For multi-robot system you build upon these and add communication between robots.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/IhEtcFCqltUjJCKuWWBavdtG5voeJ9guplmoWUY95r4ng0moy2oztMYCcucWaxTRCZQ-WUXpaDCl9e1n0CZAAF0ijhOp4b_D0LnJa-TJcZOJF8v8HdHN601dO__4t2Jz.png)
    - Basics of Autonomy
        - Robots provides implementations of the following 3 modules - it also provides an architecture for combining these 3: Perception, action and decision making are useful for respectively― ↓ 
            - Sensing and modelling the world
            - Processing that information and taking action - for example modelling how exactly the motors must be actuated to reach a goal perception.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TcUskQ-0F4yHWTWhfg7uLDG10OiVXL5IFi3wTv5fmmpWoBuDg6SJNX7wkoCMY86jepIzJ73IdclBvMhVEygf6r2wDDA8Ol7g1SosefXQHC_wO3aE9QMwPDJNFCmAw8FB.png)

            - Reasoning and planning in the face of uncertainty - for example compute a path to a goal that does not collide with any objects.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dNChga1JzEDOSGVioShUVMeFL1j-B0C5pC-783i2oKSAQRR23uaL8j6FYRM8_L5ZY3SvmHw2TfJte3MmVVXHLGXFCqs1v_hPwXwlggQM7QX5ckNoc4cd2OGiWon1LnRg.png)
        - What are proprioceptive and exteroceptive sensors? (These relate to perception)― ↓ 
            - Proprioceptive sensors tell you something about the internal state or the actions of a robot. For example a gyroscope that tells the robot it's orientation or an **odometer **that tells the robot how far it's travelled. 
            - An exteroceptive sensor tells the robot information about it's surroundings. For example a camera or a microphone.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yJjm6NbYX16kThqAVT9kk3sfE8a8vX6sWwUibNxQ81aUdnjI_lQO2JHMEyO1fXijTG8RK6RRFfJqtgW6-mJAOUB3w24oO6Wc1f_YTWogt-5T4X0RCFMmnDWuzR_wwLJi.png)
    - An extremely simple robot
        - Consider an early Roomba with bump sensing, cliff sensing, wall sensing and an optical encoder (measures how far the robot is travelled given how much force it's exerted on the wheel.)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WkqUsmtV5kXarBYGNxlOpLuV1GjIPNDyPFoRcYLEu08WO_j231_ssD80CyxXqfHQ_dsqL9nWX6953j_Z9BJc7gIVXQSvIMEY8CDB7UjOsjXPCHxMgaxstTUp2HtlmWKd.png)
        - These simple sensors allow for wall following if it bumps into a wall, spiralling if it finds a dirty spot and going straight (turning at a random angle if it bumps into something or has travelled a certain distance)
    - The history of Robotics
        - Robotics came as an influence from Control Theory, Cybernetics and AI. 
**Control theory** being the mathematics of controlling machines, differential equations being very useful.
**Cybernetics **being the integration of sensing, action and the environment.
**AI **at the time being classical AI of decision making, not a neural network in sight. 
        - The first Robot:, built in the 1940s!
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RtHTPVNS71uj3CPAmZXDOJcmhsTduWilp538NIpnbr2bMIoIm1jxkKj-jzHR-_ith3OJ3_Payhq4VZv8XvbnMD4U0eh-0uAa8ktPcEKHiALP7gJKHpDlQb5fQeSP1sUn.png) 
        - Braitenberg - a famous scientist who considered **reverse engineering **processes to reproduce the same behaviours we see in nature. He tried to reproduce complex behaviours with simple robots (Gedanken experiments, not real robots) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/V2kO3cSVXb6Eqpj6tHqEC3qWriGIFeypVgdrYWsshlkFoy6ebG-r5dRvyJ6E_ju7c9rldF3SopbP_fAfeGtKP5drKlntiaY8M93T7pxmr0gHp6NASI2OSqfBRATpq5Np.png) 
    - Advent of artificial intelligence
        - The origin of AI is said to be a research project/workshop in Dartmouth with many famous researchers. They decided on 6 things that needed to be in place for AI:
            - Internal models of the world
            - Searching through possible solutions
            - Planning & reasoning
            - **Symbolic representation of information **(How do we do this - should it be human understandable?) 
            - Hierarchical system organization
            - Sequential program execution
        - They then went forth and built **Shakey **(a robot that shakes when it moves). It contained cameras, vision algorithms in the black and white world. 
        - Describe the paradigm shift away from Shakey an early robot―The problem with shakey was that it implemented classical AI planning algorithms in an age where the compute was to slow to support it. As a result the machine was too slow to accomplish any truly useful tasks.
The paradigm shift was moving away from this long term planning, and making robots more **reactive**. Based around decisions on what the robot can perceive **right now**. This is called behaviour based robotics
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7MbNzFo2YsBf5os4q7XRdTcHNxW2iNDJv5s9bHqXp7wso5IxM7lw5IjjDvKMolZXFz8_WUILBz245Y-Ts-F0DFu3pOBLS6YFlh7qhAIR18SkfUXapQf-sTh9WZWns_bl.png) 
        - Behaviour based Robotics
            - Basic rules giving rise to reactive behaviours. 
            - Didn't take heavy compute.
            - Lead to swarm intelligence:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Eu_rnHkVXcAJ_iPcyNjZbPK3PS9JAYSeUzc673IgFPnDRR8He3zg-2IWjbdT3S1xJiVZms_yjC40UcCpd6Jxl46ilGMyP_ei9G6ZUJtRslQVkmO0DjRySrQ8ClgoUrqi.png)
            - Also useful for:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/2BajjF2B4I_OIn1Iwv9C3L46HXiVTdos5EyjG8SulK1gcynRxjjq_cr3UOdmipsGysmtAHCu8vvtshDBq9oSdwyZOe0ev0Qd3hkHbuhyW9QtAXzn2p18-UeAAjFKwpXj.png)
- Lecture 2 - Control Architectures
    - Perception-action loop 
        - Need to consider what is the robot and what is the world
        - What are the three main variants of robots employing the perception-action loop? ↓ 
            - Reactive without memory. Usually instantaneous reaction 
            - Reactive with memory. Acts on new information conditioned on older information
            - Deliberative. Foresight, planning, goal-orientation - models the interactions first and then takes a step.
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/osgYzbV12rSuEsmBTn8E1e_GEBn5YwXdHWzRoGGZtS6jHSLOy_0sF1NBOWOub9NsjaGzadcJJMtGyio38F-sQhZtRClePOQ3q-tWiXP-fkHqUhMkGkpwk6yGcbK4rySt.png) 
        - A robot on the moon will receive information after 2.5s - so we need to be able to make predictions 2.5 seconds ahead, we don't want the robot wandering into a crater because we haven't given it any 
        - What's the differences between reactive and deliberative schemes― ↓ 
            - Reactive robots have control using **current **estimates of the world, time-invariant rules produce the action - FAST to compute. Braitenberg vehicles. Don't provide guarantees on conversion, or optimality.
            - Deliberative schemes make predictions of future stats - they then take **sequences **of actions to **optimize **some metric. A* algorithm. Need to have a model of robot and world, does provide optimality guarantees.
        - Describe open-loop vs closed-loop planners― ↓ 
            - Open-loop planners do not adjust their internal representation of the world as they go - i.e. after the plan is done, close your eyes and follow it up.
            - Closed-loop planners update their plan as it goes, if a table has wheels a Roomba will need to update it's position when it bumps into it. (**Model-predictive control**) 
    - Control for Wheeled robots
        - Five basic types of 3-wheel configurations:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/SCX7RrqIrRtdBjVAylVtM3c4SjrO9XZGmyz-SpTo9kFMmuI_aT6tt6BaAsF45GrrGqPIKiOQdKfjjcyO3fRxABBqMcM1WRd5_0pZEqzI2E0zEqF5S1In0KUZbhNV_EI-.png)
        - Omnidirectional - more difficult to design, and more expensive.
        - Swedish wheels - allow the robot to move in any given direction, no turning constraints so popular in factories.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7GkVjQICwDWrINRK2j9YSroxx-ct7yKqxKVf9LAdtes4waxzem_Wx3LofaHwgkRyOjFXaLt9Cbnur1Td8wV_EmzcL1AquuXxM6-3n9A4YgJ9VNO14WqfqKAe-cgrljP6.png)
        - Kinematics
            - Describe forward kinematics―Given the control parameters (you know how you're moving it, e.g. wheel velocities), and the time of movement $t$ - **find the pose **($x,y,\theta$) reached by the robots. 
            - Describe inverse kinematics―Given the final desired pose ($x,y,\theta$), **find the control parameters **to move the robot there at a given time $t$. 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1E6Z3lxiKCMQqohVlXO1spZmspfQ5ZWWy9Au5OsArQAg4MRhmpiRahiL8WBcGuuOcrhh2OBT77iQjs9oBvBDPMuciqembQF9JiiymzmWzlL-AlETZa4EK7houXvTriZD.png)
            - Differential equations describe robot motion, for the differential-drive model. Remember **x cannot change without y changing**.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YaK6pUMHSwF3Y3DbBdR98byEdkVC2D0VKx6dOk7c1u5DVUpCdGZOg-DAxvMYs1a1DOemS_cEO1Wz4pjm784d6xodaJwwiuEE7KEwgrrBzXNxi-hTMZ_UwnT4_aBVtiPc.png)
    - Braitenberg Vehicles
        - An imagined vehicle, gedanken experiment.
        - Make a braitenberg vehicle card―TODO 
        - Purely **reactive behaviour**: ...  
        - Motors and sensors, with motors connected between them - exhibitory of inhibitory, the more excited a sensor is the more it will drive the motor:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/NGbN-l_GIi-9TsvXoHv6wx7u30yPvwyy_rFpFv4t22Oizqt35-akdPr_lArdDF_BXik0Oo9vOqdMJrHUanolr7JR2Rl7M60I5KMm7cPq-7b6czaCSY6RdZCKK8L0OmIa.png) 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QkkRd_rwB6HxYm8N1rLdJpRnlSxyEPQ_1OJi9sLocorhTMtF7ecS6lmWdwW_6S3xtQAHYFyQTMwHOrXMzo7STgKu_Kk4d5XtzVFMzPBOKRyQGSnzOdqn447h3h5Rx6N0.png)
Analysis through synthesis. 
        - Applied Braitenberg
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tWvgLq3hE4UttFOzYZpq4BWwRCkpAn2RAd1l-nFJvakrxHqqGCoX4BKFmVKhG7GqJSPhLwT7rN2fELHK9i2zZVrSDXS3MRY2uG2BJGJHnPYhQoPUPyytYaGMLSl1xiJu.png)
Base forward velocity, and a weight for each left and right wheels - will the sensors be inhibitory or excitatory?―Inhibitory, because we have a bias for forwards velocity. 
        - Artificial Neural network
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pBJFX4k6olsEsS5Ah6OGvJEHQujHbXArthYgiVA5uy-LlMwwyG0e6vus6LS_62WBnWwQEc_E0oeluhcfQty8XQrJHp7z7fpGMZmD_98SbuFekHocdRrExaQhQZKzvYbX.png)
Neuros responsible for input to each motor, they take input - apply a weight and add a bias. Then we take that and apply it to tanh - a formalizable and differentiable function. 
    - Control Architectures
        - Pick up the trash competition, where robots were tasks with finding red soda cans and putting them in blue rubbish bins.
        - Finite State machines
            - Extension of the Braitenberg machines with memory. Transitions are perceptions and states are actions.
            - Example rubbish robot FSM:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bS_q2mG3jkhnszBcB2pHnCM0G1DLRmcrgL0MX-pwuMEMdk7N2WXF9DxP-eR_5I3Zqo9VrF5q_Y3paWv0FjhKDn1CuaJiF9Evo4udGQhhMGF8tbxSiYAZX0PHMjkdhc44.png)
            - Need lots more state transitions for if we drop the can, can't grab it, can't drop it etc.
        - Two paradigms of Serial & Concurrent behaviour
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VIGkOtwGUMpZTn_xmbgprHgCfUuBxMAXKVpoFZxitVFSr_7g1eFQPJDgYh4fIyLKzr2qHn1fjzyptB49D6bmqsa2cfK1GWwnFJRGBYX_fQvCLUFZn4f1QEKN9x9-ia9C.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JJEqI7fykyUN8Is-XNkDmKidJNZRN1_Hxv_zV9ubDZNUTdpkBDfOHcAJ32SDcIAaRVffh3z29hwn7JR226GxSPbsl847Hgy6cjiUS7WwLA2mA-ea1R_zxhZ3wA5w393l.png)Many smaller brains given partial control of the different motors.
**Need **to be able to  __prioritize__  and  __combine__  actions!
            - Robot has several behaviour modules (basic behaviours), each of which is represented by an augmented FSM. Then the response t o sensor input is predominantly rule-based (discrete)
            - Coordination of behaviours: priority-based, via **inhibition **and **suppression**. 
        - Subsumption Architecture
            - Describe the subsumption architecture―Inputs and outputs go to and come from the behavioural module - these are inhibited and suppressed, the suppressor will **replace the output with a different signal. **The inhibitor simply stops the input.![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/uXCTIuvi9KRaRcp59_CPh3iVze0QFqr8t6wRJuB4qwYvFtupAM30R93sFtx-38qjKkLPO3SR6pCZkt5PVwi0W5zu_gtjqSxrUZHrKvdtzO1Bh0W5-xOZxUbAgcojLarI.png) 
You then stack multiple layers, where higher levels **subsume lower levels when they with to ** __take control__ **. **Each layer runs independently and concurrently:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T2tKHlCVAB0I5mTRcFAbByCWbCvzZmygWOoK9DKs_Qu9iXQjpuunX3Wy0xN3_oWmJTicPohkmF9Uka9LrE5khX9gPR_4tOzB6tpxDiM2IHrTxg9OAiFAfw6huF9c6Gpj.png)
            - Example Robot:
                - Layer 0: Make sure the robot doesn't come into contact with other things
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/zkhntYURyW2kyBCO367flhzegfbZ2wrsczjub5_KhgsO13g5NMX-e1ItTykM3TcA0WnFGIWPl8sy4RnY50WbUyZI9PlJzqdZcAh-iPnNXh0HvHn39vcnTuTeWaBVO58h.png)

                - Layer 1: Ensure the robot can wander and explore without colliding - we can **subsume **the runaway force to allow for **avoiding **objects.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yS21fmFjbcys77UUTrO1GQeGCDGUavdpRdPOPwJuizmxH2gLw1HFbPpEZOszOHXF9CFx2F1-glu8VSPIFftR9TRtyr25CEL0sRqrO3fIjk9nztzMztIQXo4-Yj96b6wR.png) 
            - Pick up trash in the Subsumption architecture:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tddt1aR9s2X4Cq67LnAAPvyBTqR19FTgStOXkSYkyAmYPNB0UJGhjex15XUYtNXp1N3l5iLbpCQniizPRgGLiA0tZ2KlmICFBtN85IyAavNtblc0b396CqhcIjaIt6vJ.png)
Explain the inhibitors and supressors here: ↓ 
                - TODO
        - Sense-Plan-Act
            - For pick up trash - we sense and construct a model of the world. Then invoke the planner, then execute those actions.
            - We note that the world would need to be static, complete and error-free. Furthermore, the sequence of actions should be optimal. Finally, the motion plans in the execution should be optimal. 
            - make flashcard on sense-plan-act―TODO 
        - End-to-End learning
            - We form a sensor-model - for an infrared sensor, the higher the voltage the closer the object **and this relationship needs to be calibrated**. Rather than calibrating by hand, we could learn that relationship using machine-learning. We can learn the world from our sensors.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QNIATEwF5bcAHu5cv80BCHquGmBHsxB1D5_UK5AqIz8tqbN5h8L_l-CWLuKCwY7e8v4V69w6yRObn0URom0EydtYJ7r73S9BX8EYPEbx1uipj9afP357t1eJiFRYh-dM.png)
            - Similarly, it may be more efficient to learn a motion model than to do it by hand - if we want to know how to move a quadcopter, we cannot know the exact effects of wind. 
Similarly, search algorithms can be altered by learnt heuristics
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/88g3A4_YSrMdCM_w3JrAzzaXh-Vwf150VvXtVQafkAXDrKOlrvpePZTucfMPJnR--kmwI7avIEs3LHWTPoRXjE-48AaXQZ6kVbwnqB3p97cJ_ALAg_PjLbRceMnyIB_F.png)
            - Finally, actuator models can be learned:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EELxn6Zxooe17NTnIkzM8rerh_IT1KCM-jUlyN2qWRQxttgyaS7yC4nY9iVadWQ1GFFSf0iSxeO1odZT5N54hLBLvRsC2vddSZPXAUFJMRqnAV0FPnJ9GS505mHQHvWW.png)
            - **But, **the fully end-to-end system is one with the sensor input going to a neural net and the output goes straight to the actuators:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/j4GEBPMcNpiOgf2Tn57u5NK5zODMHUwaCVHUXolMWwprd-tG73Hb0H6qcQSK0TlHYUGpwlG6ArqyuQHLPVpixMHZvRrpKDO46yEDF-sLkKjyi5WzwB_-R-4flLv_vqAU.png) 
    - Current trends in control architectures
        - Principled architectures being replaced by end-to-end mechanisms
        - Challenges:
            - Where does the training data come from?
            - How to generalize to arbitrary environments?
            - How to transfer from simulation to reality? Can we model friction correctly, if I train in situations which differ from reality I'll learn bad/wrong habits.
Red gripper in simulation, blue in reality and it won't work.
    - Considerations for control architectures
        - What is the application?  
        - Need for parallel behaviors? 
        - Is the environment very dynamic? 
        - Robustness to failure and large uncertainties  
        - Computational complexity 
        - Need for re-planning? 
            - How often? 
            - On-board computational constraints? • 
        - Fast + reactive, versus slow + deliberative 
        - Predictability of robot behaviour (proofs and guarantees)
            - Can we guarantee that robot will reach goal destination? ‣ Can we prove that the robot will never collide with a human  
    - Decision Making agents
        - Environment receives agent actions, and emits the next observation and reward. 
We then want to **maximise **the reward. 
- Lecture 3  - Introduction to Kinematics
    - Robot motions
        - Motor controllers connect everything together.
        - Different purposes for different robots - wheeled, legged vs manipulation vs heating or sound emission.
        - How many control inputs are there for a RC car driver?―2, steer and accelerate (ignore each wheel steering) 
        - Degrees of Freedom
            - Most actuators control a single **degree of freedom** - a motor shaft controls one rotational DOF< a sliding part on a plotter controls one translational DOF―todo make flashcard 
            - How many degrees of freedom does this robot have? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/YtA3Gww1aAKp-7ccl9Bpi7xGy45i0RNoc2WJZAEVJfw7Q9_zyANtVVN-DVv1F25IJNffeCITpwwXCSd9OMAgLN9HJgRTHbpQsp78t4KMxuuPE2k59WvgCcZE5715UoAD.png)―$x, y, \theta$ so 3 degrees of freedom.
        - Holonomic Motion
            - Degree of mobility―Number of DOF that can be **directly accessed **by the actuators. DOM = 2. E.g. this robot cannot move in the y direction.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9xe29Ue-GCOBTKliIQvqI7usY03cmhfTFuePxjMwBP2X-jUO3Nkm_YDSCkdjpkGkWEXyINJp_BDfUBKx-vF_e1TmGDZCX2JQ8l6VWfGk6tVA9UgVHpWlb3QB_PxukvU5.png)
            - What is a holonomic robot?―A robot where the number of DOF is equal to the robot's DOM. 
            - Describe the main problem with non-holonomic motion―The robot can activate the motors with the same power, but at different times and end in a different position - meaning the history impacts the movement. 
            - An example of a holonomic robot:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DvolksPW4U8inlOksuI3fgbAwyagFFy6_LmCWzRHyakyY0MxzFeGtOOa-0ZTmO5mgA3DK8LVYk9R-I9agdWOmuyAi50V-yqBhR-ATWHNCuqeWnpuJ98AU61qQHSFQ0c4.png) 
        - Distance, Velocity, Time
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_698dKJRcC6jvaKkktOB0pr10ZtCos6x_kW3uNGqBt7ESqA_mghqF2aqAuzGaDk2uBQJfPyd0S66s5tYBu-RSdGOSymh2vbbgIPT2ywsinnGPCKckWL00AYxXCqWmhLZ.png) 
        - Forward Kinematics
            - Differential equations describe robot motion
            - Give equations for the x, y and theta for ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GxbsSWk1Fdpe9GhpCbWQab1MMaTgklmBtVseh2b3CW1xLRVYKJhK62TOal0tGEcXDQx9rITxjiH9LSZCEgfsU6LKctj1un9Xo1kT9A-BD9QyBvv3OxbBRUVIDTMkOaUE.png)―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/caNPb_mRMk92UMUJDFtF5HUeDRkWiSKT-R6dR8tQNElEtLkGrQeYgcoatdC4BbNu2mpc0HOWGtAVb6oq7JpeCH2zXh9BelVZATkoR442TeiOCz3zUTubEIVE0K5yW4cu.png) 
            - For diffferential-drive, we have left wheel speed **and **right wheel speed. Describe the equation for total velocity and rotational velocity
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5UvHNWTiUaA73YZQhupoajrHqgNVzlziS5HYFY4ofzWdpIBJ65vMjNu5MkpDO5Je_WbzrVVvzUNEjgF1gBXqORvxHHRNt9DgR9O-qArhH6UqykB7oWooJV1OPHuQBUaP.png)―The total velocity is thus the average of their rotational velocities times their radius:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9mDxpCS68JpLbpXDyLiCwpSfBO6oD4LeGFYBrh5tQH7srgNwgQqLDTdy-QNBsjESDpYP8evaVKPzQbvTDeAHnZUm-pyra6xL5DEKvS3t7GQ1Xur3c3aMb_HBQ5won4i9.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/9mDxpCS68JpLbpXDyLiCwpSfBO6oD4LeGFYBrh5tQH7srgNwgQqLDTdy-QNBsjESDpYP8evaVKPzQbvTDeAHnZUm-pyra6xL5DEKvS3t7GQ1Xur3c3aMb_HBQ5won4i9.png)
            - Moving from local to global coordinates using a rotation matrix
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/EA43mkIj4dN_5kt0cS0G4JatNNYoCowj7Hp6RFLMpriCJiltXr5TpxHYjZBkAvFN3JpLSsjbRfqDli7XRptzO5kCnATGWzKLPWTvTvfA9zz5M2-Lg5kOco8L5-nkaT0M.png) 
            - A second-order model
                - More is needed for a quadcopter, because the rotation of the wings no longer directly corresponds with the vertical velocity.
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i-MRBJbGGPWJMmnl-tT3JrGGoj-jjMwFKExk2gtJTego9xWj3GaZ5TX99cYQBmTJGPlIgnhTTpGUutQeNnO7S0ony7_cM6VGMuruP5sZSW9hJjGM138XY6VVTeIODydd.png) 
        - Inverse kinematics
            - We invert the previous equations to find control inputs - this is done under the constraints that $\dot{x} \sin \theta = \dot{y}\cos\theta$ 
            - If our robot was holonomic - what equation could we use for inverse kinematics?―![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/XIuFH5Olkj_jBwyCliemrTRLSK4pEbRDFo5sj9OqTYnwQU-pkvEDCM19bR7EvQktH5KHiKRNYsylZrE_Vw_fQqDGksVFJDLSO5Fk9GFNVHixlVug8cx7MiNH6UR03wSJ.png) 
Just adjusting each dimension independently over time.
            - Trajectory Generation
                - To satisfy our constrains, we need a smooth trajectory. For example Cubic Bezier curves ensuring the robot waypoints lie on a feasible trajectory:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ldx5jh-7-lcEZo1XAF8t-kgoTagU235vXLE00GqmvxjffcEols0rcnkjV5wND1kGsPwCNf_cLlEA4eibC4RX8ALVGZpSi_boLOhggPGFjk5cXGGwuRI6qGmhC5PEDfyN.png)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/3SYpxUB-oYMqBhOmyg7ZANyh-NJc1lyQ9kIsmMuF45W6WB0sjFU6MmcIVjP9Q7YhxYCMnYu4uu94jDVNmi29q2OR8OfJaPpMAjHgXJgxp-_X-TJyM1L3Yx6mvXZKVhtg.png) 
            - Feedback Linearization
                - Imagine attaching a robot to a rod that can move holonomically, then view the effects as you move the rod directly to the desired point.―TODO go over these slides wtf is this 
            - Describe open vs closed loop trajectory tracking―Open-loop means the robot blindly follows the path - closed-loop means the robot stops and checks out the environment as it goes. 
            - Closed-loop is beneficial because― ↓ 
                - Noisy sensors could cause wrong estimation of position
                - Noisy actuation could mean we don't move how we think we move
                - Unforeseen events, dynamic objects need to be handled
        - A simple closed loop controller 
            - The robot measures the error and corrects, using an on-off / bang-bang controller. If error is in one direction, apply one motor, otherwise apply the other one.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sxGBncesz2w_boWQZFO-bP9VCrjLc2LsIoBAtuC4_cBzlbh-KhTur_-3I989hUkHw26v5gq9LkxacERwYHnhqOWXn7xhzE3qumP4GfDUdOlcEz1d9w9lFoTB00PiFi2x.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/xzzA7IoqLWi2IE00eX9SdwRXQqqlCsuUl7OPTWuw5iGnPYT48oBFjs4m9V5WodVetC58drHQzSlEuCO00i7a39M0TbmEQttVpmNgS6OXLHBTChOqgNr9yt58Hb-ClvCL.png)
This results in a zig-zag behaviour. Note that error is a Euclidean distance - i.e. a single number
        - Proportional control
            - The robot adjusts control as a function of error - the lower the error the lower the motor output. Note that you do this continually!! Meaning that the robot will start adjusting error immediately -
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Cm5m6yVA2mEfhadp9HY_xQ_xFUdNhrqn_dX8PHuhd-TfM3x12Bh7XAj6xPWSvxVlOJZbj19p35Jnt8A2gdl6ovN22yCPr7uW33Z15KvRhtEGwYxKBhfNUGGekwg63Di3.png) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ABPB0SkcQYF8k47DECUPGbzfLbEDjVD90zOiCdeAu-umu_XRwTOStscRCyopLh551FAGCwzbD022S8hc8FWsvBku7FgTwhTpJeDQmUEixRVBi6dSef4CijPOVsMKeTFj.png) 
            - The behaviour can mirrored exponential: 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JcgqZHZxMtwk-Ardapy8_LMEsdX74xGSjuM9FkysoTB8TfkPA1kWIM35IrrsM5-iMaelPcD67ClsQay_1lJcakQ29tcSy0_FrtJE3KtMlQKED5Z2opxZt93rEHsOPhAG.png)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Q_Ss89p_23iZnZ_OYSNxU_Znri-87fQ8jz45TX40hI0AfG5oVOwzcDrHe9g-35Dyv_wgEeAa3X-RA1pkVKRyseVsXy9oqdlwJZwJm_Gi_rbvPZ01x_OG5SJ9aB8sStIS.png)

        - Kinematics of Robot Manipulators
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/iJhu_KLRu5GNKHN8GftMNd4pQTja728q-2c-98E3ombmhTZcj2VK8UN_MeTQkJKOaP3kygwLUZnqEDnYx67hZO-Xte1zfnSjV3Zxp2IuhTMDBaM9pLsATFP7kYqsec71.png) 
            - Two-Link Arm (Holonomic)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/F656qz1dTreun_GMnNxYGjYUDBEh0rFswJVAdcJaYVCNlamkzug_QoJHMvsEu0GoSpL18iLW6aztqI37BC3G2lpISBIj207GIRnZFjVCpyz3-lbcc9oPrGc4CBJEqkxC.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7sp9wYslLi4mGvO7-SGGNj2S8Z58kAYh3VYJYLO0zqe9ONnFIEL-lehJutshsjBzn-xbYGAmfwgt-SO9f3BO15XaKuSW8rZcCAroXdy_brtqR7YNfcpQVeBwUeqoePJT.png) 
                - We can generalize the forward kinematics with the Jacobian Matrix What is the jacobian matrix?―The relationship between one coordinate system and another: ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_3EGYEgckMqFYU0CnL6kpPx42wYmEr-6P9s474cjfZOZXohWITBDQqPzgJD-3cXwn5qvX-IYDTGr6PClAWuIk6d6rTB7-KbivIxjBS8mPzUbE9g5rBs41XEwKvWZvg9X.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p7CtQbf8fEJNj2cNcJEMnDvZUoqWEo_2zrVuELyl2XbyT-raFwJ4PqMdWQUk82V94aJIjBMVK9uN-uSYIZLCaD0IdrwhKLlxgquprLqBQL7dQdUWv13tToZh-tkQCybY.png)―TODO he said to try out figuring out the Jacobian here 
        - What is this diagram showing?![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/x6XyhcjWhCNoGb7G2GSiLVEYbGJjiZx1Tm1QBeYr00mCAvDcUJbNeCY6b0ngXYIQfWrLAWtnmbyYezy2KAkgwhOGJndGp0JIrSBBjn7Ntgurqwf8W9HRRUgGbVoftFHa.png)―Robots can maintain balance if their center of balance stays within the support polygon of the legs! 
        - 
    - 
- 
- Lecture 5 - 
    - 
    - 
    - Sensors have errors - we can minimize via calibration, take a measurement of known ground truth and fit a model for how the sensor measurements relate to the distance
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/cC1qVR4a7CYocH_npdXvIzrBHaZW8AQrajaLRfLBqwM1YQL561LbsMlj6HCzdASw-VgQ3iBNZ3pGvNG73i83dBx3Fs9F--nK94Eq6NsHq15U8cPGbZp5mG2OFjSYL1YT.png) 
    - Central limit theorem means gaussian!
    - LIDAR - mirror that spins with a laser, tells you how far away things are. 
    - We want to estimate this the probability $p(z_t | x_t)$  where z is our sensor reading and x is the ground truth - however LIDAR can have many error sources.
        - Inherent noise
        - Something unexpected in the way
        - Sensor fails to get a reading
        - Random unexplainable results
    - Start with a gaussian for the **noise**.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/i4-Pfe8Tb9pkxsdQAN1nU6WkoewbufwK9OlVdWmpF80_vme2vJr8sHwZelWuW0MFMNjUFNM3NjzVDk9DbFSzqWkyVqBXoJcFGHyPFyOsHGPg6QXhr3OcLgTKMQOFB0VH.png) 
    - **Unexpected Objects **are measured using an exponential distribution - more likely to be closer than further. Because objects further away will appear smaller - so further away more likely. (Stops after the object stops)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/RaljKzi5scb7P-buSftp0Yy_04zb7hOJbQXrDZKwIyqsNQ3sCAqIiD6zEw3__GUjVr9-dvlxd4eW1zYoVGSlQgJd4uQJwXS6JyrK0bR3aNsckSaTX42eIeWeiBZ9I_Wg.png) 
    - 
    - False **max range detections** are added as uniform:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/r5VsUEXk_fJc2raUg5bLfJlCqPlT-qyQIrPdpJYwsCoxq-9Nhun04ZC3RmSiqNeoyiVwPujyrySZwELPQgMI9d_emyHP9vgBAbgKqfLmiw-qY2HrOoZkgs1XNFb_dV1W.png)
    - **Random failures **are added as uniform:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yil2wonjUZp52GBaUIQ75s6D-3KpE20Zwr1Qf0Ao83hq3smLzXbvDWzuHrOJ8ZCkk2E5SxDMzemQcUlFJejiqKQaCF55P8KZAOUHzFZXzcWtZULOklP4CPWgaWxU467Y.png) 
    - The **Result **is this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/bIqNiuUptkmVXbOtW-zSn6WO0prs5Tim44lzu0bMOpvpQhu-k_hRNgCKMiKc_mXwRRoSsAlGLwBaf4L49Q2PHeJYazNQxKHrUudtMkRYiZCSkGAE_Z8_FM0nF5FRCif8.png) 
We then need to fir this to the data - we'd want to find the variance of the Gaussian and the exponential decay rate (and also maybe the size of objects).
    - Probabilistic Robotics
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6qxM5gxydnSlqq7YFIVF_sbB3ArfBVcL6cKvrQqqWh2hTdPCilGJh-gJASYmY4Wwv3Bj7F7JUMaLeJv69DuZlmk_87241Ms7fh42RHZkd_YZKSrj0F4eF3Frk8qNpVkE.png) 
        - We change to a markov model as we cant solve this:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1s1Ex0nz3LcvyCpiibGv8yst7CdUobQXp39YLkvpSZcaNcmWSsVPvVBeH9SKMcUjWvioM00DTcQFJwVp-v9GVZsLWzMH3Hsa7kr1LFSuouhAZuKR_S_NRD7zeuTZkey8.png)
        - $z_T$ = any controls we've made 
        - $u_t$ = any measurements we've taken since then 
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/JWC6Byzv0PPVcuHmKWG67LOswhrrOqBOLrQryG40mq0nt19h-RtLlteQBa6UVzBjVZ6B_hFD3H6Sq3VlRvXpcXFM3nGUamVrFFZpzHqXApVd-8qnkf4xj4YPUv7IZTWd.png) 
        - Prediction Step:
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xwi4QhGb-er-5_7kI1o1ZeTRMvmPR2NUibbd4PHii0UsdMaF_SVRek7xxNBl48mOs4eOsoMR6O21e4HlfHaH0gYF1LJRHpOabQhRQvquBR0Orr00lyuJH4JAvhmkn2Nf.png) 
This equation means, the probability you're at a given place - is the probability you're at that place given where you were last and the measurements you've taken - multiplied by how certain you were of the last move - integrated over all the possible places you could have been!
        - 
        - Odometry sensor
            - ?? TODO
        - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/u4dU2rYyuwgP_Rdf1cf1lihd1HQMeZlgmvkqfnS2kvUwxy2x_0EK6bB9AXAvHZ2JGyWUtKY387NR_47UUySSLthzkNFXG-eXzF9Ba7KFkhVMN3VOuHJSl7cs_-jQ-8hY.png) 
        - We assume you moved linearly
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/D82L54xui9y_cjd3tgEt9q_wgeqeVXSVlVzYC2RBbiQ_Pza7TEHLb3dfkHSMG7tcVdJvv4G3ll8t8V9Z-urWyBVJOJvgK9C6Q8jH8xW2vJ4bCCW04NR6QFwOnrnOayO6.png) 
            - We break it down into turning, moving in a straight line and then turning again!
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/UBVyn3654f5k12fs7QTHYgb_Ffz7nIoflvJHoaC_v9qvP8RAoDLz0jh2ybAbCB-Vy1B7GNWXcTAf66TXgY-SjsSro8ORin_7h9wFEtGmZA9ENa0fE1aJEVENqD0K-6kM.png)
This is using the x y yaw from the odometer reading. 
            - NOTE: $u_t$ = ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/qiljog_oCssHE66j2tWa8-bAcSlTTypBBXQlU4tEutMaJFursJC3t7yl8OLTKtVt_HJ7ctVOBP7zEanSNcIWO6I8aGm6chYHGona3of-bkwAno872twKBwnfL0OEClBP.png)  (control input)
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/T3Liv9s4RU5Qv-BX4Xi2UHumXvO6rXu0XzaAoNrnXCGoSP1kZ-z-vzm8olZz8SDGs5io-tMleyPiWdw384v_mXjIGDtFlDA5eZl9cBO0EYTGi2yHx0w7z1gH06gE4F1n.png) 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gWqEy38-PwXrsCccEb6nKABLtVSs7Qfn7mVJ6EkmKpNriZOmIDXNdAg7Q7hPZoWVEtLdsrDiZPYV-nsh880KXhnWC9umKbtVb6prvB_2CtScBmIQkOdeD7pZv_ceJUls.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gTqyLlMbLNNv2kmpy2siSBZH6u-OeAUjirTeioYGmtclWPw7WRkBbUbz-49FuUu-XF8NFnBcacp5qumIh6mdhB9HxyjUYVNL-EXsl5zx1nIjJJTiOW3DyKYc3wvFLvH5.png)
Then we work out the components if we really did go from $x_{t-1}$ to $x_t$ 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/82oXcfxjUMwvkREIZw08zZEVFAsxCJbYVl2Ul3iMdN87uJUkqSuQ4DjdVWrTPZbSdBiJVG4x-QXES8sNL9ZEc9XI65WJKlneAts6CtzVliPvYUUUD-vEsrA3Gny2WILL.png) 
            - Assume independence and return final prob:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dGftqaHU-Gn6WEcOLhyK1YXn-ht1XPFdEIYM5xTxwfT2XRBCkVoR23MT_gSaqSj062fiDt8EtnPvcK_eBwNVmAvkxJhbkXmDgSBPu4w7YSwC4onl7-Rm2EZ3K5wZNx3W.png)
        - 
        - Bayes Filter: Correction
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/WxCzbeGsSQdaAlTGEXJr0sCbnwVexAslIwkOJYkTlaRlMq-h7TSNSodUpAolTqO_L0SAyEtfAexImL5dnwXB6b-40i-SFE-fOGZ8x__UGAaKy4ae26sODRTMEersHTYm.png) 
The measurement given the state multiplied by the belief we're in that state! Eta is just a normalisation constant
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/PFYFXyvv82WDDqOWOanyVe01FwCTqJDCQFWQPowp2PfHzC4A09lnSwQhxgcyWtYNDNWpVp5d1_ehb3J0IE0nK9KzHog3dgecHB8keQnkm3tnsO2bGZN--Bn2Uj0kHti3.png) 
            - But we used our sensors in the predict step!
        - 
        - Kalman Filter
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/TnZeewGj8OarwFP82zNzL9VEvFCujs5JYfOyUPmWirDbMRMIctENIPxfnxAWhSxt1roWs6F7NMKtaew2XGIdW3Wr1jvFQs5vXysSdwEeZPh7MhWuRU6wLA9DSfjaqQv3.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nhusfjg2oCo5Vu6xLKRuxbG_n-Xdn_BrCxmPuPC5eWPc6h9SuBCHZfRJ2Hm4-cTfKlfaIju0oOSGftIHq3kQjvjbd6UOtfJWX5psvuBHPHOXqXHE26bOrnok7jA9dvqt.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/FYQH0fx5xReYPxl4laJKDoR2rdQ-eMpO2x1KVDJyG_6mLHX4TMUuOWznF04Lsn0owTegYi9cjgMGTYW0MUiBTTSB2va329BlFh_TT4zPf7UoKfhEBzDvG7QCrqyO6Pm2.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LG0VnuN50IQ11lo5hjr5i1ltZLRfxbVJg7NvU-6k_Tndl2btMeMuJAxgmEQ3E5xpf7EW9rKhARbrTLuYFNtMIX_GFJwEdkEFktazjIy6zZezmqpDelf_xSeH0s5uhB0o.png) 
            - Key! We need to add in noise, meaning we add gaussians - we add noise to the gaussian. The more I walk with my eyes closed, the less certain where I am.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/p56z3WcU3tVT6MmV7wQtcuNVVMj3czx1PrZaskOyQnEgGxNQlOVxCncAOveqiFxlClzZGfgbcs0Q96d7_MY3fwN59BPk0MZNslFoF764tQlUEk4DExVu1J20i_EXyuON.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Xf8ZqN3IOcU_lzqb47e2RiJyBVujntoS7rEJzimTX_U00UCDO7hMNO02Cnhqzm2GN_F9Fu5YoBABjy6tjXustpXrYLtkyV4lLIcIyu0vRWJhNLkspgzPT81WpZS4PBzf.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ryZDEhqyIjwNJb_uAe2X-cCnKK7m21OidfZNgwurh0mOtC_xMiAOXCr-wNoHyIOwkeH9TQjhQJMoJ8m6APKzJkoFYkSV_hhNjUpOV4wyKmcczQM4k3zB2sS-sLRmywRk.png)
Multiply your prior and your measurement and you get another gaussian! We end the cycle and we're ready to go round again! 
            - The real world is non linear! So we would start with a gaussian and end with something else:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gGWDeOJlih15QoYmW9qkVdxt5Qsx3e49p7Z5TC2gEOnRJW_nkwBXhB2qWaIxhJiS9NEMyUQ0IA28FjO0GFOcWCBNYTqgcK6nqpvSbVCYADCm0C9XYdH_R_tEIcL0ZEeQ.png)
So we take a linear best fit:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/raI1qGbRv5qNyE1ArRkmTeOU-BeiwFRXx6iS22H_z67Azx4GLGe5YxvxgrOfBaUcDEsKOSb8eb-idQ1LJvcsj3PpWzhzP4bQ0BCRd2JTnX1o9FjSUKVmX3l6_EhEMkMS.png)

            - We move from gaussians to histograms:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Sgwa5r5gfPooRcS7OnX_xAmeRVcIZoRpbQrU3oyl3-EwmbRjF9gHP8ZX_QQUr0LcSIUjwyeqdOP-tGLfK0D4m4blhGAeKbg0hGODh96P0i59ZkBV_Gg-BxpkoXxBbKbA.png)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mQnv_K_BkQ5rMwxKw8L1P1C57FgYIBk0onnuft-CqgKgcMryjhot71dBzhGBG_IHOrOiSlfMM5VYcxN5GMMo-8zHB72R58HUiHxklFkauyAQIfq_c9-ifBW49E0_pzsj.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/CmrZc1PBr_tB5dns6J-sz1hpcpq3s4s0rTGVYjWWoa7Jjvzmvbz5mdyHdhxCV4GnMj5JzuR_9V5yIDc39UCIcGYgv_I2bYRcqRRDMCOvN_GKGXu42ljpleJhHWT-7Cld.png)
Multiply each bar by each bar and normalise at the end. But is very computationally expensive
        - Particle Filters
            - Single hypothesis of current system state! Each particle has a weight, the probability that the hypothesis is correct.
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/LQj1EQ8DXynmUBykztECa62MwzOAS4hpvSqZXBUvjpdGGrAah80Bme7zdkE9fF1EC2i3pBR6eu0GQy9yFXfPQ4-7bMcoUeBcXcsP_15HeoDfLhu9MAv_CHHLDzMNCEBP.png) 
            - We move them all forward depending on our motion model
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/sQ4P-ETTl0f92jsO2g8u6wu00fhWs26Ofa-I7yyUqVWhjStv6UWrLkzsTk_GLgJtwAyKfjEAnvjBDaVa6ArxgfQUJs1SI8hp3cs3xwvXYTfbR8Tk6PtlUIM_falhkL4o.png) 
Note we add noise to each value! They start to disperse
            - 
            - 
            - 
            - We then go through and apply our sensor model to estimate the probability $p(z_t | x_t$) for each particle. We need this for bayes to get prob of $x_t$! Where z is our sensor reading.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/DBKWC2Lxu2bbNEMFMQHhCfWKgrbhGCzeQt8g0gtuZuBzS0NbDf929Z6-S1QnP655uKp4xN_xZB1DdVfQj82eCm12KHpJSMqTtlXBDriSBlKqS_KICLYCAMPcj5p0t8Q-.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/mEYaX_qpI66m6SkJsF-cWDMtq9BytYp5rkXcQHHNR1zg2PfaYIJkKNS-R0TgfRKb_g2NPXGtlwDjJGPVqIktjkDSN-pmWShEzTq4Fpd0HdENgsahGeaac2OkIthe8zAT.png) 
            - Also if our particle is inside a wall, the probability is zero and we need to kill it.
            - We want something like:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/yDIcEcjHFSpaTu-dCa31ptNpNwhFt4cE-senY1HN-jIamxVVWPBl2QxeR0ceVCZlMTupay0zcBA52X8bD5BIFTufMBINzi-p4pibqMoAtEuI4nGcKP9JRjKbtnAIlJ51.png)
            - Take our particles and draw out a histogram:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/7Z-mZlcZKK07VbOIIFhFu0nQC63IxeGXX_drIl_CA2H5Fge0Lu7DJC3y4TBHe1khV6ong3dew85iliP24hXY7MuQdX4gK4n7SOhdbLBJjuiLDUpx3fN8Iug83BCPVkFt.png) 
            - Then resample based on random uniform guesses between one and zero from this histogram:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/A1Ej6MOj1qP98BRWBwZ-k5IKD73Bp--oyA5CObG9q7UhgV3onGPjzsb4dV0M1pip1wzCPdiNWR-kVZHdaUR74hlbnQa-UVVMlatVY2dlr5xtMRh0-8-9h8anupCSW2-_.png)
Then we clone those ones - we're going to randomly change those anyways. Then give them all uniform probs:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/_ENGoba7P9CzP-b88NIigGhldtOAa8rxSQWuzA38vMWrbgGUGgiRItZoGmOmkVaVpstyGc1O0jP8OxemllAKfv6WbR7syHaJONrylLezSXHlO3XQtQjBWIWe9YMA-0_f.png) 
            - 
            - Easy to break by "kidnapping" the robot - grab it and move it somewhere else.
            - Poor sensor/motion modeling
            - Underestimated errors screw you - you want to overestimate the error.
- Lecture 6
    - Navigation and Path planning
        - Focussing on Motion control and navigation
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/S2_v-CYLk3pW0m5NoxFmFpcKTdTQ3JIPJWBMKQcFzCi61HdW5tm4-dBVPOaEqTX6rrrnwFMMmWRBM_4WJyr3ba06KGsk6HuyGSgB5wz4mHLb5PvO0lqzAeh6eyJd1sIK.png) 
        - Motion Planning
            - Planning is more than simply coming 
            - Need to understand how to execute the motion controls while respecting the robots kinematics **and **the environment - this is a difficult problem. 
            - Search-based algorithms for planning problems can be used.
        - Configuration Space
            - The world has two entities **robots and obstacles**. Considered subsets of the world:![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jpbrouCxmi3mIGFGRvakx0mLyLDsKFBmVn2Lm1WjsNVhPADyJdwN0mhBiEeleOfEwJ7ygd6WzpMTo-LFu_2nzDXCU_eaIkgJoKevyml3UkbpoCjK-Gw3-fkgzw1UJkNI.png) 
            - The space for motion planning is **the set of possible transformations that could be applied to the robot **(considered as a rigid body). 
            - The configuration space C ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c3lBEDysLhtMGauHi2Hkq4GTK74v6_3ZJqUx-X1oy99JDKuMQmDcnZlFSvAwIrEnev-BAQ3dsfr5q1p8sOzFma4z4j6OiqyzaMDWD7DBH1qP2mpqfdK6KNoYAzWjKAaK.png) - allows us to solve the problem for different geography and kinematics.
            - The robot is mapped to a **single point **in C-Space 
            - We can then use anything that deals with points in high-dimensional space to help us solve this problem. I.e. Vector of generalized joint coordinates.
            - A configuration **q **is expressed as a vector of the degrees of Freedom of the robot, store everything that's important. e.g. $x,y,\theta$ for a differential drive robot.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tGF52mFWDHak2mKpjyyJu47iOHPeiZxmAGVb1MVOVGPMoYyiC-BaCHIVRMRfA1GnhsYxBDgWFMc9ylSqQWVD75uzMlqzVPk546uoc1A8hLvbVwAMHFXz_mD2ySNkLdsH.png) 
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Dtlcl0NqSY7Wjr2whzk-JoqUbxiNcFvrkuO_EXu1ThRQ-UvgUA6TcJQx7o81oYUWc_i4GoEx315IooTucbH-38W8PsKC_pWK0yzB3o58tyhrc-XH8VzaBf_OIs_k6lQ2.png)
A(q) are the points occupied by the robot. 
            - The world has an obstacle region - how do we represent an obstacle region in the configuration space? 
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/c7PPLsEeNfgKi2ByUlZR_ks2WRj3eXAKHjLUWlE5oa--mBT-UizKhwjyKqjI9odkBAHjkYKQXHqdCDlQzmbHo1BKZ1gtyJHTPw54A_vXIRSZTHU7QHpI_w91pJwjPxTN.png)
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/U6knR4MwbjG3aHASyvgOA0d9TnscAv0Y30oCEPChN6Vgq2DWYVeLBkgooO-0QQnhRHzzFQfkuhvyS40y8e47yZGXTUQ4lfDZ5OGxHH1jX5FL2tpZ5hGBVF3JJkmA-qvP.png)
We move the robot around the space, and find points where the robot does not collide with any obstacles.  Results in almost dilated objects, within which the robot will collide with the object.
            - Minkowski Sum
                - Formed by taking each vector in a and adding them to each vector in B:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/QMkPmWMHaFYk--74qdrgbhZEeK-xRKfrLRm690kU0lzwRFqWkBwP4fcnyF7Oj-oi4ZTcTWVVOnHcv45UACz2MsDYndUepltrK09vCeta41uULKBedkFUgjxIjA7bH5Jk.png)
Results in this dilation of points the robot **cannot **inhabit! 
                - Using negative A gives the other part.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/laiNUVDJfDt8JKWkNAoNJQBlAVpVa7OwcjKLDG2yiIrh0Gft2elHef-E1O52PD7GxRC_LhtO9JkpuHd6wQ9e3Y5_2vdG0j85J9t2v3bTLCXWA80vBKxisvFGtqmRnhxG.png) 
        - The Path Planning Problem
            - Given a query with an initial configuration and a desired goal configuration:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/pn5nZyXGNMqTiVYl3uznWV0Hb3L2h1639wL99kUI2qRtnzalNfD3nds8g4XiHzIxxVzI6ihu185p8om8_0SB9gMKcvGHbG362RjrYbvURJUMuZdMc59UGZKCpHKRFRXq.png)
We want to compute a path that's parameterised with respect to time and means we reach the final configuration at the end of time:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/nR_CsPYvvZpnSBy9yzvIUnFyNLglpQQu-Eu1O9hQMMXbpBTUY2JYRY08PKToVsgCKT1qTVTQESAezp4QqmvjAqsedfhhrhFt2zYlvt-MxDW1FjWRZXR3TPyFO-Hz3jpH.png)
            - Guarantees
                - Complete: If a solution exists, it finds one or it returns failure.
                - Semi-Complete: If a solution exists, it finds one; otherwise it might run forever
                - Resolution-complete: If a solution exists, it finds one; otherwise it terminates and tells you no solution within a specified resolution exists.
                - Probabilistically complete: If a solution exists, the probability that it will be found tends to 1 as the number of iterations tends to $\infin$. 
            - Combinatorial Methods
                - Requires discretized spaces! Squares in the configuration space.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/llU7hIAYrw8_9lc1QfeQBIt7CDd5xQ64Bh7hY0auTqqlN_lOhBK3uNtQgo84GLJvSU94bZ9jXF1JddbBx0hFDjcNaJzHT0PErUBm7wcD35gWT3wUXsHfqtwN-00kvq-h.png)
                1. Compute the C-Space
                2. Generate a roadmap (graph) in Cfree
Use celldecomposition methods to discretize the state space.
                3. Compute the **minimum-cost path **from initial to goal configuration. (Need a cost function).
                4. Results in a path that travels a distance from time 0 to time 1.
            - A*
                - Remember, admissible heuristics **underestimate **the true cost. 
                - Memory inefficient and grows exponentially with the exponential growth of the dimensionality of the state space.
            - Complexity of Path Planning
                - General motion-planning is PSPACE-hard - uses a polynomial amount of memory. The C-spaces are usually high dimensionality, meaning it's very very hard.
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/H47MKa2DADeno5w_BSCzu-n--2zRMaGRA1scC52_pGes2Gj_ceH0N68vJB9wP6ASQFUzj6iicl1gOBlx4Wz-WEvGWZGFR9zGAxk2A98RONRqzRiEF-fe3JkNxDvlE3ca.png)
                - Attention has thus turned to approximation and randomized algorithms which trade full completeness of the planner for major gains in efficiency - e.g. sampling based methods
            - Sampling-Based Methods
                - Probabilistic Roadmaps - we want to find a better way of generating the search space 
                    1. Initialize an empty graph G - vertices correspond to robot configurations, and edges are collision-free paths
                    2. Sample configurations a(i) in Cfree
                    3. Use a metric to compute a neighbourhood set of a(i) of vertices q already in G
                    4. Local Planner: check if a(i) can be connected to points q in the neighbourhood, if so add the edge (a(i), q) to the edge set if no collision is detected
                    5. Terminate when N edges are added to the roadmap
                - **Connected graphs not guaranteed!**![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/W1max6o8CMqRSK9T4hRfyKT5QRi4aDeRkzh5cVbGx3HxSfiIAhjClZIXGOqQM7R52axrAr2Qw0zQujepogtpNYfGQPj8i3HZwQbHEtACcpjfUlXDmv5ZW23V8OmKhicK.png) 
                - PRM requirements:
Method to sample configurations in free C-Space
Method to check for collisions in C-space
                - Pros:
Probabilistically complete
Apply easily to high-dimensional C-spaces
Fast query processing - search overs state space
                - Cons:
Doesn't work well for narrow passages
Hard to connect vertices for differential motion constraints
Hard to sample uniformly in configuration space.
            - Rapidly Exploring Random Trees (RRTs)
                - Similar to PRMs but for single-query problems (to solve a new planning problem I have to create a whole new tree).
                - Build a tree by generating next states that are achievable
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/eEYI4fE34VUu6Mdw8ZEk-G0FwPb7t3J5KIruGNTBFFfX1VRxnIN_NQQPKGtzFga40LtUe6H7DsFHlhYZeTVIic9nc49z-yJi8zwmTgLqPB67SYT2yiS4aHkPWM3goAoY.png)
Only occasionally do we sample qG, only then do we plan a path to it. 
                - Primitives required
                    - Method to sample configs in c-space
                    - Method for collisions in C-space
                - Pros:
                    - Probabilistically complete
                    - Exponential rate of decay for the probability of failure
                    - Asymptotically optimal (RRT*)
                - Cons:
                    - For non-holonomic robots, generating edges to sampled configs requires solutions to the two-point value problem.
                - **You could only sample values that are feasible for your robot to reach from any current edges.** :
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/1qtvhlJfSs3V5P6QZlUfg74UkHJgZjeI-LBw_zn1-AHi3a0_3Y4oURSREVNWV07-DWfTfGZ0aJkMk8qbDG87xW08t6S6oS7DZuf13vGrqHWvL1aVo80IvGwK8zI-13oD.png)
            - Potential Field Method
                - No explicit roadmap - instead construct a real-values potential function:
![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0gpKNewmSQhY87cD5OxLmtDVvT-U2tbnGGyncIk2gNQcKesLXKi92mOQr3OmT-6M7Oz-L3PE3x8v78fR4z82KWUnix6ONU6oVFe-seRyGVLT8Qu0jK_LC3rC8QJFRCh9.png)
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wr-NgfgMIUaUtheKQqbEtuFr1M9sXwq1RBMSWshtKQlOJOoakX6Te5MVFEKVIe3pndRJy9C28glXcWGYdy2WTatS43MGF02ZxUmdKnXXpiFrcS6RJJyUgk2EABMj4HqG.png) 
                - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/lLTSuzVUyTQ595nZIPlWcjNQT9_nX-NTucrVNJkt2nk32qTOaBMrTLK7ZohIMNCk7IbsNdzFPTTSIs8olvGVClFvVoQROxZ_iMxuJDNcoedt34ywm1WJczQFk-TR6MrW.png)
Derivative with respect to the different controls! 
                - Creating a potential field in C-Space is **difficult! **One strategy is to create a potential field in the robots work space instead of the C-space.  
                    - Then compute gradient
                    - Use feedback linearization to get control inputs
                    - Compute gradients in C-space from control inputs
                    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KhGE6hT2PdyKcVtQJ6vV1cAdNHkld2wHiQJ9Txc_lpHAMO9evniGhimzLGN2-Sxxk8ojG-3bulzn4fl_c8KV0cBqXRWa0Mr2O91-bWPcT2MVM86wEoYuf5pq-fJeLSM8.png) 
                - Feedback Linearization
                    - Imagine a carriage being pulled along by horses that can move in any direction
            - Requirements
                - Representation of work space
            - Pros
                - Computationally efficient once we have the C-space
                - More than one path
            - Cons
                - local minima require methods to resolve them
                - Representation of C-space in high dimensions
            - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jsmx_ETwIR4aaAQEXS7eRwios7jAimmPxwzoptEhUlBTxvMuUMdLcjItyenWPwzKt1jls2HvPpGz54S8GVGPrC4F4hf6t_B6xuh4u5kl-rDjazpeDq-6LFtB0x5URA2s.png) 
    - Multi-Robot Navigation and Path Planning
        - Focus on multiple robots, connected via some form of communication.
        - Multi-Robot Systems
            - Robot swarms/robot teams/ robot networks
            - Needed for distributed problems, Also adds robustness and resilience through redundancy - additionally the whole is more than the sum of parts.
            - **Coordination **- linear gains from increase in number of robots 
            - **Cooperation **- Robots take small hit to solve overall problem. Non-linear, threshold which can improve system. Need a certain number of agents working together before the benefit is seen 
            - **Collaboration **- When robots need each other, other robots have complementary skills that we can leverage. 
        - Taxonomy
            - Architectures can be centralized or decentralized. 
            - Implicit vs explicit communication - can observe the robots position implicitely, but it's battery needs to be communicated explicitly.
            - Disk models are used to represent communication range - very crude approximation.
        - Communication Topologies
            - Start topology, fully connected or random meshes.
            - 
        - 
        - MISSING A BIG BIT
        - 
        - Decentralization
            - Want similar performance as centralized control. As information percolates they converge to the same values.
            - Advantges
                - No single point of failure
                - Any-comm algorithms which gracefully degrade under poor comms
                - Any-time algorithms which continuously improve the solution
            - Challenges:
                - Communication delays and overhead
                - Input: Asynchronour with rumor propagation
                - Sub optimality with respect to the centralized solution.
        - Collective Movement
            - Properties: No collisions, without an apparent leader; tolerant to loss or gain of group members. Coalescing an dplitting and reactive to obstacles.
            - Benefit from energy saving and better navigation accuracy
        - Flocking with Boids
            - A boid reacts only to its neighbours
            - Neighborhood define d by distance and angle (region of influence)
            - 3 steering rules - separation (stay away from neighbors or will collide), cohesion (want to stay in a group don't go too far), alignment (stay in the same direction as neighbors)
            - Boid wide field of view, no delays, no noise in measurements.
            - Behaviour-based with priorities
                - Low priority acceleration requests towards a point or in a direction to direct the flock
                - Highest priority to obstacle avoidance, steer to avoid!
        - The consensus Algorithm
            - Reach decentralized agreement purely based on local interactions.
            - Based on graph topological definition of multi robot systems useful for motion coordinate and synchronization.
            - 
            - Discrete:
                - Iterate over neighbors and get their values. Take the measurement and sum them, average them to find x at time t+1.
                - All robots eventually converge to average of initial values. Convergence rate is exponential.
        - Formation Control
            - Formations are **specific **geometric configuration as opposed to flocks - some applications require moving in certain formations/groups (think trucks in formation on the road).
            - Need to know something about yourself **and **other robots. Challenges with noise, anonymous robots and non-holonomicity
            - 
- Lecture 7
- 
- 
- Project Notes
    - Part 0
        - Useful Commands
            - ros2 topic pub -r 1 /my topic std msgs/String ’data: hello’
            - ros2 topic echo /my topic.
            - ros2 topic type /my topic.
        - 
        - Exercise 4
            - ROS 2 is middleware, anonymous publish/subscribe for different ROS2 processes to talk to each other. ROS graph contains the different nodes and the connections between them all.
            - Nodes, Messages, Topics and Discovery:
                - Nodes are items which send ROS2 messages
                - Data type used when publishing to/reciving from topic
                - Topics...
                - Discovery: Process for nodes determining how to talk to each other
            - Client Libraries
                - ROS client libraries allow ROS clients written in different languages to communicate - ATM Python and C++ centrally supported. 
            - Discovery: 
                1. Nodes announce their presence to ROS nodes on the same ROS domain - settable with the ROS_DOMAIN_ID environment variable. Then appropriate connections are made
                2. Periodically, nodes announce themselves so connections can be made to newcomers.
                3. Nodes announce when they're going offline.
            - Nodes will only connect  __if they have compatible QOS __  
        - Exercise 5
            - Initially - ros2 not working. Working on fixing this by checking if ros. ⇒ Fixed this by creating a command to set up the sources. Don't forget to run ". ./start.sh" to load the aliases into the current working script.
            - b.) Daemon is down - this daemon sits around and records nodes arriving and leaving the network. Useful if a node has a short lifespan and doesn't want to spend ages discovering neighbours.
            - c.) Empty
            - d.) parameter_events and rosout
        - Exercise 6
            - a.) Publishes hello to my topic continuously -r 1 sets the message to be published at 1 Hz.
            - b.) Listens for the topic and prints hello
            - c.) Tells you the datatype of the topic - tells you how to handle the data
        - Exercise 7
            - a.) Makes a publisher producing a twist message by .1 in x linearly and the angular .2 in z every .2 seconds. 5 is the QOS history
            - c.) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/jgUqxBg5k_qbRgGn75YwXY_n7kyIT2rFz2OUetOz9nlZNKc-Zhi4foHBbEqRoG44qdTEwpKsCun1GJXQivIW5RQKHeSsxgpwsUnhCPLbdTiNgsDLlPTH-2XPHTtmlKbR.png) Produces this. 
            - d.) had to change to robot0/cmd_vel then it worked 
    - Part 1
        - Euler's Method
            - Basically step along the tangent of the curve repeatedly.
            - $$y_{n+1} = y_n + hf(t_n, y_n)$$ 

                - Where h is the step size
                - n is how many steps in the iteration you are
                - t is the time (When your differential equation needs it)
                - f is the differential of the function you're attempting to approximate
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
