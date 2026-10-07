# Employee-Leave-Management-BA-Project

## Project Overview
The Employee Leave Management & Workforce Analytics System (ELMS) is an end-to-end Business Analysis portfolio project designed to digitize, centralize, and optimize the employee leave lifecycle. The project transitions an organization from a partially manual, email- and paper-dependent process into a structured digital architecture featuring self-service request portals, multi-tier approval workflows, automated record synchronization, and executive workforce analytics.

## Business Problem
Prior to ELMS, the organization managed leave requests using manual paper forms, fragmented email threads, and localized spreadsheets. This legacy process caused significant operational friction:
* **Approval Bottlenecks:** Delays in manager reviews resulting from lack of centralized request queues.
* **Administrative Burden:** Manual balance checking and record updates conducted repeatedly by HR staff.
* **Opaque Tracking:** Limited visibility for employees regarding the status of pending requests.
* **Data Discrepancies:** Risk of duplicate entries, balance errors, and inconsistent tracking.
* **Analytical Blind Spots:** Absence of standardized cross-departmental leave pattern and absenteeism tracking.

## Business Objectives
* **Process Centralization:** Establish a unified web portal for submission, tracking, and administration of leave.
* **Workflow Automation:** Eliminate paper/email dependency and automate approver routing and balance updates.
* **Transparency Improvement:** Provide real-time leave balance visibility and automated event notifications.
* **Administrative Efficiency:** Substantially lower HR administrative overhead and eliminate manual spreadsheet reconciliation.
* **Data-Driven Governance:** Deliver interactive Power BI dashboards to support workforce planning and capacity management.

## Proposed Solution
ELMS introduces a web-based, role-governed platform structured around a closed-loop workflow:
1. **Employee:** Logs in, checks available leave entitlements, and submits a digital leave request.
2. **System Core:** Automatically validates requested dates against real-time entitlement balances and routes the request to the assigned manager.
3. **Manager:** Reviews pending requests, evaluates 6-month historical leave contexts, and submits an Approval or Rejection (with mandatory feedback).
4. **Automation Engine:** Deducts approved days from the employee's balance, updates central logs, and dispatches automated status alerts.
5. **Analytics Engine:** Aggregates operational data into Power BI management reports for executive evaluation.

## Key Users
* **Employees:** Submit requests, monitor application status, view entitlement balances, and manage historical leave records.
* **Managers / Approvers:** Review team requests, detect scheduling conflicts, enforce SLA targets, and approve or reject submissions.
* **HR / Admin Users:** Configure leave policy rules, manage entitlements, oversee staff-manager assignments, and maintain compliance audit logs.
* **Executive Management:** Monitor organizational capacity, review approval metrics, analyze seasonal trends, and evaluate departmental absenteeism.

## Major Features
* **Role-Based Authentication:** Secure access control tailored to Employees, Managers, HR, and Executives.
* **Entitlement & Balance Engine:** Real-time computation of Available Days ($Available = Entitlement - Used$), preventing requests that exceed quotas.
* **Automated Manager Routing:** System-identified approver assignment without requiring manual user selection.
* **Conflict & Overlap Detection:** Alerts managers to concurrent team requests to prevent coverage gaps.
* **Audit & Activity Tracking:** Comprehensive logging of system events, decision timestamps, and administrative policy updates.
* **Emergency / Extra Leave Workflow:** Dedicated policy-driven paths for special leave applications.

## Business Analysis Activities
* **Requirements Elicitation & Analysis:** Stakeholder interviews, MoSCoW prioritization, and requirements matrix creation.
* **Process Engineering:** Detailed As-Is and To-Be modeling alongside Gap Analysis.
* **Specification Authoring:** Creation of formal BRD, SRS, FRD, and Use Case specifications.
* **Agile Implementation:** Product backlog creation, user story mapping, story point estimation, and Sprint planning.
* **Data Modeling & BI:** Relational ERD design, SQL querying, data cleaning, and Power BI semantic modeling.
* **Validation & Testing:** End-to-end UAT test scenario planning, execution tracking, and defect management.

## Process Analysis
* **As-Is Workflow:** Employee Form $\rightarrow$ Manual HR Balance Check $\rightarrow$ Manual Manager Communication $\rightarrow$ Manual Approval $\rightarrow$ Manual Excel Update $\rightarrow$ Employee Notification.
* **Gap Analysis:** Identifies core gaps including manual submission channels, manual balance checks, approval delays, record maintenance burden, and limited analytics capability.
* **To-Be Workflow:** Employee Submission $\rightarrow$ Automated ELMS Validation $\rightarrow$ Manager Direct Review $\rightarrow$ Auto-Updated Balance Log $\rightarrow$ Automated Notification $\rightarrow$ Real-Time Executive Dashboard Feed.

## Requirements Analysis
Requirements were systematically analyzed and categorized across functional and non-functional domains:
* **Business Requirements (BR-01 to BR-08):** Centralization, digital submission, visibility, administrative reduction, and data insights.
* **Functional Requirements (FR-01 to FR-23):** Authentication, self-service submission, manager queues, HR entitlement tools, and reporting exports.
* **Non-Functional Requirements (NFR-01 to NFR-07):** Role-based access control, sub-second transaction response times, strict data integrity, operational availability, and activity audit trails.
* **Business Rules (BRULE-01 to BRULE-07):** Validation blocking requests exceeding balances, mandatory rejection reasons, and balance deduction occurring strictly upon formal approval.

