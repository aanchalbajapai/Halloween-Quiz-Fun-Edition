# Halloween Quiz — Fun Edition

## Project Description
An interactive web-based Halloween quiz application built with Gradio and powered by OpenAI's GPT API. The app dynamically generates spooky-themed questions across various Halloween categories, featuring an engaging UI with lifelines, progress tracking, and immediate feedback. Perfect for Halloween enthusiasts looking to test their knowledge of horror movies, monsters, folklore, and Halloween traditions.

## Project Objectives
- Create an entertaining Halloween-themed educational quiz platform
- Implement AI-powered dynamic question generation using OpenAI API
- Provide interactive gaming experience with lifelines and power-ups
- Build responsive, themed UI with Halloween aesthetics
- Ensure secure API key management and error handling
- Deliver real-time feedback and progress visualization

## Tools Used and Their Usage

| Tool | Usage |
|------|-------|
| **Python** | Core programming language for application logic and data handling |
| **Gradio** | Web interface framework for creating interactive quiz UI |
| **OpenAI API** | Dynamic question generation using GPT models |
| **python-dotenv** | Environment variable management for secure API key storage |
| **JSON** | Data serialization for API responses and question formatting |
| **CSS/HTML** | Custom styling for Halloween-themed interface design |
| **Git** | Version control and project management |

## Project Details

### 1. AI-Powered Question Generation
```python
def generate_questions_with_gpt(topic: str, n: int) -> Dict[str, Any]:
    client = get_openai_client()
    user_prompt = f"Topic: {topic}\nNumber of questions (N): {n}\nReturn ONLY JSON."
    resp = client.chat.completions.create(
        model=MODEL_NAME,
        temperature=TEMPERATURE,
        messages=[
            {"role": "system", "content": GEN_SYS_PROMPT},
            {"role": "user", "content": user_prompt},
        ],
    )
```
**Features:**
- Dynamic question generation using OpenAI GPT
- Structured JSON response validation
- Fallback questions for API failures
- Topic-specific content mapping

### 2. Quiz Categories Implementation
```python
CATEGORIES = [
    "General Halloween",
    "Horror Movies (Classic)",
    "Horror Movies (Modern)", 
    "Urban Legends",
    "Monsters & Creatures",
    "Haunted Places",
    "Witchcraft & Folklore",
    "Kids-Friendly Spooky"
]
```
**Screenshot: Category Selection Interface**
- 8 diverse Halloween-themed categories
- Dropdown selection with intuitive labels
- Question count slider (5-20 questions)
- Themed styling with pumpkin colors

### 3. Game Mechanics & Lifelines
```python
def apply_fifty(st):
    # 50-50 lifeline eliminates 2 wrong answers
def apply_flip(st):
    # Flip lifeline skips to next question
def apply_pass(st):
    # Pass lifeline skips question without penalty
```
**Screenshot: Lifeline System**
- **50-50**: Eliminates 2 incorrect options
- **Flip**: Skip to next question in queue
- **Pass**: Skip question without losing points
- Limited usage (1 per lifeline type)

### 4. Interactive UI Components
**Screenshot: Main Quiz Interface**
- **Question Display**: Large, readable question text in card format
- **Multiple Choice**: Radio button options with hover effects
- **Action Buttons**: Submit, lifelines, and game controls
- **Progress Bar**: Visual progress with pumpkin emojis
- **Score Tracking**: Real-time score and question counter

### 5. Halloween-Themed Styling
```css
:root{
  --pumpkin:#ff7a00; --plum:#6c4ce6; --mint:#d8ffe6;
}
.float-ghost, .float-bat {
  position:absolute; opacity:.12;
  animation: drift 14s infinite ease-in-out;
}
```
**Screenshot: Themed Interface**
- Floating ghost and bat animations
- Pumpkin orange and purple color scheme
- Gradient backgrounds and card designs
- Animated progress indicators

### 6. Error Handling & Fallbacks
```python
def _fallback_questions(topic: str, n: int, reason: str) -> Dict[str, Any]:
    base = [
        {"question": "Which creature transforms during a full moon?",
         "options": ["Vampire", "Werewolf", "Zombie", "Banshee"], 
         "correct_index": 1}
    ]
```
**Features:**
- Graceful API failure handling
- Predefined fallback questions
- JSON validation and sanitization
- User-friendly error messages

### 7. Security Implementation
```python
# Load environment variables
load_dotenv()
OPENAI_API_KEY = os.getenv('OPENAI_API_KEY')
```
**Screenshot: Environment Setup**
- Secure API key storage in .env file
- Git ignore configuration for sensitive data
- Environment variable validation

## Screenshots and Features

### Main Interface
![Main Interface](screenshot-main.png)
- Halloween-themed header with floating animations
- Category dropdown with 8 spooky options
- Question count slider for customizable difficulty
- Prominent "Start Game" button with gradient styling

### Quiz Experience  
![Quiz Interface](screenshot-quiz.png)
- Large question display in styled card
- Radio button options with hover animations
- Lifeline buttons (50-50, Flip, Pass) with usage counters
- Real-time score and progress tracking
- Submit button for answer confirmation

### Feedback System
![Feedback Display](screenshot-feedback.png)
- Immediate visual feedback with colored badges
- Correct/incorrect answer indication
- Detailed explanations for learning
- Progress bar with pumpkin emoji visualization

### Game Completion
![Completion Screen](screenshot-complete.png)
- Final score display with celebration emojis
- Game over state with restart option
- Complete progress bar showing 100%
- Summary of performance metrics

## Project Conclusion

### What Was Accomplished
- **AI Integration**: Successfully integrated OpenAI API for dynamic question generation
- **Interactive Gaming**: Built engaging quiz experience with lifelines and power-ups
- **Themed Design**: Created immersive Halloween-themed interface with animations
- **Error Resilience**: Implemented robust error handling with fallback mechanisms
- **Security**: Established secure API key management and environment configuration
- **User Experience**: Delivered intuitive interface with real-time feedback and progress tracking

### Key Learnings
1. **API Integration**: Mastered OpenAI API integration with proper error handling and response validation
2. **Gradio Framework**: Advanced understanding of Gradio's state management and interactive components
3. **CSS Animations**: Implemented floating animations and themed styling for enhanced user experience
4. **Game Logic**: Developed complex game mechanics with lifelines, scoring, and progress tracking
5. **JSON Handling**: Learned robust JSON parsing and validation techniques for API responses
6. **Security Practices**: Applied environment variable management and secure development practices
7. **Fallback Systems**: Created resilient applications with graceful degradation capabilities

### Technical Challenges Overcome
- **State Management**: Complex game state handling across multiple UI interactions
- **API Response Validation**: Robust parsing of AI-generated JSON with error recovery
- **Dynamic UI Updates**: Real-time interface updates based on game state changes
- **CSS Integration**: Custom styling within Gradio's component system

### Future Enhancements
- **User Profiles**: Add user authentication and progress tracking
- **Difficulty Levels**: Implement adaptive difficulty based on performance
- **Multiplayer Mode**: Add competitive multiplayer quiz sessions
- **Question Database**: Build persistent question storage and caching
- **Mobile Optimization**: Enhanced responsive design for mobile devices
- **Analytics Dashboard**: Performance tracking and learning insights
- **Social Features**: Share scores and challenge friends

This project demonstrates advanced web application development combining AI integration, interactive gaming mechanics, and modern UI design principles in a fun, educational Halloween-themed package.

### Made By
Aanchal Bajpai<br>
Vidushi Dixit<br>
Shatakshi Srivastava<br>
