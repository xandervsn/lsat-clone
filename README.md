# LSAT Online Test Environment

A practice version of the LSAT online administration system that supports custom test content via JSON format.

## Features

- **Reading Comprehension (RC)**: Support for up to 4 passages with 5-8 questions each
- **Logical Reasoning (LR1 & LR2)**: Two separate LR sections with individual questions
- **Custom JSON Input**: Load your own test content via JSON files or text input
- **Full Test Simulation**: 4 sections with timing, breaks, and scoring

## JSON Format

The application accepts JSON files with the following structure. A complete test must include all three sections: RC, LR1, and LR2.

### Complete Test Structure

```json
{
  "RC": {
    "timeLimit": 35,
    "passages": [...]
  },
  "LR1": {
    "timeLimit": 35,
    "questions": [...]
  },
  "LR2": {
    "timeLimit": 35,
    "questions": [...]
  }
}
```

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

### Logical Reasoning (LR1 & LR2)

```json
{
  "LR1": {
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

**Note:** Both LR1 and LR2 sections follow the same structure. The application expects exactly two Logical Reasoning sections.

## Usage

1. **Load Default Test**: Simply click "Begin Test" to use the built-in sample questions
2. **Load Custom JSON**: 
   - Upload a JSON file using the file picker
   - Click "Load JSON Data" to apply