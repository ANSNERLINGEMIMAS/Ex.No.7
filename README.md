# Ex.No. 7 – Develop a Prompt-Based Personal Productivity Application

**Date:19/11/2026**  
**Register No.:212224040027**

## Aim

To develop a prompt-based application using ChatGPT that helps users organize daily tasks, schedule reminders, generate wellness suggestions, and answer general queries. The experiment demonstrates the progression from simple to advanced prompt designs and their corresponding outputs.

## AI Tools Required

1. ChatGPT
2. Python 3
3. VS Code / Python IDLE
4. Command Prompt or Terminal

## Explanation

A prompt-based application uses instructions given to a Large Language Model (LLM) to perform specific tasks. In this experiment, ChatGPT is used as a Personal Productivity Assistant.

The assistant helps users manage their daily activities, organize tasks based on priority, plan schedules, suggest wellness tips, and answer general questions.

The application uses natural language prompts so users can interact with it easily without needing complex commands.

## 1. Core Requirements

The Personal Productivity Assistant should provide the following features:

**1. Daily Task Manager**
- Accept tasks using natural language.
- Organize tasks based on priority.
- Display pending and completed tasks.
- Generate daily task summaries.

**2. Smart Scheduler**
- Help users organize daily schedules.
- Identify overlapping activities.
- Suggest suitable time slots.
- Provide reminder details.

**3. Wellness Tips Generator**
- Suggest healthy daily habits.
- Recommend hydration and screen breaks.
- Provide simple activity suggestions.
- Adapt suggestions according to user preferences.

**4. General Query Assistant**
- Answer general questions.
- Provide study and productivity suggestions.
- Help users plan academic activities.

## 2. Progressive Prompt Design

The application is developed using different levels of prompt engineering, starting with a simple prompt and gradually adding more instructions.

### Level 1 – Simple Prompt

**Input Prompt:**

```text
Help me organize my daily tasks.
```

**Expected Output:**

```text
Here is a simple daily task list:

1. Complete college assignments.
2. Study programming.
3. Revise important topics.
4. Take a short break.
5. Review completed tasks.
```

**Observation:** The basic prompt generates a general task list but does not consider deadlines or priorities.

### Level 2 – Role-Based Prompt

**Input Prompt:**

```text
You are my personal productivity assistant.
Help me organize my daily activities and
suggest a productive daily routine.
```

**Expected Output:**

```text
Personal Productivity Assistant

Morning:
- Review your daily goals.
- Complete important academic tasks.

Afternoon:
- Attend classes.
- Work on programming assignments.

Evening:
- Practise coding.
- Revise academic topics.

Night:
- Review completed tasks.
- Prepare for the next day.
```

**Observation:** Assigning a role helps the AI respond like a personal productivity assistant.

### Level 3 – Task Management Prompt

**Input Prompt:**

```text
Act as my task manager.

Organize the following tasks based on priority:

1. Complete Python assignment – Today
2. Prepare for Java exam – Tomorrow
3. Update GitHub project – This week
4. Revise AI/ML concepts – Today

Display the tasks in a table.
```

**Expected Output:**

| Task | Deadline | Priority |
|---|---|---|
| Complete Python assignment | Today | High |
| Revise AI/ML concepts | Today | High |
| Prepare for Java exam | Tomorrow | Medium |
| Update GitHub project | This week | Low |

**Observation:** Adding task details and formatting instructions produces a more organized response.

### Level 4 – Smart Scheduling Prompt

**Input Prompt:**

```text
You are an intelligent scheduling assistant.

Help me plan my day using these activities:

- Complete assignments
- Practise Java
- Work on my project
- Take breaks

Create a balanced timetable.
Identify any overlapping activities and
suggest suitable time slots.
```

**Expected Output:**

| Time | Activity |
|---|---|
| 9:00 AM – 10:00 AM | Complete assignments |
| 10:00 AM – 10:15 AM | Break |
| 10:15 AM – 11:15 AM | Java practice |
| 11:15 AM – 12:00 PM | Project work |
| 12:00 PM – 1:00 PM | Lunch and rest |
| 1:00 PM – 2:00 PM | Project development |
| 2:00 PM – 2:15 PM | Short break |

**Observation:** The AI creates a timetable based on the given activities. Actual scheduling should also consider the user's availability.

### Level 5 – Wellness Tips Prompt

**Input Prompt:**

```text
Act as a wellness assistant.

I spend several hours studying and working
on my laptop. Suggest five simple wellness
habits that I can follow every day.
```

**Expected Output:**

```text
Daily Wellness Suggestions:

1. Drink water regularly.
2. Take short breaks between study sessions.
3. Maintain a comfortable sitting posture.
4. Include some light physical activity.
5. Maintain a regular sleep schedule.
```

**Observation:** The AI generates practical wellness suggestions based on the user's situation.

### Level 6 – Advanced Personalized Prompt

**Input Prompt:**

```text
You are my personal productivity assistant.

Your responsibilities are:

1. Manage my daily tasks.
2. Organize tasks based on priority and deadlines.
3. Create a balanced daily timetable.
4. Suggest simple wellness habits.
5. Answer general academic and productivity queries.

Use clear tables and simple language.
Ask for missing information when necessary.
Adapt your suggestions based on the preferences
I provide during our conversation.

At the end of each response, provide a short
summary of my important tasks.
```

**Expected Output:**

