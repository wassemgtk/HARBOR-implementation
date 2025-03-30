# HARBOR Prototype

This is a simplified prototype implementation of the **HARBOR** framework (Housing Auction for Reasoning, Bidding, and Opponent Recognition) from the paper *"Harbor: Exploring Persona Dynamics in Multi-Agent Competition"* by Jiang et al. It simulates a multi-agent housing auction where agents with distinct personas compete to maximize profit, using the `meta-llama/Llama-3.2-3B-Instruct` model from Hugging Face for decision-making.

## Features
- Multi-agent auction simulation with a Master Agent and two Rival Agents.
- Persona-driven bidding (e.g., Urban Dweller, Eco-Conscious).
- Priority planning for items based on persona and profit goals.
- Basic competitor persona profiling.
- Strategic bidding decisions (bid or quit) using predefined options.
- Tracks budget, profit, and won items for each agent.

## Prerequisites
- Python 3.8+
- Hugging Face account and access token (for gated model access)
- GPU recommended (CPU works but is slower)

### Dependencies
Install the required libraries:
```bash
pip install transformers torch
```

## Setup
1. **Authenticate with Hugging Face**:
   - Log in to Hugging Face and generate an access token.
   - Authenticate via CLI:
     ```bash
     huggingface-cli login
     ```
   - Ensure you have access to `meta-llama/Llama-3.2-3B-Instruct`.

2. **Clone or Download**:
   - Save the script as `harbor_prototype.py` in your working directory.

## Usage
Run the auction simulation:
```bash
python harbor_prototype.py
```

### Example Output
```
Auctioning House A (Starting Price: $100)
Master bids $110
Rival 1 bids $120
Rival 2 quits
Master quits
Rival 1 wins House A for $120

[...]

Final Results:
Master: Budget: $1000, Profit: $0, Won: []
Rival 1: Budget: $880, Profit: $180, Won: ['House A']
Rival 2: Budget: $1000, Profit: $0, Won: []
```

## Project Structure
- **`harbor_prototype.py`**: Main script containing the auction simulation, agent logic, and LLM integration.
  - **Agent Class**: Handles persona, priority, profiling, and bidding.
  - **Auction Logic**: Simulates ascending-bid auctions for three houses.
  - **LLM Integration**: Uses Llama-3.2-3B-Instruct for decision-making.

## Limitations
- Simplified from the original paper: no second-order ToM, limited metrics (e.g., Profit Ratio, TrueSkill).
- Basic JSON parsing; LLM responses may require tuning for reliability.
- Small scale: 3 agents and 3 houses (expandable).

## Extending the Prototype
- Add more houses/agents for larger auctions.
- Implement full metrics (e.g., KL divergence for profiling accuracy).
- Enhance prompts for better LLM performance.
- Include second-order Theory of Mind (ToM) as per the paper.

## Acknowledgments
Based on *"Harbor: Exploring Persona Dynamics in Multi-Agent Competition"* by Kenan Jiang, Li Xiong, and Fei Liu (Emory University).

