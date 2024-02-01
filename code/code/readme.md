software requirements:
----------------------
python version: 3.10.8
sumo version: 1.14.1
Tensorflow
keras

Training:
---------
training the reinforcement agent: python training.py 
the results stored to models folder.

Testing:
--------
testing the reinforcement agent: python testing.py


files explanation:
------------------
Within the file model.py, there are two distinct classes that define the deep neural network. These classes encapsulate all the relevant details of the network, including the necessary functions to train and predict outputs. Specifically, there is a class for training the network and a separate class for testing it.

In the program, there is a class called Memory which manages the storage and retrieval of data for the experience replay mechanism. One of the functions within this class adds a new sample to the memory, while another function retrieves a batch of samples from the memory.

The Simulation class is responsible for managing the simulation process, including the execution of individual episodes. The run function, in particular, allows the simulation of a single episode. Additionally, other functions are used during the run function to interact with the SUMO simulation environment. For example, the get_state function retrieves the current state of the environment, the _set_green_phase function sets the next green light phase, and the _replay function preprocesses data for use in training the neural network. It should be noted that there are two files containing slightly different versions of the Simulation class.

class: simulation_training.py and simulation_testing.py. Which one is loaded depends if we are doing the training phase or the testing phase.

The TrafficGenerator class contains the function dedicated to defining every vehicle's route in one episode. The file created is episode_routes.rou.xml, which is placed in the "intersection" folder.

The Visualization class is just used for plotting data.

The utils.py file contains some directory-related functions, such as automatically handling the creations of new model versions and the loading of existing models for testing.

training_settings.ini file contains input parameters for training.

testing_settings.int file contains input parameteres for testing.

input parameters for training:
--------------------------------
gui: enable or disable the SUMO interface during the simulation.
total_episodes: the number of episodes that are going to be run.
max_steps: the duration of each episode, with 1 step = 1 second.
n_cars_generated: the number of cars that are generated during a single episode.
green_duration: the duration in seconds of each green phase.
yellow_duration: the duration in seconds of each yellow phase.
num_layers: the number of hidden layers in the neural network.
width_layers: the number of neurons per layer in the neural network.
batch_size: the number of samples retrieved from the memory for each training iteration.
training_epochs: the number of training iterations executed at the end of each episode.
learning_rate: the learning rate defined for the neural network.
memory_size_min: the min number of samples needed into the memory to enable the neural network training.
memory_size_max: the max number of samples that the memory can contain.
num_states: the size of the state of the env from the agent perspective.
num_actions: the number of possible actions.
gamma: the gamma parameter of the Bellman equation.
models_path_name: the name of the folder that will contain the model versions and so the results. Useful to change when you want to group up some models specifying a recognizable name.
sumocfg_file_name: the name of the .sumocfg file inside the intersection folder.

input paramets for testing:
--------------------------
gui: enable or disable the SUMO interface during the simulation.
max_steps: the duration of the episode, with 1 step = 1 second.
n_cars_generated: the number of cars generated during the test episode.
episode_seed: the random seed used for car generation.
green_duration: the duration in seconds of each green phase.
yellow_duration: the duration in seconds of each yellow phase.
num_states: the size of the state of the env from the agent perspective.
num_actions: the number of possible actions.
models_path_name: The name of the folder where to search for the specified model version to load.
sumocfg_file_name: the name of the .sumocfg file inside the intersection folder.
model_to_test: the version of the model to load for the test.





