Agentic AI with a MCP Server for human-activity-recognition video analysis


https://www.kaggle.com/code/rokoyim/human-activity-recognition




Agentic AI Video Classification MCP Server
Combines video processing with multi-step AI reasoning for intelligent video analysis



                "sports", "nature", "urban", "indoor_activity",
                "presentation", "tutorial", "vlog", "news",
                "entertainment", "education", "documentary"




Speed, accuracy, 

Video Classification Agent - Setup & Usage Guide
Overview
This is a complete Agentic AI system that combines:
* Multi-step reasoning (agent plans and executes)
*  Video processing (frame extraction and analysis)
*  Computer vision (object detection, scene classification)
*  Memory system (learns from past analyses)
*  MCP integration (works with Claude)

Installation
Step 1: Install Dependencies


bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install packages
pip install fastmcp opencv-python numpy

# Optional: For OCR support
pip install pytesseract
Step 2: Project Structure


video-classification-agent/
├── server.py              # Main MCP server (code above)
├── requirements.txt       # Dependencies
├── test_videos/          # Sample videos
│   ├── sports.mp4
│   ├── nature.mp4
│   └── tutorial.mp4
└── README.md
Step 3: requirements.txt


fastmcp>=0.1.0
opencv-python>=4.8.0
numpy>=1.24.0
pytesseract>=0.3.10

Configuration
Claude Desktop Config
Add to ~/Library/Application Support/Claude/claude_desktop_config.json:


json
{
  "mcpServers": {
    "video-agent": {
      "command": "python",
      "args": ["/path/to/server.py"]
    }
  }
}
Restart Claude Desktop after configuration.

How It Works
Agentic Workflow


1. USER REQUEST
   "Classify this video"
          ↓
2. AGENT PLANNING
   Agent creates multi-step plan
          ↓
3. FRAME EXTRACTION
   Extract key frames (scene changes)
          ↓
4. FRAME ANALYSIS
   Detect objects, scenes, activities
          ↓
5. CLASSIFICATION
   Aggregate evidence, classify category
          ↓
6. INSIGHTS GENERATION
   Human-readable summary
          ↓
7. MEMORY UPDATE
   Store for future reference
Agent Reasoning
The agent uses ReAct pattern (Reasoning + Acting):


python
# Agent thinks: "What do I need to do?"
plan = agent_plan_analysis(video_path)

# Agent reasons about each step:
# "First, I need frames to understand content..."
# "Then, I need to detect what's in those frames..."
# "Finally, I can classify based on evidence..."

# Agent executes:
results = agent_execute_plan(plan)

# Agent learns:
# Stores results in memory for future comparisons

Usage Examples
Example 1: Basic Video Classification


User: "Analyze video.mp4 and tell me what category it is"

Claude: Let me analyze this video step by step.

[Agent creates plan]
[Extracts 8 key frames using scene detection]
[Analyzes each frame for objects and scenes]
[Classifies based on evidence]

Result:
📊 Video Classification Report
━━━━━━━━━━━━━━━━━━━━━━━━━━━

Primary Category: Sports
Confidence: 82.5%

Key Findings:
- Detected 12 people across analyzed frames
- Dominant scene type: outdoor/natural lighting
- Activity pattern: dynamic/motion detected
- High scene variety (5 different scenes)

Summary: This video is classified as 'sports' with 82.5% confidence. 
The classification is highly confident. Multiple people and dynamic 
movement patterns strongly indicate sporting activity.
Example 2: Agentic Analysis with Reasoning


User: "I have a video at /path/to/nature_doc.mp4. Can you figure out 
       what it's about and explain your reasoning?"