## Agile & Jira
Developed using an iterative Scrum methodology across planned Sprints:
* **Product Backlog:** Prioritized list of Epics, Features, User Stories, and Acceptance Criteria mapped in Jira.
* **Sprint 1 (11 Story Points):** Core employee workflow—User Login (US-01), View Leave Balance (US-02), and Submit Leave Request with validation (US-03).
* **Sprint 2 (15 Story Points):** Manager workflow—Review Queue (US-04), Approve Request (US-05), Reject Request with Reason (US-06), Status Tracking (US-07), and Event Notifications (US-08).
* **Jira Tracking:** Complete workflow governance (To Do $\rightarrow$ In Progress $\rightarrow$ Testing $\rightarrow$ Done) utilizing story points and MoSCoW priorities.

## System & Process Modeling
* **Process Flow Diagrams:** As-Is vs. To-Be workflows and Gap Analysis diagrams.
* **Swimlane Diagrams:** Operational hand-offs across Employee, Manager, HR, and System actors.
* **Use Case Diagram:** Structural map of 15 use cases across primary user roles.
* **System Context Diagram:** Boundary definitions linking core ELMS functionality to external actors and services.
* **Entity Relationship Diagram (ERD):** Relational schema definition across 9 core database entities.

## UI Prototype
Role-based Figma prototypes were developed to map user interactions prior to implementation:
* **Employee Portal:** Interactive dashboard displaying live balance cards, request submission forms, and historical logs.
* **Manager Command Center:** Pending approval queues, team calendar conflict overlays, and decision modals enforcing mandatory rejection feedback.
* **HR Administration:** Staff directory tables, entitlement quota editors, and policy setup modules.
* **Executive View:** High-level executive KPI cards and visual trend charts.

## SQL Analysis
A relational database (`ELMS_DB`) was architected in MySQL 8.0 containing 9 primary tables: `users`, `departments`, `employees`, `leave_types`, `leave_entitlements`, `leave_requests`, `leave_approvals`, `notifications`, and `leave_attachments`.

### Sample Query Highlights:
* **Dynamic Balance Calculation:** Joining entitlements and leave types to evaluate available days without storing redundant calculated values.
* **Manager Pending Queues:** Multi-table JOINs isolating pending requests by assigned manager ID.
* **Departmental Utilization:** Aggregating total approved leave days grouped by organizational department.
* **KPI Metrics:** Evaluating monthly leave consumption trends and manager decision ratios.

## Excel / Google Sheets Analysis
* **Data Preparation:** Raw leave record cleaning, duplicate removal, status standardization, and date format validation.
* **Formula Implementation:** Automated calculations using `SUMIF`, `COUNTIF`, `AVERAGE`, and multi-condition `IF` logic.
* **Pivot Table Summaries:** Department-level request counts, leave-type distribution splits, and monthly consumption trends.
* **Interactive Spreadsheets:** Formatted dashboards for rapid operational data review and collaborative stakeholder analysis.

## Power BI Dashboard
An interactive executive dashboard built on prepared leave datasets to deliver workforce intelligence:
* **Executive KPI Cards:** Total Requests, Total Leave Days, Pending Count, Approved Count, Rejected Count, and Approval Rate (%).
* **Departmental Analysis:** Clustered column charts mapping request volumes and total days taken per department.
* **Type & Status Breakdown:** Bar and donut charts illustrating requests across Annual, Sick, and Casual leave types and workflow states.
* **Temporal Trends:** Line charts tracking month-over-month leave day fluctuations to highlight seasonal absenteeism risks.
* **Cross-Filtering:** Global interactive slicers for Department, Leave Type, Status, Employee, and Date Range.

## UAT
User Acceptance Testing was planned and executed across 29 business test cases (TC-001 to TC-029):
* **Execution Metrics:** 25 Passed, 0 Failed, 4 Blocked (Pass Rate: 100% of executed tests).
* **Defect Log:** 4 infrastructure-dependent open/deferred defects logged (DEF-001: Backend File Storage API; DEF-002: Live SMTP Mail Server; DEF-003: Cron Scheduler for Year-End Rollover; DEF-004: Power BI Cloud Workspace Tenant License).
* **Outcome:** Conditionally accepted for production go-live pending final backend infrastructure integration.

## Key Business Insights
* **Operational Bottlenecks:** Tracking pending request queues highlights manager SLA performance and eliminates approval bottlenecks.
* **Capacity Planning:** Departmental breakdown identifies high-demand teams (e.g., IT and Finance) requiring proactive coverage scheduling prior to peak periods.
* **Burnout Prevention:** Categorizing workforce leave balances into Healthy, Medium, and Low categories enables HR to mitigate balance exhaustion risks.
* **Policy Compliance:** Standardizing rejection feedback ensures transparent governance and clear audit trails.

## BA Skills Demonstrated
* **Requirements Engineering:** Elicitation, analysis, MoSCoW prioritization, and traceability matrix maintenance.
* **Process Optimization:** As-Is mapping, Gap Analysis, and To-Be process design.
* **Agile Frameworks:** User story generation, acceptance criteria definition, backlog grooming, and Sprint execution.
* **Data Modeling & Analytics:** Relational schema design, SQL querying, Excel pivot modeling, and Power BI dashboard development.
* **Quality Assurance:** UAT test plan definition, scenario execution, defect tracking, and stakeholder sign-off orchestration.

## Tools Used
* **Requirements & Agile:** Jira, Confluence, Markdown
* **Diagramming & UX:** Draw.io, Figma
* **Data Analysis & Databases:** MySQL 8.0, Microsoft Excel, Google Sheets
* **Business Intelligence:** Microsoft Power BI
* **Documentation:** Google Docs / Workspace Suite

## Project Outcome
The ELMS portfolio project demonstrates a complete Business Analysis lifecycle. By translating ambiguous manual problems into clear functional specifications, structured database models, interactive UI wireframes, agile execution boards, and actionable business intelligence dashboards, the project proves how structured analysis delivers measurable operational value and executive transparency.
