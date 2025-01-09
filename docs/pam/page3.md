# Programs Entity Documentation
![image](https://github.com/user-attachments/assets/03094df9-7041-47dd-8843-b1cf7267e60d)

## Overview
The Programs entity is used to manage and document various programs within the system. It includes details such as program identification, timeline, donor information, inclusion criteria, and the current program status.

---

## Interface Explanation 

1. **Program ID**: Unique identifier for the program.
2. **Program Name**: Name of the program.
3. **Start Date**: The date when the program begins.
4. **End Date**: The date when the program concludes.
5. **Donor**: The program's funding source.
6. **Description**: Detailed information about the program.
7. **Inclusion Criteria**: Defines eligibility criteria for participants.
8. **Program Status**: Indicates the current stage of the program (e.g., Planned, Active).
9. **Assigned User**: The user managing the program.
10. **Teams**: The team(s) collaborating on the program.

---
## Fields and Behaviors

### 1. **Program ID**
- **Type**: Text (Required)
- **Description**: A unique identifier for the program.
- **Usage**: Used to distinguish and reference each program in the system.

---

### 2. **Program Name**
- **Type**: Text (Required)
- **Description**: The name of the program.
- **Usage**: Used to describe the program in a human-readable format.

---

### 3. **Start Date**
- **Type**: Date (Required)
- **Description**: The date when the program is scheduled to begin.
- **Usage**: Helps in determining the program timeline and planning activities.

---

### 4. **End Date**
- **Type**: Date (Required)
- **Description**: The date when the program is scheduled to end.
- **Usage**: Marks the conclusion of the program and is used for program lifecycle management.

---

### 5. **Donor**
- **Type**: Text (Required)
- **Description**: The name or identifier of the donor(s) funding the program.
- **Usage**: Keeps track of the program's financial source and helps in donor reporting.

---

### 6. **Description**
- **Type**: Text
- **Description**: A detailed description of the program.
- **Usage**: Used for documentation purposes to provide additional details about the program's objectives, activities, and scope.

---

### 7. **Inclusion Criteria**
- **Type**: Text (Required)
- **Description**: Criteria that determine eligibility for the program.
- **Usage**: Ensures transparency and clarity regarding the target audience or beneficiaries.

---

### 8. **Program Status**
- **Type**: Dropdown (Required)
- **Default Value**: `Planned`
- **Options**:
  - Planned
  - Active
  - Completed
  - Cancelled
- **Description**: Represents the current status of the program.
- **Usage**: Tracks the lifecycle stage of the program.

---

### 9. **Assigned User**
- **Type**: Relationship
- **Description**: The user responsible for managing or overseeing the program.
- **Usage**: Allocates accountability and ensures smooth program execution.

---

### 10. **Teams**
- **Type**: Relationship
- **Description**: Teams assigned to the program for collaboration.
- **Usage**: Facilitates team-based program management and resource allocation.

---

## Key System Behaviors

### 1. **Program Lifecycle Management**
- The combination of **Start Date**, **End Date**, and **Program Status** provides a complete overview of the program's lifecycle.
- Status transitions:
  - `Planned` → `Active` → `Completed`
  - Can also transition to `Cancelled` based on program needs.

---

### 2. **Donor Tracking**
- Donor information is captured to maintain transparency and accountability in program funding.
- The system can generate donor-specific reports based on this field.

---

### 3. **Eligibility Management**
- The **Inclusion Criteria** field ensures that only eligible individuals or groups are included in the program.
- Can be used as a reference during program participant selection.

---

### 4. **Collaboration and Accountability**
- The **Assigned User** and **Teams** fields enable tracking of personnel or groups responsible for the program, promoting clear accountability and collaborative efforts.

---

