# Language Learning Platform

## 📖 Overview

A next-generation language learning platform that combines the strongest aspects of Anki, Duolingo, Memrise, and Busuu while leveraging AI to automatically generate learning content.

**Core Idea:** A single word becomes a complete learning experience.

When a new word is added, the system automatically enriches it with definitions, CEFR level, pronunciation, examples, flashcards, quizzes, stories, conversations, and review schedules.

## 🎯 Vision

Most language-learning platforms focus on either:

- **Memorization** (Anki)
- **Gamification** (Duolingo)
- **Vocabulary acquisition** (Memrise)
- **Structured courses** (Busuu)

This platform combines all four approaches into one AI-powered ecosystem.

## 📚 Table of Contents

- [Core Features](#core-features)
- [System Architecture](#system-architecture)
- [Technology Stack](#technology-stack)
- [MVP Roadmap](#mvp-roadmap)
- [Long-Term Vision](#long-term-vision)

## ✨ Core Features

### 1. Word Intelligence Engine

**Description:** The foundation of the platform.

Whenever a word is submitted, the engine automatically enriches it.

**Input:** `achievement`

**Generated Data:**

```json
{
  "word": "achievement",
  "level": "B1",
  "part_of_speech": "noun",
  "ipa": "/əˈtʃiːvmənt/",
  "translation": "...",
  "definition": "...",
  "synonyms": [],
  "antonyms": [],
  "examples": [],
  "audio_url": ""
}
```

**Features:**

- Dictionary enrichment
- Translation generation
- IPA generation
- Pronunciation audio
- CEFR classification
- Synonym extraction
- Antonym extraction
- Frequency ranking
- Topic categorization ### 2. AI Content Generation Engine

Automatically creates learning material from words.

**Flashcards**

- Front: `achievement`
- Back: definition, translation, audio, example

**Quizzes**

- Multiple Choice
- Fill in the Blank
- Match Pairs
- True / False
- Listening Quiz

**Story Generation**

- Generate stories containing target vocabulary, grammar focus, and difficulty level
- Example: A2 Story contains (achievement, goal, success)

**Dialogue Generation**

- Job Interview (achievement, experience, skills)
- Restaurant, Hotel, Airport, Meeting, Daily Life

**Conversation Scenarios**

- Real-world communication practice ### 3. Spaced Repetition System (SRS)

Inspired by Anki.

**Goals:** Show words exactly before they are forgotten.

**Features:**

- Ease Factor
- Review Intervals
- Forgetting Curve
- Adaptive Scheduling

**Review States:**

- New
- Learning
- Reviewing
- Mastered

**Rating Options:**

- Again
- Hard
- Good
- Easy

### 4. Knowledge Graph

Connect words together.

**Example:**

```
happy
├─ happiness
├─ happily
├─ unhappy
├─ joyful
└─ delighted
```

**Features:**

- Word families
- Related words
- Synonyms graph
- Antonyms graph
- Topic clusters

### 5. CEFR Learning Path

Structured progression through language levels.

**Levels:** A1 → A2 → B1 → B2 → C1 → C2

**Features:**

- Vocabulary roadmap
- Grammar roadmap
- Progress tracking
- Level assessment

### 6. Speaking Module

AI speaking coach with real-time feedback.

**Features:**

- Speech Recognition
- Pronunciation Scoring
- Accent Analysis
- Fluency Scoring
- Grammar Correction

**Output Example:**

```json
{
  "pronunciation": 82,
  "fluency": 75,
  "grammar": 91
}
```

### 7. Listening Module

Improve listening skills through various exercises.

**Features:**

- Native Audio
- AI Generated Audio
- Dictation Exercises
- Listening Quizzes

### 8. Reading Module

Reading comprehension training.

**Features:**

- Stories
- Articles
- News
- Dialogues

**Metrics:**

- Reading Speed
- Unknown Words
- Comprehension Score

### 9. Writing Module

AI writing evaluation and improvement.

**Features:**

- Grammar correction
- Style suggestions
- Vocabulary enhancement
- CEFR estimation

### 10. Gamification System

Inspired by Duolingo.

**XP System:**

- Lesson = 10 XP
- Quiz = 5 XP
- Review = 2 XP

**Features:**

- Levels
- XP
- Streaks
- Achievements
- Leaderboards
- Daily Goals

### 11. User Progress Analytics

Track learning performance and insights.

**Metrics:**

- Total Words Learned
- Retention Rate
- Daily XP
- Weekly XP
- Speaking Score
- Listening Score
- Reading Score

### 12. AI Tutor

Chat-based learning assistant.

**Capabilities:**

- Explain grammar
- Translate phrases
- Create exercises
- Correct mistakes
- Generate examples

### 13. Course Builder

Internal tool for administrators to create:

- Vocabulary Courses
- Grammar Courses
- Reading Courses
- Speaking Courses

## 🏗️ System Architecture

### Architecture Overview

```
┌──────────────────┐
│ Mobile/Web UI    │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ API Gateway      │
└────────┬─────────┘
         │
    ┌────┼────────┬─────────────┐
    ▼    ▼        ▼             ▼
┌─────┐ ┌──────┐ ┌────────┐ ┌────────┐
│User │ │Learn │ │ AI     │ │Speech  │
│Core │ │Core  │ │Service │ │Service │
└─────┘ └──────┘ └────────┘ └────────┘
    │    │        │             │
    ▼    ▼        ▼             ▼
┌──────────┐ ┌──────────┐ ┌──────────┐
│PostgreSQL│ │Redis Cache│ │Vector DB │
└──────────┘ └──────────┘ └──────────┘
```

### Microservices

**User Service**

- Authentication
- Authorization
- User Profile
- Progress Tracking

**Vocabulary Service**

- Word Management
- Dictionary Data
- CEFR Levels
- Examples

**Content Generation Service**

- Flashcards
- Stories
- Dialogues
- Quizzes

**SRS Service**

- Review Scheduling
- Memory Algorithm
- Recall Prediction

**AI Tutor Service**

- Chat
- Corrections
- Explanations

**Speech Service**

- Speech-to-Text
- Text-to-Speech
- Pronunciation Evaluation

**Analytics Service**

- Progress Reports
- Learning Insights
- Recommendations

### Database Design

**Words Table**

```
id
word
language
level
ipa
frequency_rank
definition
created_at
```

**Examples Table**

```
id
word_id
sentence
translation
```

**Synonyms Table**

```
id
word_id
synonym_word_id
```

**Flashcards Table**

```
id
word_id
content
```

**User Progress Table**

```
id
user_id
word_id
ease_factor
interval
next_review
```

**Quizzes Table**

```
id
word_id
type
question
answer
```

## 🛠️ Technology Stack

| Layer        | Technology                           |
| ------------ | ------------------------------------ |
| **Frontend** | Flutter, React Native (Alternative)  |
| **Backend**  | NestJS, Node.js                      |
| **Database** | PostgreSQL                           |
| **Cache**    | Redis                                |
| **Search**   | Elasticsearch                        |
| **AI**       | OpenAI, Local LLM (Future)           |
| **Speech**   | Whisper, Azure Speech, Google Speech |
| **Storage**  | AWS S3, Cloudflare R2                |

## 🚀 MVP Roadmap

### Phase 1: Foundation

- [ ] Authentication
- [ ] Word Intelligence Engine
- [ ] Database Setup
- [ ] Flashcards
- [ ] Spaced Repetition System

### Phase 2: Content & Progress

- [ ] AI Content Generation
- [ ] Quizzes
- [ ] Stories
- [ ] Progress Tracking

### Phase 3: Speaking & AI

- [ ] Speaking Module
- [ ] AI Tutor
- [ ] Pronunciation Scoring

### Phase 4: Engagement

- [ ] Gamification System
- [ ] Social Features
- [ ] Leaderboards

### Phase 5: Advanced Learning

- [ ] Knowledge Graph
- [ ] Personalized Learning Paths
- [ ] Full AI Language Coach

## 🎓 Long-Term Vision

**The Complete Learning Journey:**

```
1 Word
  ↓
AI Enrichment
  ↓
Flashcards
  ↓
Quizzes
  ↓
Stories
  ↓
Conversations
  ↓
Speaking Practice
  ↓
Mastery Tracking
```

**Goal:** Build a platform where learners never study isolated vocabulary. Every word becomes part of a complete language-learning ecosystem that combines:

- Memorization (Anki approach)
- Engagement (Duolingo approach)
- Vocabulary depth (Memrise approach)
- Structured learning (Busuu approach)
