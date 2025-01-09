
# Tasks Entity Documentation
![image](https://github.com/user-attachments/assets/708994a6-2b10-4dfd-ae5b-1424e406e83a)

## Overview
The Tasks entity is designed to manage and track various tasks within the system. It includes details such as task identification, status, program association, and timeline, ensuring proper task management and accountability.

---

## Fields and Behaviors


---
### 1. **Task Name**
- **Type**: Text
- **Description**: The name or title of the task.
- **Usage**: Used to describe the task in a more detailed or human-readable format compared to the `Name` field.

---

### 2. **Task ID**
- **Type**: Number (Auto-increment)
- **Description**: A system-generated unique identifier for the task.
- **Usage**: Ensures every task has a distinct and unique reference for internal processing.

---


### 3. **Task Status**
- **Type**: Enum
- **Description**: Represents the current status of the task.
- **Options**:
  - Not Started
  - In Progress
  - Completed
  - On Hold
  - Cancelled
- **Usage**: Tracks the progress or state of the task within its lifecycle.
---

### 4. **Due Date**
- **Type**: Date
- **Description**: The date by which the task must be completed.
- **Usage**: Helps in planning and ensuring timely completion of tasks.

---

### 5. **Description**
- **Type**: Text
- **Description**: A detailed description of the task.
- **Usage**: Clarifies the purpose, objectives, or details of the task for the assigned user or team.

---

### 6. **Program**
- **Type**: Link
- **Description**: Links the task to a specific program.
- **Usage**: Establishes a connection between the task and the program it belongs to for better organization and reporting.

---
### 7. **Assigned User**
- **Type**: Link
- **Description**: The user responsible for completing the task.
- **Usage**: Allocates accountability and ensures tasks are assigned to specific individuals.

---
### 8. **Teams**
- **Type**: Link Multiple
- **Description**: Teams associated with the task for collaborative work.
- **Usage**: Ensures that multiple users or groups can work together on a single task effectively.

- 

---

## Key System Behaviors

### 1. **Task Lifecycle Management**
- The **Due Date** and **Task Status** fields allow tracking and managing tasks through their lifecycle.
- Status transitions include:
  - `Not Started` → `In Progress` → `Completed`
  - Can also transition to `On Hold` or `Cancelled` as required.

---

### 2. **Program Association**
- Tasks can be linked to specific programs through the **Program** field.
- This relationship ensures that tasks are aligned with the program's objectives and can be reported as part of program activities.

---

### 3. **Collaboration and Accountability**
- The **Assigned User** and **Teams** fields enable task assignment to individuals or groups.
- Maintains clear accountability for completion and fosters collaboration for complex tasks.

---

### 4. **Auditing and Change Tracking**
- The **Created At**, **Created By**, **Modified At**, and **Modified By** fields provide a complete audit trail of task creation and updates.

---
