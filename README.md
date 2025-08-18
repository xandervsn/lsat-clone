# LSAT Online Test Environment

A practice version of the LSAT online administration system that supports custom test content via JSON format.

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

## Usage

1. **Load Default Test**: Simply click "Begin Test" to use the built-in sample questions
2. **Load Custom JSON**: 
   - Upload a JSON file using the file picker
