# robot_master
- description: this package gives controller for robot all motion.
- system configuration:
![Alt text](%E3%83%AD%E3%83%9C%E3%83%83%E3%83%88%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E6%A7%8B%E6%88%90%E5%9B%B3.drawio.png)

- functions:
    - chassis (namespace):
        - input: 
            - `/odometer_3wheel` (topic):
                - description: this topic gives the odometry counts of the odometers.
                - type: `nucleo_agent/msg/OdometerData.msg`
            - `/path_and_feedback` (action):
                - description: this action gives the path and feedback for the robot.
                - type: `robot_master/action/PathAndFeedback.action`
        - output:
            - `/input_vel` (topic):
                - description: this topic gives the velocity for each wheel.
                - type: `std_msgs/msg/Float64MultiArray.msg`
        
    - mechanism (namespace):
        - input: 
            - `/input_vel` (topic):
                - description: this topic gives the velocity for each wheel.
                - type: `std_msgs/msg/Float64MultiArray.msg`
        - output:
            - `/switchs_states` (topic):
                - description: this topic gives the switch states.
                - type: `nucleo_agent/msg/SwitchsStates.msg`
    - robot_master_node (node):
        - input:
            - `robot_movements.yaml` (parameter):
                - description: this parameter gives the robot movements which include the path (including angle data) and specific points on the path and mechanism command on the specific points.
                - type: `yaml`
            - `/switchs_states` (topic):
                - description: this topic gives the switch states.
                - type: `nucleo_agent/msg/SwitchsStates.msg`
            - feedback of `/path_and_feedback` (action):
                - description: this action gives the path and feedback for the robot.
                - type: `robot_master/action/PathAndFeedback.action`
        - output:
            - `/path_and_feedback` (action):
                - description: this action gives the path and feedback for the robot.
                - type: `robot_master/action/PathAndFeedback.action`
            - 

## msgs, srvs, actions
### relate to chassis
- OdometerData.msg
    - description: this message gives the odometry counts of the odometers.
    - fields:
```
# 計測輪の角変位のデータ [rad]

std_msgs/Header header
float64[3] rotation # 各計測輪の角変位
float64[3] angular_vel # 各計測輪の角速度
```

- PathAndFeedback.action
    - description: This action gives the path (including angle data) and feedback (that robot passes specific points on the path) for the robot.
    - fields:
```
# パスとフィードバックのデータ

it is not defined yet.
```

### relate to mechanism
- SwitchsStates.msg
    - description: this message gives the switch states.
    - fields:

```
# スイッチの状態のデータ

std_msgs/Header header
bool[] switchs # 各スイッチの状態
```

    - assignment:
        - switchs[0]: switch for the mechanism
        - switchs[1]: switch for the mechanism
        - switchs[2]: switch for the mechanism
        - switchs[3]: switch for the mechanism
        - switchs[4]: switch for the mechanism
        - switchs[5]: switch for the mechanism
        - switchs[6]: switch for the mechanism
        - switchs[7]: switch for the mechanism
        - switchs[8]: switch for the mechanism
        - switchs[9]: switch for the mechanism
        - switchs[10]: switch for the mechanism
        - switchs[11]: switch for the mechanism
        - switchs[12]: switch for the mechanism
        - switchs[13]: switch for the mechanism
        - switchs[14]: switch for the mechanism
        - switchs[15]: switch for the mechanism