# LSAT Online Test Environment

A practice version of the LSAT online administration system that supports custom test content via JSON format.

## Features

- **Reading Comprehension (RC)**: Support for up to 4 passages with 5-8 questions each
- **Logical Reasoning (LR)**: Individual questions with stimulus and 5 answer choices
- **Analytical Reasoning (LG)**: Logic games with setup and questions
- **Custom JSON Input**: Load your own test content via JSON files or text input
- **Full Test Simulation**: 4 sections with timing, breaks, and scoring

## JSON Format

The application accepts JSON files with the following structure:

### Reading Comprehension (RC)

```json
{
  "RC": {
    "timeLimit": 35,
    "passages": [
      {
        "title": "Passage Title",
        "content": "Full passage text...",
        "questions": [
          {
            "text": "Question text?",
            "choices": [
              "Choice A",
              "Choice B", 
              "Choice C",
              "Choice D",
              "Choice E"
            ],
            "correct": 0
          }
        ]
      }
    ]
  }
}
```

**RC Structure:**
- `timeLimit`: Section time limit in minutes (default: 35)
- `passages`: Array of up to 4 passages
  - `title`: Passage title
  - `content`: Full passage text
  - `questions`: Array of 5-8 questions per passage
    - `text`: Question text
    - `choices`: Array of exactly 5 answer choices
    - `correct`: Index of correct answer (0-4)

### Logical Reasoning (LR)

```json
{
  "LR": {
    "timeLimit": 35,
    "questions": [
      {
        "stimulus": "Argument or stimulus text...",
        "text": "Question text?",
        "choices": [
          "Choice A",
          "Choice B",
          "Choice C", 
          "Choice D",
          "Choice E"
        ],
        "correct": 0
      }
    ]
  }
}
```

**LR Structure:**
- `timeLimit`: Section time limit in minutes (default: 35)
- `questions`: Array of individual questions
  - `stimulus`: Argument or stimulus text
  - `text`: Question text
  - `choices`: Array of exactly 5 answer choices
  - `correct`: Index of correct answer (0-4)

### Logic Games (LG)

```json
{
  "LG": {
    "timeLimit": 35,
    "game": {
      "title": "Game Title",
      "setup": "Game setup and rules...",
      "questions": [
        {
          "text": "Question text?",
          "choices": [
            "Choice A",
            "Choice B",
            "Choice C",
            "Choice D", 
            "Choice E"
          ],
          "correct": 0
        }
      ]
    }
  }
}
```

**LG Structure:**
- `timeLimit`: Section time limit in minutes (default: 35)
- `game`: Single logic game
  - `title`: Game title
  - `setup`: Game setup and rules text
  - `questions`: Array of questions
    - `text`: Question text
    - `choices`: Array of exactly 5 answer choices
    - `correct`: Index of correct answer (0-4)

## Usage

1. **Load Default Test**: Simply click "Begin Test" to use the built-in sample questions
2. **Load Custom JSON**: 
   - Upload a JSON file using the file picker
   - Or paste JSON content directly into the textarea
   - Click "Load JSON Data" to apply
3. **Reset to Default**: Click "Reset to Default" to return to sample content

## File Structure

- `index.html` - Main application interface
- `script.js` - Core application logic
- `style.css` - Styling and layout
- `in.json` - Sample JSON data file
- `README.md` - This documentation

## Browser Compatibility

Works in modern browsers that support:
- ES6+ JavaScript features
- File API
- Fetch API
- CSS Grid and Flexbox

## Notes

- All sections default to 35 minutes if not specified
- Answer choices must be exactly 5 options (A-E)
- Correct answer indices are 0-based (0 = A, 1 = B, etc.)
- The application will validate JSON format and show error messages for invalid input