```text
PERSONAL PRODUCTIVITY ASSISTANT

1. Today's Important Tasks
- Complete pending assignments.
- Practise Java programming.
- Work on the academic project.

2. Suggested Schedule
- Morning: Academic work
- Afternoon: Programming practice
- Evening: Project development

3. Wellness Tips
- Take regular screen breaks.
- Drink water throughout the day.
- Maintain a balanced routine.

4. Productivity Suggestion
Complete high-priority tasks first and
avoid scheduling too many activities together.

Daily Summary:
Focus on assignments, Java practice,
and project development.
```

**Observation:** The advanced prompt combines task management, scheduling, wellness suggestions, and personalization in a single assistant.

## 3. Procedure

1. Open ChatGPT.
2. Define the core requirements of a personal productivity assistant.
3. Create a simple prompt for organizing daily tasks.
4. Improve the prompt by assigning ChatGPT the role of a productivity assistant.
5. Add instructions for task prioritization and scheduling.
6. Include wellness suggestions and general query support.
7. Test the prompts using different user inputs.
8. Observe and compare the generated outputs.
9. Collect user preferences and provide them as additional context.
10. Analyse the final output and identify improvements.

## 4. Python Prototype – Personal Productivity Assistant

The following Python program demonstrates a simple command-line prototype. It manages tasks locally and provides a basic schedule and wellness suggestions. It does not connect to the ChatGPT API or send actual notifications.

```python
tasks = []

def add_task():
    task = input("Enter your task: ")
    priority = input("Enter priority (High/Medium/Low): ")
    deadline = input("Enter deadline: ")

    tasks.append({
        "task": task,
        "priority": priority,
        "deadline": deadline,
        "status": "Pending"
    })

    print("Task added successfully!")


def view_tasks():
    if not tasks:
        print("No tasks available.")
        return

    print("\nYOUR DAILY TASKS")

    priority_order = {
        "high": 1,
        "medium": 2,
        "low": 3
    }

    sorted_tasks = sorted(
        tasks,
        key=lambda item: priority_order.get(
            item["priority"].lower(), 4
        )
    )

    for task in sorted_tasks:
        print("\nTask:", task["task"])
        print("Priority:", task["priority"])
        print("Deadline:", task["deadline"])
        print("Status:", task["status"])


def complete_task():
    task_name = input("Enter task name to complete: ")

    for task in tasks:
        if task["task"].lower() == task_name.lower():
            task["status"] = "Completed"
            print("Task marked as completed!")
            return

    print("Task not found.")


def wellness_tips():
    tips = [
        "Drink water regularly.",
        "Take short breaks while studying.",
        "Maintain a comfortable posture.",
        "Include light physical activity.",
        "Maintain a regular sleep schedule."
    ]

    print("\nDAILY WELLNESS TIPS")

    for tip in tips:
        print("-", tip)


while True:
    print("\nPERSONAL PRODUCTIVITY ASSISTANT")
    print("1. Add Task")
    print("2. View Tasks")
    print("3. Complete Task")
    print("4. Wellness Tips")
    print("5. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        add_task()
    elif choice == "2":
        view_tasks()
    elif choice == "3":
        complete_task()
    elif choice == "4":
        wellness_tips()
    elif choice == "5":
        print("Thank you for using the assistant!")
        break
    else:
        print("Invalid choice. Try again.")
```

### Sample Output

```text
PERSONAL PRODUCTIVITY ASSISTANT

1. Add Task
2. View Tasks
3. Complete Task
4. Wellness Tips
5. Exit

Enter your choice: 1

Enter your task: Complete Python assignment
Enter priority (High/Medium/Low): High
Enter deadline: Today

Task added successfully!

Enter your choice: 2

YOUR DAILY TASKS

Task: Complete Python assignment
Priority: High
Deadline: Today
Status: Pending

Enter your choice: 4

DAILY WELLNESS TIPS

- Drink water regularly.
- Take short breaks while studying.
- Maintain a comfortable posture.
- Include light physical activity.
- Maintain a regular sleep schedule.
```

## 5. Output Analysis

| Prompt Level | Technique Used | Main Output |
|---|---|---|
| Level 1 | Simple Prompt | Basic task list |
| Level 2 | Role-Based Prompt | Personalized routine |
| Level 3 | Structured Prompt | Priority-based task table |
| Level 4 | Contextual Prompt | Daily timetable |
| Level 5 | Wellness Prompt | Wellness suggestions |
| Level 6 | Advanced Prompt | Integrated productivity assistant |

**Analysis:**

- Simple prompts provide general responses.
- Role-based prompts give the AI a specific responsibility.
- Structured prompts improve the organization of information.
- Contextual prompts help generate more relevant schedules.
- Advanced prompts combine multiple functionalities.
- User feedback and additional context help the assistant adapt its suggestions.

## 6. Advantages

1. Saves time by organizing daily activities.
2. Helps users identify important tasks.
3. Improves time management.
4. Provides personalized suggestions.
5. Supports academic planning.
6. Demonstrates practical applications of prompt engineering.

## 7. Limitations

1. AI-generated schedules may need manual correction.
2. Incorrect or incomplete user information can affect the output.
3. Actual notifications require a separate reminder or scheduling system.
4. Preference adaptation depends on the context or memory available to the application.
5. AI responses should be reviewed before important decisions are made.

## Result

The prompt-based Personal Productivity Assistant was designed and demonstrated using ChatGPT. Different levels of prompts were tested, progressing from simple task organization to advanced personalized assistance. A Python command-line prototype was also developed to add, view, and complete tasks and display wellness tips.

## Conclusion

The experiment demonstrates how prompt engineering can be used to develop a practical personal productivity application using Large Language Models. By gradually improving prompts with roles, context, structure, and user preferences, the assistant can provide more organized and relevant responses. This experiment also demonstrates how AI can support everyday task management, scheduling, and productivity.
