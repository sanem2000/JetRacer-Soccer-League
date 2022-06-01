# Multi Agent Soccer

![alt text](https://github.com/sanem2000/JetRacer-Soccer-League/blob/main/Videos/Pictures/Unity_implementation.png)

This section contains our attempt to train soccer agents(striker and keeper) to coordinatively play soccer in Unity's Soccer Twos Environment using Deep Reinforcement Learning. 

## Reward Structure:

    1. Keeper:
        • -1 when the ball enters the team’s goal
        • +0.1 when the ball enters the opponent’s goal
        • +0.001 existential bonus (to make sure the keeper prolongs the episode as the ball should not enter the team’s goal)
        • -0.03 when the ball is not in view

    2. Striker:
        • +1 when the ball enters the opponent’s goal
        • -0.1 when the ball enters own team’s goal
        • -0.001 existential penalty (to ensure the striker does not cheat and stays still. This ensures that the agent accumulates a penalty as time increases and looks to end the episode soon by hitting it into the opponent’s goal.)
        • -0.03 when the ball is not in view
        • +0.3 when striker kicks the ball

## Implementation:

Please check out **multi_agent_soccer.ipynb** for our implementation

## References:

1. https://github.com/Unity-Technologies/ml-agents
2. https://github.com/ppipat/Multi-Agent-Soccer
