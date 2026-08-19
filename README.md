# Robot_learning_model_implentation
Here you can find the model I implemented during the Robot_Learning hackathon hosted by Dream Machines.

The task given to the robot was to pick up a small pink cube and place it gently in a black box without touching its boaders. 

The robot , an SO100 Hand Robot, was trained on 100 episodes of the given task. You can find the data set here: https://huggingface.co/datasets/DouaaKDR/small_cube_merged

the command to train on your local machine is : 
lerobot-train --dataset.repo_id=DouaaKDR/small_cube_merged --policy.type=act --policy.push_to_hub=false --output_dir=outputs/train/small_cube_test --job_name=small_cube_test --policy.device=cuda --batch_size=16 --steps=30000  --save_freq=500               

if you want to run it on your local machine, the command is: 

lerobot-rollout --strategy.type=base --policy.path=C:\robot_learning\lerobot\outputs\train\small_cube_test\checkpoints\last\pretrained_model --robot.type=so101_follower --robot.port=* --robot.id=my_follower_arm --robot.cameras="{ front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 30} }" --task=" pick the small pink cube and place it after the hexagon in the bin without touching its boarders, task is complete." --duration=120   

* = here you put the port that is linked to your follower arm

PS : some of the code used here was git cloned from the LeRobot library at https://github.com/huggingface/lerobot.git
