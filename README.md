# LLM Agent Patterns: ReAct + ToT + Reflect

This project implements three advanced AI agent patterns for enhanced reasoning and problem-solving:

- **ReAct (Reasoning + Acting)**: Iterative reasoning with action execution
- **ToT (Tree of Thoughts)**: Multi-branch reasoning for complex problems  
- **Reflect**: Self-correcting answers through critical reflection

## 🚀 Quick Start

### Prerequisites
- Python 3.7+
- OpenAI API key

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd "ReAct + ToT + Reflect"
```

2. Install dependencies for each agent:
```bash
# ReAct Agent
cd ReAct
pip install -r requirements.txt

# ToT Agent  
cd ../ToT
pip install -r requirements.txt

# Reflect Agent
cd ../Reflect
pip install -r requirements.txt
```

3. Set up your OpenAI API key:
```bash
# Create .env file in each agent directory
echo "OPENAI_API_KEY=your_api_key_here" > .env
```

## 🤖 Agent Patterns

### ReAct Agent
**Location**: `ReAct/`

The ReAct agent combines reasoning and acting in an iterative loop:
- **Think**: Analyze the question and determine next action
- **Act**: Execute the determined action (search or answer)
- **Observe**: Process results and update context

**Usage**:
```bash
cd ReAct
python main.py
```

**Features**:
- Web search integration for real-time information
- Iterative reasoning with context building
- Configurable maximum iterations
- Interactive command-line interface

### ToT (Tree of Thoughts) Agent
**Location**: `ToT/`

The ToT agent explores multiple reasoning paths simultaneously:
- Generates multiple thought branches at each step
- Evaluates each path for correctness
- Prunes unsuccessful branches
- Finds optimal solutions through tree search

**Usage**:
```bash
cd ToT
python main.py
```

**Features**:
- Solves the 24-game mathematical puzzle
- Multi-branch reasoning with depth control
- Expression evaluation and validation
- Solution tracking and reporting

### Reflect Agent
**Location**: `Reflect/`

The Reflect agent improves answers through self-criticism:
- **Answer**: Generate initial response
- **Reflect**: Critically evaluate answer quality
- **Correct**: Generate improved answer based on feedback
- **Repeat**: Iterate until satisfactory

**Usage**:
```bash
cd Reflect
python main.py
```

**Features**:
- Self-correcting answer generation
- Critical reflection on answer quality
- Iterative improvement with feedback loops
- Configurable reflection rounds

## 📁 Project Structure

```
ReAct + ToT + Reflect/
├── README.md
├── ReAct/
│   ├── main.py              # ReAct agent implementation
│   ├── openai_server.py     # OpenAI API client
│   ├── search.py           # Web search functionality
│   └── requirements.txt    # Dependencies
├── ToT/
│   ├── main.py             # ToT agent implementation
│   └── requirements.txt    # Dependencies
└── Reflect/
    ├── main.py             # Reflect agent implementation
    └── requirements.txt    # Dependencies
```

## 🔧 Configuration

### Environment Variables
Each agent requires an OpenAI API key. Create a `.env` file in each agent directory:

```env
OPENAI_API_KEY=your_openai_api_key_here
```

### Model Configuration
All agents use GPT-3.5-turbo by default. You can modify the model in each `main.py` file:

```python
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",  # Change this to gpt-4 or other models
    messages=messages,
    temperature=0.7
)
```

## 💡 Usage Examples

### ReAct Agent Example
```
Enter your question: What is the current weather in New York?
Thinking...
Thought: SEARCH: current weather New York
Action: search
Observation: Search results: Current weather in New York...
Final Answer: The current weather in New York is...
```

### ToT Agent Example
```
Solving 24 game with numbers: [2, 4, 6, 8]
Depth 0: Generated 3 thoughts
  Expression: 2+4 = 6
  Expression: 2*4 = 8
  Expression: 2-4 = -2
Found 1 solution(s):
1. (2+4)*(8-6) = 24
```

### Reflect Agent Example
```
Question: What is the capital of France?
Generating initial answer...
Initial Answer: The capital of France is Paris.

Reflection Round 1:
Reflecting on answer...
Reflection: CORRECT
Final Answer: The capital of France is Paris.
```

## 🛠️ API Reference

### ReActAgent Class
- `think(question)`: Analyze question and determine action
- `act(thought)`: Execute determined action
- `observe(action_type, result)`: Process action results
- `run(question, max_iterations=3)`: Main ReAct loop

### ToTAgent Class
- `generate_thoughts(node)`: Generate multiple reasoning branches
- `create_child_nodes(parent, thoughts)`: Create child nodes from thoughts
- `search_tree(numbers)`: Search for solutions using tree traversal
- `solve_24_game(numbers)`: Main method to solve 24-game

### ReflectAgent Class
- `generate_initial_answer(question)`: Generate first answer
- `reflect_on_answer(question, answer)`: Evaluate answer quality
- `generate_corrected_answer(question, original, reflection)`: Create improved answer
- `run(question)`: Main Reflect loop

## 🔍 Key Features

### ReAct Agent
- **Web Search Integration**: Real-time information gathering
- **Iterative Reasoning**: Builds context through multiple iterations
- **Action Selection**: Intelligently chooses between search and answer
- **Context Management**: Maintains conversation history

### ToT Agent
- **Multi-Branch Reasoning**: Explores multiple solution paths
- **Tree Search**: Systematic exploration with pruning
- **Mathematical Validation**: Safe expression evaluation
- **Solution Tracking**: Finds and reports multiple solutions

### Reflect Agent
- **Self-Correction**: Improves answers through reflection
- **Quality Assessment**: Critical evaluation of answer completeness
- **Iterative Improvement**: Multiple rounds of refinement
- **Feedback Integration**: Uses reflection to guide corrections

## 🚨 Error Handling

All agents include basic error handling for:
- OpenAI API failures
- Network connectivity issues
- Invalid input formats
- Maximum iteration limits

## 📝 Dependencies

### ReAct Agent
- `openai==0.28.1`
- `requests==2.31.0`
- `python-dotenv==1.0.0`

### ToT Agent
- `openai==0.28.1`
- `python-dotenv==1.0.0`

### Reflect Agent
- `openai==0.28.1`
- `python-dotenv==1.0.0`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- OpenAI for providing the GPT models
- The research papers that inspired these agent patterns:
  - ReAct: "ReAct: Synergizing Reasoning and Acting in Language Models"
  - ToT: "Tree of Thoughts: Deliberate Problem Solving with Large Language Models"
  - Reflect: "Reflexion: Language Agents with Verbal Reinforcement Learning"
