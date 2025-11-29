MyDerma Interactive Skincare Agent

Track: Concierge Agents
Subtitle: Personalized Skincare Recommendations and Dermatologist Booking Using AI Agents

1. Problem Statement

Skin care is a deeply personal process, with routines, remedies, and treatments varying significantly across individuals. Managing a consistent skincare routine and finding verified dermatologists can be challenging due to:

Time-consuming manual research for appropriate remedies and diets.

Confusion between Ayurvedic and medical approaches for skin types.

Difficulty in locating trusted dermatologists nearby.

These challenges often lead to inconsistent care, delayed treatments, and sub-optimal skin health outcomes.

Objective: Develop an AI-powered concierge agent that simplifies skincare management by recommending remedies, routines, and diet plans tailored to a user’s skin type, approach, and location, while also facilitating dermatologist appointment booking.

2. Proposed Solution

MyDerma is a personal interactive AI agent designed to automate skincare management. It leverages a multi-agent system architecture to provide:

Personalized Skincare Recommendations

Generates Ayurvedic or medical remedies based on user skin type (oily, dry, normal).

Provides morning/night skincare routines for daily implementation.

Suggests dietary modifications to support skin health.

Dermatologist Referral System

Recommends nearby dermatologists with clinic details and contact information based on the user’s location.

Appointment Booking Module

Allows users to book appointments with recommended dermatologists directly through the agent.

Key Benefits:

Reduces manual effort and time in managing skincare.

Provides actionable, easy-to-follow recommendations.

Ensures users can access professional help seamlessly.

3. Features Demonstrated

Multi-Agent System

Skincare Recommendation Agent: Suggests remedies, routines, and diet plans.

Dermatologist Referral Agent: Identifies and lists nearby dermatologists.

Appointment Booking Agent: Handles scheduling and confirms bookings.

Tools & Integrations

Custom functions for skincare recommendation, dermatologist lookup, and appointment booking.

IPyWidgets for interactive front-end and data collection.

Kaggle Secrets integration for Google API key setup, allowing future location-based features.

Session & Memory Management

Current implementation saves user profile in memory.

Can be extended to long-term memory for tracking skincare progress over weeks or months.

Observability & Logging

Outputs recommendations and booking confirmations as pretty-printed JSON, allowing easy tracking and debugging.

4. Architecture

High-Level Architecture:

           +-------------------------+
           |      User Interface     |
           |  (IPyWidgets Frontend) |
           +-----------+-------------+
                       |
                       v
           +-------------------------+
           |  MyDerma Core Agent     |
           +-----------+-------------+
                       |
        +--------------+---------------+
        |                              |
        v                              v
+----------------+              +----------------+
| Skincare Agent |              | Dermatologist  |
| - Generates    |              | Referral Agent |
|   recommendations |           | - Finds nearby |
| - Diet & routine |            |   dermatologists|
+----------------+              +----------------+
        |                              |
        +--------------+---------------+
                       |
                       v
            +------------------+
            | Appointment Agent|
            | - Books slots    |
            | - Confirms time  |
            +------------------+


Workflow:

User inputs name, skin type, city, approach.

Clicks Run MyDerma → Agent generates skincare plan and dermatologist list.

User selects doctor → Inputs date/time → Clicks Book Appointment.

System outputs confirmation JSON.

5. Technical Implementation

Tech Stack:

Python 3 for core agent logic.

IPyWidgets for interactive UI in Kaggle Notebook.

JSON for structured data handling.

Kaggle Secrets to manage API keys securely.

Sample Code Features:

get_skincare_recommendation(profile) – Generates remedies, routines, and diet plans.

get_dermatologist_referral(profile) – Returns nearby dermatologists.

book_appointment(derma, date, time) – Books appointment and confirms details.

Interactive widgets for input and booking.

Integration Points:

Multi-agent logic is modular for future expansion (e.g., LLM-powered agents for advice, multi-agent coordination).

Output logs and pretty-printed JSON provide observability for debugging and user transparency.

6. Example Output

User Profile:

{
  "name": "Iniya",
  "skin_type": "oily",
  "location": "Bengaluru",
  "approach": "ayurvedic"
}


Skincare Recommendation:

{
  "recommended_remedies": ["Aloe vera gel", "Neem paste mask", "Multani mitti mask"],
  "skincare_plan": [
    "Morning: Cleanser + Toner + Oil-free moisturizer",
    "Night: Gentle cleanser + Serum + Light moisturizer"
  ],
  "diet_plan": ["Reduce oily food", "Eat fruits & vegetables", "Drink water"]
}


Nearby Dermatologists:

[
  {"name": "Dr. Skin Care", "clinic": "Bengaluru Dermatology Clinic", "contact": "123-456-7890"},
  {"name": "Dr. Glow", "clinic": "Bengaluru Skin Center", "contact": "987-654-3210"}
]


Appointment Confirmation:

{
  "status": "booked",
  "doctor": "Dr. Skin Care",
  "clinic": "Bengaluru Dermatology Clinic",
  "date": "2025-11-25",
  "time": "10:00"
}

7. Advantages

Personalized Recommendations: Tailored to skin type and approach.

Automated Scheduling: Simplifies finding and booking dermatologists.

Extensible Architecture: Can integrate LLMs, memory systems, or parallel agents.

Interactive and User-Friendly: Intuitive interface with instant feedback.

8. Limitations & Future Work

Current Limitations:

Recommendations are rule-based, not AI-driven.

Dermatologist list is static.

No long-term tracking of user routines yet.

Future Enhancements:

Integrate LLM agents for dynamic advice.

Add parallel agents for handling multiple users simultaneously.

Implement long-term memory for tracking progress and habit formation.

Deploy on cloud platform (e.g., Vertex AI Agent Engine) for real-time access.

Add video or image processing for skin condition analysis.
