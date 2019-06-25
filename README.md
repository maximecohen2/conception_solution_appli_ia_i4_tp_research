# Research

Rapport sur les essais.

https://github.com/Microsoft/malmo/blob/master/scripts/python-wheel/README.md

Lancer cette commande pour travailler:

```bash
docker-compose up -d --build
```

Commenter le code.

https://github.com/crowdAI/marLo

https://github.com/Microsoft/malmo

Marlo ReadtheDoc

https://marlo.readthedocs.io/en/latest/usage/singleagent_example.html

---

Apprentissage par renforcement

+ https://skymind.ai/wiki/deep-reinforcement-learning
+ => Q-Learning est l'approche la plus utilisée
+ Choix techniques ouverts


+ Présentation orale 26 Juin / 30min

---

Diego Perez-Liebana, Katja Hofmann, Sharada Prasanna Mohanty, Noburu Kuno, Andre Kramer, Sam Devlin, Raluca D. Gaina “The Multi-Agent Reinforcement Learning in MalmÖ (MARLÖ) Competition”, 2019, Challenges in Machine Learning (NIPS Workshop), 2018; <http://arxiv.org/abs/1901.08129>.

---

+ Agent: An agent takes actions; for example, a drone making a delivery, or Super Mario navigating a video game. The algorithm is the agent. In life, the agent is you.1
+ Action (A): A is the set of all possible moves the agent can make. An action is almost self-explanatory, but it should be noted that agents choose among a list of possible actions. In video games, the list might include running right or left, jumping high or low, crouching or standing still. In the stock markets, the list might include buying, selling or holding any one of an array of securities and their derivatives. When handling aerial drones, alternatives would include many different velocities and accelerations in 3D space.
+ Discount factor: The discount factor is multiplied by future rewards as discovered by the agent in order to dampen thse rewards’ effect on the agent’s choice of action. Why? It is designed to make future rewards worth less than immediate rewards; i.e. it enforces a kind of short-term hedonism in the agent. Often expressed with the lower-case Greek letter gamma: γ. If γ is .8, and there’s a reward of 10 points after 3 time steps, the present value of that reward is 0.8³ x 10. A discount factor of 1 would make future rewards worth just as much as immediate rewards. We’re fighting against delayed gratification here.
+ Environment: The world through which the agent moves. The environment takes the agent’s current state and action as input, and returns as output the agent’s reward and its next state. If you are the agent, the environment could be the laws of physics and the rules of society that process your actions and determine the consequences of them.
+ State (S): A state is a concrete and immediate situation in which the agent finds itself; i.e. a specific place and moment, an instantaneous configuration that puts the agent in relation to other significant things such as tools, obstacles, enemies or prizes. It can the current situation returned by the environment, or any future situation. Were you ever in the wrong place at the wrong time? That’s a state.
+ Reward (R): A reward is the feedback by which we measure the success or failure of an agent’s actions. For example, in a video game, when Mario touches a coin, he wins points. From any given state, an agent sends output in the form of actions to the environment, and the environment returns the agent’s new state (which resulted from acting on the previous state) as well as rewards, if there are any. Rewards can be immediate or delayed. They effectively evaluate the agent’s action.
+ Policy (π): The policy is the strategy that the agent employs to determine the next action based on the current state. It maps states to actions, the actions that promise the highest reward.
+ Value (V): The expected long-term return with discount, as opposed to the short-term reward R. Vπ(s) is defined as the expected long-term return of the current state under policy π. We discount rewards, or lower their estimated value, the further into the future they occur. See discount factor. And remember Keynes: “In the long run, we are all dead.” That’s why you discount future rewards.
+ Q-value or action-value (Q): Q-value is similar to Value, except that it takes an extra parameter, the current action a. Qπ(s, a) refers to the long-term return of the current state s, taking action a under policy π. Q maps state-action pairs to rewards. Note the difference between Q and policy.
+ Trajectory: A sequence of states and actions that influence those states. From the Latin “to throw across.” The life of an agent is but a ball tossed high and arching through space-time.

### Exemple Code Malmo

```python
#!/usr/bin/env python
# $MALMO_MINECRAFT_ROOT/launchClient.sh -port 10000

import marlo
client_pool = [('127.0.0.1', 10000)]
join_tokens = marlo.make('MarLo-FindTheGoal-v0',
                          params={
                            "client_pool": client_pool
                          })
# As this is a single agent scenario,
# there will just be a single token
assert len(join_tokens) == 1
join_token = join_tokens[0]

env = marlo.init(join_token)

observation = env.reset()

done = False
while not done:
  _action = env.action_space.sample()
  obs, reward, done, info = env.step(_action)
  print("reward:", reward)
  print("done:", done)
  print("info", info)
env.close()
```

https://github.com/zenoengine/QLearning-Minecraft-Malmo

https://github.com/ilovecocolade/Reinforcement-Learning-algorithms-Q-MC-for-MARLO-Minecraft-
