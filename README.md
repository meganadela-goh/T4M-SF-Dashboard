ASM Trans4m 2.0 — Sales Design Status Dashboard
Version: 1.0
Workstream: Salesforce · Sales Track
Owner: Sales Functional Lead
Programme: Trans4m 2.0 (Salesforce, S4, Kinaxis, Teamcentre)

What is this?
A self-contained HTML dashboard for weekly PMO and stakeholder reporting on the Salesforce Sales Track. It provides an executive-level view of progress across three work item types — Design Blockers (Actions), User Stories (Requirements), and Development Tasks — grouped by area path.
The dashboard is a single .html file that runs in any browser with no server, login, or installation required.

How to use it
1. Open the dashboard
Double-click the .html file to open it in your browser, or host it via Netlify Drop, SharePoint, or any static web server for mobile access.
2. Load this week's CSV
Click "Choose CSV file" and select your latest export from Azure DevOps. The dashboard will populate immediately.
3. Load last week's CSV (optional)
Scroll to the Week-on-week changes section and click "Choose last week's CSV". The dashboard will automatically compare the two files and generate:

Summary tiles (open blockers, aligned, requirements, tasks)
A narrative of what was completed and aligned this week
A summary of what the team is currently working on


CSV format
Export from Azure DevOps with the following columns:
ColumnDescriptionIDWork item ID (used for transition matching)Work Item TypeMust be Action, Requirement, or TaskTitleWork item title (used as fallback match if IDs differ)Assigned ToAssignee nameStateCurrent state (e.g. New, In Analysis, In Review, Complete)TagsUsed to classify requirements (e.g. ASM to Review, ACN to Review)Area PathFull path e.g. Salesforce\2. CRM\2.1 Sales\Account Mgmt

Area paths supported
The dashboard recognises the following area paths automatically:

Account Mgmt
Opportunity Mgmt
Quote Mgmt
Order Mgmt
Product Mgmt
Reporting
Forecast Mgmt

Items not matching any of the above will be excluded from the area breakdown.

Work item types explained
TypeLabel in dashboardDescriptionAction⚡ Design BlockersOpen design items being discussed or resolved between ASM and ACNRequirementUser Story + ACFunctional requirements / user stories being designed and reviewedTaskDevelopment (Tasks)Development tasks raised against requirements

Status colour coding
StatusColourMeaningNewPurpleNot yet startedIn AnalysisAmberUnder functional designIn ReviewTealIn review / sign-off pendingOn HoldGreyPausedCancelledRedRemoved from scopeComplete / AlignedGreenClosed / agreedIn ProgressAmberActively being worked
Requirements tag logic
Requirements are classified by their Tags field rather than State:
TagColourMeaningASM to ReviewPurpleAwaiting ASM reviewACN to ReviewTealAwaiting ACN (Accenture) review(no tag)Dark purpleNew / not yet tagged

Week-on-week comparison
How it works
When you load both CSVs, the dashboard:

Matches items by ID first, then falls back to Title
Detects state changes between the two files
Identifies newly aligned blockers, closed user stories, and completed tasks
Reads current-week snapshot for active work (ACN to Review requirements + In Progress tasks)

Colour logic for tiles
TileGoes green whenGoes red whenOpen BlockersCount decreasesCount increasesAlignedCount increasesCount decreasesReq ClosedCount increasesNo change (stays neutral)Requirements / Tasks / TotalAlways neutral—

Weekly update process
Each week:

Export the latest Azure DevOps query to CSV (same columns as above)
Open the dashboard HTML in your browser
Click Load CSV → select this week's file
Click Choose last week's CSV → select the previous week's file
Screenshot the full dashboard for your PPO/PMO slide deck


Tip: Keep previous weekly CSV exports in a dated folder (e.g. exports/2026-04-16.csv) so you can always load the prior week for comparison.


Design system
This dashboard follows the ASM Trans4m 2.0 Design System:

Font: Inter (Google Fonts)
Primary colour: #4A1F5C (aubergine purple)
Action colour: #00B2A9 (teal)
Background: #FFFFFF / #F7F6F4 (white / off-white)
Fully responsive — works on desktop, tablet, and mobile


Dependencies
All dependencies are loaded via CDN — no installation required:

PapaParse 5.4.1 — CSV parsing
Inter — Typography (Google Fonts)


Support
Maintained by the Salesforce Sales Track functional lead as part of ASM Trans4m 2.0.
For questions contact the Salesforce workstream PMO.
