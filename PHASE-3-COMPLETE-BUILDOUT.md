# MERIDIAN PHASE 3 COMPLETE BUILDOUT PLAN
**Last Updated:** May 20, 2026 (Late Night)
**Source:** April 28, 2026 foundation + all subsequent additions

---

## 🎯 THE CORE THESIS - BUILD PLANNER IS THE PRODUCT

**Build Planner = scheduler + superintendent + PM + contract specialist + estimator in one engine.**

Every other module exists to feed it data:
- **Contracts** → COD/deliverables/LD rates
- **BOM** → quantities  
- **Locations** → site structure
- **Daily Reports** → actual progress
- **Materials** → inventory
- **Quality** → inspection data

No competitor (Procore, Buildertrend, Primavera P6) has this capability. This is the $50M acquisition target and the justification for GC pricing at $10K/month/project.

---

## 📋 PHASE 3A - FOUNDATION (Week 1-2)

### **1. Admin Module**
**Purpose:** Project-specific configuration, folder structure builder

**Features:**
- Project-level settings and configuration
- CSI MasterFormat folder structure builder
- Project team setup (roles, permissions)
- Module activation/deactivation per project
- Company branding customization
- Document template library setup
- Default values and preferences

**Why It's First:** Everything else needs project-specific configuration. This is the rails everything runs on.

---

### **2. Auto PDF Conversion & Filing System**
**Purpose:** Every completed item auto-files to correct location

**Features:**
- Automatic PDF generation from completed forms
- Smart filing to CSI MasterFormat folders
- Version control and audit trail
- Batch export capabilities
- File naming conventions (auto-generated)
- Tags and metadata assignment

**Strategic Importance:** This is the engine for CloseoutIQ. By substantial completion, 90% of turnover package is already built.

---

### **3. File Storage Infrastructure**
**Purpose:** Centralized, secure storage for all project files

**Supabase Storage Setup:**
- Bucket configuration and structure
- Organized hierarchy matching folder system
- File size limits and type validation
- Image compression (reduce storage costs)
- Automatic thumbnail generation

**File Management:**
- Drag-and-drop upload interface
- Multi-file upload support
- Progress indicators for large files
- File preview capability (view without downloading)
- Download individual or bulk folders
- Move/rename files (admin only)
- Search by name, type, date, uploader

**File Metadata:**
- Filename, size, type/extension
- Upload date/time and uploader
- Associated module/item (linked record)
- Version history
- Access log (who viewed/downloaded)

---

### **4. Contract & Deliverables Management**
**Purpose:** AI parsing of contracts → auto-extract deliverables → track to completion

**Contract Upload & Storage:**
- PDF upload with version control
- Contract metadata (parties, dates, value)
- Link to project milestones
- Contract document library

**AI-Powered Parsing (Claude API):**
Upload contract PDF → Claude extracts:
- Commercial Operation Date (COD)
- Substantial Completion Date
- Notice to Proceed (NTP) date
- Liquidated Damages rate ($/day)
- Payment milestones
- All deliverables with due dates
- Performance guarantees
- Warranty requirements

**Deliverables Tracking:**
- Auto-generated deliverables list from contract
- Status tracking (Not Started → In Progress → Submitted → Approved)
- Due date alerts (30/15/7/1 day warnings)
- Assignment to team members
- Upload deliverable files
- Owner approval workflow
- Link deliverables to turnover package
- Impact assessment: "3 deliverables overdue = can't achieve Substantial Completion"

**Change Order Management:**
- Track change orders that modify deliverables
- Version control (original vs. amended)
- Impact analysis: "CO #5 added 3 deliverables, extended 2 due dates"
- Change order approval workflow

**Why This Feeds Build Planner:** Contract dates (COD, NTP) and deliverables define the master schedule constraints.

---

### **5. Location Buildout System**
**Purpose:** Multi-tier site hierarchy with AI extraction from drawings

**Location Hierarchy:**
- **Project Level** - Overall site
- **Zone/Area Level** - Sections of site
- **Block Level** - Inverter blocks
- **Equipment Level** - Individual assets

**Location Management:**
- Create location tree (parent-child relationships)
- Drag-and-drop reorganization
- Bulk import from CSV
- Location-specific attributes:
  - GPS coordinates
  - Area (acres/square feet)
  - Equipment count
  - Status (mobilized, in progress, complete)
  - Lead crew assignment
  
**AI-Powered Location Extraction (Claude API):**
Upload site drawings → Claude extracts:
- Block names/numbers
- Equipment locations
- Distances between blocks
- Terrain features
- Auto-generates location tree

**Location-Based Views:**
- All modules filter by location
- Daily Reports by block
- Quality inspections by area
- Materials by location
- Equipment by block

**Heat Maps & Dashboards:**
- Color-coded status by block
- Completion percentage by zone
- Deficiency density by area

**Why This Feeds Build Planner:** Location structure defines work breakdown and sequencing.

---

## 📋 PHASE 3B - DOCUMENT MANAGEMENT (Week 3)

### **6. BOM Document Upload System**
**Purpose:** Replace URL-based document fields with actual file storage

**Features:**
- Replace "Document URL" fields with file upload
- Drag-and-drop interface
- Support multiple file types: PDF, Excel, CSV, images
- File preview capability
- Multiple files per BOM item
- Link files to specific BOM line items
- "View Documents" button per item
- Auto-link to Documents module

---

### **7. BOM Document Upload/Parsing (AI-Powered)**
**Purpose:** AI extracts quantities, part numbers, delivery dates from BOM PDFs/Excel

**AI Parsing (Claude API):**
Upload BOM PDF/Excel → Claude extracts:
- Part numbers
- Descriptions
- Quantities
- Unit prices (optional)
- Delivery dates
- Manufacturers
- Model numbers

**Manual Fallback:**
- If AI parsing fails → manual entry
- AI pre-fills 80% → user reviews/corrects

**BOM Integration:**
- Links to Material Requests
- Links to Deliveries tracking
- Links to Build Planner (quantities)
- Export to Excel

**Why This Feeds Build Planner:** BOM quantities drive auto-scheduling (quantity × hours per unit = duration).

---

### **8. Drawings Log**
**Purpose:** File upload/viewing system for project drawings

**Features:**
- Upload PDF/DWG files
- Drawing metadata:
  - Drawing number
  - Revision number
  - Drawing type (site plan, electrical, civil, etc.)
  - Issue date
  - Uploaded by
  - Status (For Review, Approved, Superseded)
- Drawing viewer (PDF inline preview)
- Version control (track revisions)
- Link drawings to locations
- Link drawings to RFIs/Submittals
- Download individual or bulk drawings

**Future Enhancement (Phase 3F):**
- Drawing Markup Tools (annotations, measurements)

---

### **9. Logistics Module Restructure (6 Tools)**

**Purpose:** Consolidate all material tracking into one module

**Tool 1: Parts List/BOM**
- Existing BOM functionality
- Enhanced with file uploads (from #6)
- AI parsing integration (from #7)

**Tool 2: Deliveries**
- Existing Deliveries functionality
- Track shipments, arrivals, status
- Link to BOM line items
- Excel export

**Tool 3: Material Requests (NEW)**
- Crew requests materials from warehouse/foreman
- Request form:
  - Location (where materials needed)
  - Material type (from BOM)
  - Quantity requested
  - Date needed
  - Requested by
  - Justification/reason
- Approval workflow (foreman approves)
- Status: Pending → Approved → Fulfilled → Denied

**Tool 4: Material Transfers (NEW)**
- Track materials moving between locations
- Transfer form:
  - From location
  - To location  
  - Material type
  - Quantity transferred
  - Transfer date
  - Reason (reallocation, return, etc.)
- Real-time inventory updates
- Audit trail (who moved what, when, why)

**Tool 5: Major Equipment**
- Existing Major Equipment functionality
- Track critical equipment (cranes, excavators, pile drivers)
- Link to Daily Reports
- Link to Build Planner (equipment dependencies)

**Tool 6: Construction Equipment Tracker**
- Track smaller equipment (generators, compressors, tools)
- Equipment inventory
- Equipment assignments
- Maintenance tracking

**Why Material Tracking Matters:**
- Prevents "you didn't give us enough materials" disputes
- Real-time inventory prevents LD exposure from running out before milestones
- Audit trail protects against theft/waste claims
- **This feature alone could sell Meridian - it's tangible ROI**

---

## 📋 PHASE 3C - QUALITY/QC (Week 4-5)

### **10. Quality Module Restructure**
**Purpose:** Split Quality/QC into 4 separate tools

**Tool 1: Inspections**
- Existing Inspections functionality
- Link to locations
- Link to Build Planner (inspection milestones)

**Tool 2: First Article Inspections (FAIs)**
- Existing FAI functionality
- Pre-production verification
- Link to BOM (equipment types)

**Tool 3: Deficiencies**
- Existing Deficiencies functionality
- Separate from Inspections for clarity
- Link to Constraint Dashboard

**Tool 4: Non-Conformance Reports (NCRs)**
- Existing NCR functionality
- Separate from Deficiencies for clarity
- Link to Constraint Dashboard

**Why This Matters:** Cognitive load reduction. Users know exactly where to go for each quality function.

---

### **11. QC Admin Portal**
**Purpose:** Customizable dropdowns for inspection types

**Features:**
- Admin interface for managing inspection templates
- Custom inspection categories:
  - Foundation inspections
  - Racking inspections
  - DC electrical inspections
  - AC electrical inspections
  - Module inspections
  - Torque inspections
- Add/edit/delete inspection types
- Define required fields per inspection type
- Set default values
- Template library

---

### **12. QC Template System**
**Purpose:** Pre-built templates by equipment type

**Templates Include:**
- Foundation Inspection Template
- Racking Inspection Template
- DC Electrical Inspection Template
- AC Electrical Inspection Template
- Module Inspection Template
- Torque Inspection Template
- Grounding Inspection Template

**Template Features:**
- Pre-populated field lists
- Equipment-specific pass/fail criteria
- Required photo locations
- Reference spec values (torque, embedment, etc.)
- Auto-link to BOM (equipment-specific tolerances)

---

### **13. Per-Item Photo Requirements**
**Purpose:** Configurable photo requirements per inspection item

**Features:**
- Define number of photos required per item type
- Photo angle requirements (overview, closeup, detail)
- Label requirements (equipment ID visible)
- Validation: Cannot submit inspection without required photos
- Photo metadata (timestamp, location, uploader)

---

### **14. Auto-Observation Trigger**
**Purpose:** Failed inspections auto-create safety observations

**Logic:**
- If inspection result = "Fail" → auto-create Safety Observation
- Link Observation to failed inspection
- Pre-fill Observation details from inspection
- Assign to responsible party
- Escalation alerts

---

### **15. Deficiencies Enhanced Template**
**Purpose:** Severity auto-calc, impact assessment

**Enhanced Fields:**
- Severity calculation based on:
  - Days overdue
  - Impact to COD
  - Safety risk level
- Impact assessment:
  - Affects milestone: Yes/No
  - LD exposure: $X if not resolved by [date]
  - Blocking other work: Yes/No
- Resolution tracking:
  - Corrective action plan
  - Resources needed
  - Estimated resolution date

---

### **16. NCRs Enhanced Template**
**Purpose:** Root cause analysis, corrective actions

**Enhanced Fields:**
- Root cause analysis (5 Whys method)
- Corrective action plan (immediate + long-term)
- Preventive action plan (prevent recurrence)
- Cost impact (rework, materials, labor)
- Schedule impact (days lost)
- Link to Contract (if impacts deliverables)
- Approval workflow (QC Manager → PM → Owner)

---

### **17. Overall Result Field Update**
**Purpose:** Replace "Partial" with "In Progress"

**Change:**
- Current: Pass / Fail / Partial
- New: Pass / Fail / In Progress

**Why:** "In Progress" is clearer than "Partial" - inspection is ongoing, not partially complete.

---

## 📋 PHASE 3D - SAFETY & CONSTRAINTS (Week 4-5)

### **18. Safety Module Restructure (7 Tools)**

**Purpose:** Consolidate Observations into comprehensive Safety module

**Tool 1: Incident Tracker**
- Record workplace incidents
- Injury details, severity, OSHA recordability
- Investigation findings
- Corrective actions
- Days lost tracking

**Tool 2: Observations**
- Existing Observations functionality
- Near-miss reporting
- Unsafe condition reporting
- Positive observations (safe behaviors)

**Tool 3: Toolbox Talks**
- Daily/weekly safety meetings
- Pre-built talk topics
- Attendance tracking
- Sign-off sheets
- Photo documentation

**Tool 4: Safety Certifications**
- Track worker certifications (OSHA 30, CPR, forklift, etc.)
- Expiration alerts
- Renewal tracking
- Badge printing

**Tool 5: JSA/JHA (Job Safety Analysis)**
- Task-specific hazard analysis
- Step-by-step risk assessment
- Mitigation measures
- Link to specific work activities

**Tool 6: Emergency Response**
- Emergency contact list
- Evacuation procedures
- First aid station locations
- Incident response protocols

**Tool 7: Safety Stand-Down Tracker**
- Track safety stand-downs (work stoppages)
- Reason for stand-down
- Duration
- Resolution
- Lessons learned

**Why This Matters:** Comprehensive safety management in one place. Prevents OSHA violations and reduces liability.

---

### **19. Constraint Dashboard**
**Purpose:** Executive view of all project blockers

**Consolidates:**
- Deficiencies (from Quality module)
- NCRs (from Quality module)
- Action Items (standalone tool)
- Safety Observations (if critical)

**Dashboard Features:**
- Color-coded by severity (red/yellow/green)
- Filter by:
  - Type (Deficiency/NCR/Action Item)
  - Location
  - Responsible party
  - Due date
  - Impact to COD
- Sort by priority
- Bulk actions (assign, close, escalate)
- Export to Excel

**Why This Matters:** PM sees all blockers in one place. Prevents things from falling through cracks.

---

### **20. Action Items**
**Purpose:** Standalone task tracking separate from Constraints

**Features:**
- Create action items from any module
- Link to source (RFI, Meeting, Observation, etc.)
- SMART goal framework:
  - Specific description
  - Measurable outcome
  - Assigned to
  - Realistic deadline
  - Time-bound (due date)
- Priority levels (Low/Medium/High/Critical)
- Status tracking (Not Started → In Progress → Blocked → Complete)
- Recurring action items (weekly safety walks)
- Notifications (due date reminders)

**Integration:**
- Link to RFIs/Submittals
- Link to Meeting Minutes
- Link to Observations
- Link to Deficiencies/NCRs
- Show on Constraint Dashboard if critical

---

## 📋 PHASE 3E - MODULE ENHANCEMENTS (Week 5)

### **21. Crew/Subs Management**
**Purpose:** Track crews, subcontractors, labor resources

**Crew Management:**
- Create crew records (crew name, foreman, size)
- Crew assignments to locations
- Crew schedules
- Production rates by crew
- Link to Daily Reports

**Subcontractor Management:**
- Subcontractor database (company, contact, trade)
- Subcontract details (scope, value, dates)
- Payment applications
- Certificate of Insurance (COI) tracking
- Performance ratings

**Labor Tracking:**
- Headcount by day
- Labor hours by trade
- Labor cost tracking
- Link to Build Planner (labor resource allocation)

---

### **22. RFI/Submittal Email Threading**
**Purpose:** Hybrid internal/external email system

**Email Integration:**
- Unique email address per RFI/Submittal
- External parties can reply via email
- Email replies automatically thread to item
- Email notifications to internal team
- Attachment handling
- Spam filtering

**Internal Messaging:**
- Internal team can respond in-platform
- Comment threading
- @mentions
- Notification system

**Why Complex:** Email deliverability, threading logic, spam filtering. Consider Phase 4 if beta feedback doesn't demand it.

---

### **23. Daily Reports Template System**
**Purpose:** Pre-built templates for different report types

**Templates:**
- Standard Daily Report (weather, production, crew, equipment, issues)
- Commissioning Daily Report (testing, energization, startup)
- Punchlist Walk Report (deficiencies found, photos)
- Quality Inspection Report (inspections completed today)
- Safety Report (incidents, observations, toolbox talks)

**Template Features:**
- Pre-populated field lists
- Required fields per template type
- Custom templates (admin creates)
- Clone templates (start from existing)

---

### **24. Documents Module Enhancements**
**Purpose:** Enhanced document management system

**Enhancements:**
- CSI MasterFormat folder structure (50 divisions)
- Document metadata (tags, categories, keywords)
- Advanced search (full-text search within PDFs)
- Version control (track document revisions)
- Approval workflows (review → approve → publish)
- Document expiration dates (re-certification required)
- Related documents (link contracts, drawings, specs)

---

## 📋 PHASE 3F - BUILD PLANNER & SCHEDULE (Week 6-7)

### **🏆 BUILD PLANNER - THE FLAGSHIP PRODUCT**

**Already Built (Phase 2 Tier 2):**
- ✅ What-If COD Calculator
- ✅ Daily Reports Feedback Loop
- ✅ Recovery Plan Generator
- ✅ Extreme Weather Toggle

---

### **25. Build Planner: Construction Readiness Index (CRI)**
**Purpose:** 0-100% score showing mobilization readiness

**CRI Components:**
- Contract signed? (Yes = 15%)
- NTP received? (Yes = 15%)
- Permits obtained? (Yes = 15%)
- Site access secured? (Yes = 10%)
- Materials on order? (Yes = 10%)
- Equipment secured? (Yes = 10%)
- Crew mobilized? (Yes = 10%)
- Drawings approved? (Yes = 10%)
- Insurance/bonds in place? (Yes = 5%)

**CRI Display:**
- Dashboard widget showing current score
- Color-coded (0-50% red, 51-75% yellow, 76-100% green)
- Checklist view (what's missing)
- Trend over time (is readiness improving?)

---

### **26. Build Planner: Industry Standards Library**
**Purpose:** Pre-loaded man-hours per task benchmarks

**Industry Standards Data:**
- Foundation installation: X hours per pile
- Racking installation: X hours per row
- Module installation: X hours per module
- DC electrical: X hours per string
- AC electrical: X hours per inverter
- Grounding: X hours per block
- Testing/commissioning: X hours per MW

**Data Sources:**
- NREL Solar Cost Benchmarks
- NECA Electrical Standards
- RSMeans Construction Data
- Internal benchmarks from beta customers

**Customization:**
- Admin can edit standards per project type
- Override standards for specific projects
- Add custom task types with custom hours

---

### **27. Build Planner: Quantity-Based Auto-Scheduling**
**Purpose:** BOM quantities × hours per unit = realistic timeline

**Auto-Scheduling Logic:**
```
BOM Quantity × Industry Standard Hours = Total Task Duration

Example:
- 50,000 modules in BOM
- Industry Standard: 0.15 hours per module
- Total Task Duration: 7,500 labor hours
- Crew Size: 25 workers
- Calendar Duration: 7,500 hours ÷ (25 workers × 8 hours/day) = 37.5 days
```

**Inputs:**
- BOM quantities (from BOM module)
- Industry standards (from Standards Library)
- Crew size (from Crew Management)
- Work schedule (5-day week? 6-day? 7-day?)

**Outputs:**
- Task durations (days per activity)
- Start/end dates per task
- Milestone dates
- COD forecast
- Critical path

**Adjustments:**
- Change crew size → durations recalculate
- Change work schedule → durations recalculate
- Change quantities → durations recalculate

---

### **28. Build Planner: Cost Calculation Engine**
**Purpose:** Labor rate × hours = project cost (with $/W DC)

**Cost Calculations:**
```
Labor Cost = Labor Hours × Labor Rate
Material Cost = BOM Line Items × Unit Prices
Equipment Cost = Equipment Days × Daily Rates
Subcontractor Cost = Subcontract Values
Total Project Cost = Labor + Material + Equipment + Subs

$/W DC = Total Project Cost ÷ Project Size (MW DC) ÷ 1,000
```

**Cost Tracking:**
- Budget vs. Actual
- Cost variance by phase
- Forecasted total cost
- Cost per milestone
- Cost impact of delays (overtime, acceleration)

**Alerts:**
- Budget overruns
- Cost trending above forecast
- $/W DC above target

---

### **29. Build Planner: Premium AI Tier (Claude API Integration)**
**Purpose:** AI reads PDFs and auto-populates planner

**This is THE DIFFERENTIATOR. No competitor has this.**

**AI Feature 1: Auto-Populate from Drawings**
- Upload site drawings (PDF)
- Claude API extracts:
  - Block layout and names
  - Equipment locations
  - Distances between areas
  - Terrain features
- Auto-generates location tree
- Auto-populates Build Planner structure

**AI Feature 2: Auto-Populate from BOM**
- Upload BOM (PDF/Excel)
- Claude API extracts:
  - Quantities (modules, inverters, trackers, etc.)
  - Part numbers
  - Delivery dates
- Auto-populates Material List
- Auto-populates Build Planner quantities

**AI Feature 3: Auto-Populate from Contract**
- Upload EPC contract (PDF)
- Claude API extracts:
  - COD date
  - Substantial Completion date
  - NTP date
  - Liquidated damages rate
  - Milestone dates
  - Deliverables with deadlines
- Auto-populates Contract Deliverables tracker
- Auto-populates Build Planner constraints

**Pricing:**
- Base Meridian: $10K/month
- Build Planner Premium AI: +$2K/month
- Quality AI Premium (InspectionIQ): +$2K/month
- **Total with Dual AI: $14K/month**

---

### **30. Build Planner: Dynamic Adjustment Engine**
**Purpose:** Change any variable → instant recalculation across entire project

**This is THE KILLER FEATURE.**

**What Recalculates:**
- All task dates
- All milestone dates
- COD forecast
- LD exposure
- Labor costs
- Resource requirements
- Critical path
- Deliverable due dates

**Example Scenarios:**

**Scenario 1: COD Moves Earlier**
- User changes COD from June 15 → May 30 (15 days earlier)
- System instantly shows:
  - 8 deliverables now overdue
  - Labor cost increases 18% (overtime required)
  - LD exposure: $0 → $450K if missed
  - 3 subcontracts need acceleration clauses
  - Crew size must increase from 25 → 35

**Scenario 2: NTP Delayed**
- NTP delayed 2 weeks
- System recalculates:
  - All downstream dates shift
  - COD at risk (highlight in red)
  - LD exposure increases
  - Deliverable deadlines adjust
  - Recovery plan auto-generates

**Scenario 3: Crew Size Changes**
- Reduce crew from 30 → 20 workers
- System recalculates:
  - Task durations extend
  - Critical path shifts
  - COD forecast moves out
  - LD exposure increases
  - Cost per day decreases (fewer workers) but total cost increases (longer duration)

**Why No Competitor Has This:**
- Procore: Static schedules, manual updates
- Buildertrend: Template-based, no intelligence
- Primavera P6: Complex, manual, no AI
- **Meridian: Real-time recalculation across entire project**

---

### **31. Build Planner: Proprietary Learning Loop**
**Purpose:** AI shifts from industry standards to YOUR company's historical data

**How It Works:**
1. **Phase 1 (Project 1):** System uses industry standard benchmarks
2. **Phase 2 (Project 2-5):** System tracks actual production rates from Daily Reports
3. **Phase 3 (Project 6+):** System learns YOUR crew's production rates:
   - Your racking crew installs 150 rows/day (vs. industry 120 rows/day)
   - Your module crew installs 400 modules/day (vs. industry 300 modules/day)
4. **Phase 4 (Project 10+):** System auto-adjusts ALL future estimates based on YOUR historical data

**Competitive Moat:**
- Procore/P6/Buildertrend: No learning capability
- **Meridian: Gets smarter with every project**
- After 10-20 projects, Meridian knows YOUR company better than you do
- Data advantage compounds over time
- Cannot be replicated without full data infrastructure

---

### **32. Schedule Module Enhancement (P6 Visual Patterns)**
**Purpose:** Professional schedule visualization

**P6-Style Features:**

**1. Multiple Baseline Overlays**
- Project Baseline (original plan)
- Primary Baseline (current approved plan)
- Secondary Baseline (alternative scenario)
- Tertiary Baseline (historical comparison)
- All overlaid on Gantt chart for comparison

**2. Critical Path Highlighting**
- Red bars for critical path activities
- Black bars for non-critical activities
- Auto-calculate critical path based on dependencies

**3. Driving vs. Non-Driving Relationship Lines**
- Solid lines for driving relationships (affects successor dates)
- Dotted lines for non-driving relationships (informational)
- Color coding: Red (critical), Black (non-critical)

**4. Multiple Timescales**
- Week/Day view
- Month/Week view
- Quarter/Month view
- Year/Month view
- Hourly intervals (for commissioning)

**5. Non-Working Time Shading**
- Weekends shaded gray
- Holidays shaded differently
- Weather delay days shaded

**6. Progress Spotlight**
- Highlight tasks with recent updates
- Show variance from baseline

**7. Direct Gantt Editing**
- Drag bars to adjust duration
- Update status inline (% complete)
- Drag dependency lines to create links

**Integration:**
- Build Planner = "Schedule Engine" (generates the schedule)
- Schedule Module = "Living Canvas" (displays, interacts, updates)
- Build Planner lives INSIDE Schedule module as AI planning agent
- Toggle bar shows/hides Build Planner panel

---

### **33. Drawings: Markup Tools**
**Purpose:** Annotate and measure drawings

**Markup Features:**
- Draw shapes (rectangles, circles, arrows)
- Text annotations
- Freehand drawing
- Measurement tools (distance, area)
- Stamp tools (approved, rejected, see note)
- Color picker
- Layer management

**Collaboration:**
- Multiple users can markup simultaneously
- Markup history (who added what, when)
- Comments on markups
- Resolve/close markups

**Export:**
- Export marked-up drawing as PDF
- Email marked-up drawing
- Link markups to RFIs

**Consideration:** Users already have Bluebeam ($349/year). May defer to Phase 4 based on beta feedback.

---

## 📋 PHASE 3G - UX & ANALYTICS (Week 8)

### **34. Interconnection: Commissioning Readiness Checklist**
**Purpose:** Track pre-commissioning requirements

**Checklist Items:**
- All modules installed and tested
- DC electrical complete and tested
- AC electrical complete and tested
- Grounding complete and tested
- SCADA system operational
- Utility interconnection agreement signed
- AHJ final inspection passed
- Insurance certificates submitted
- O&M manuals delivered
- Commissioning plan approved

**Dashboard:**
- Color-coded checklist (green/yellow/red)
- Completion percentage
- Estimated commissioning date
- Link to Contract Deliverables

---

### **35. Response Time Analytics Dashboard**
**Purpose:** Track RFI/Submittal/Deficiency response times

**Metrics Tracked:**
- Average response time by type
- Response time by responsible party
- Overdue items count
- Trend over time (improving or degrading?)
- Comparison to project targets

**Dashboards:**
- RFI Response Times: Submitted → Answered
- Submittal Response Times: Submitted → Approved/Rejected
- Deficiency Response Times: Identified → Resolved

**Alerts:**
- Items overdue by >7 days
- Response times trending above target
- Specific parties consistently slow

---

### **36. Push Notification & Email Alert System**
**Purpose:** Real-time notifications for critical events

**Notification Triggers:**
- New RFI assigned to you
- Submittal requires your review
- Deficiency assigned to you
- Action Item due in 24 hours
- Contract deliverable due in 7 days
- Inspection failed (auto-observation created)
- Material Request pending your approval
- Safety incident reported
- COD at risk (LD exposure > $X)

**Notification Channels:**
- In-app notifications (bell icon)
- Email notifications
- SMS notifications (optional, premium)
- Push notifications (mobile app)

**User Preferences:**
- Customize which events trigger notifications
- Set quiet hours (no alerts 10pm-7am)
- Batch daily digest option

---

### **37. Confirmation Modals & Validation**
**Purpose:** Prevent accidental deletions and errors

**Confirmation Modals:**
- Delete confirmations (are you sure?)
- Irreversible action warnings
- Duplicate entry warnings
- Form validation errors
- Unsaved changes warnings

**Field Validation:**
- Required field indicators
- Date format validation
- Number range validation
- File type validation
- Cross-field validation (start date < end date)

---

### **38. Empty State Enhancements**
**Purpose:** Guide users when modules are empty

**Empty State Designs:**
- Illustrative graphics (not just "No data")
- Action-oriented CTAs ("Create your first RFI")
- Helpful tips ("RFIs track questions to designers/engineers")
- Quick-start guides
- Sample data option (load demo data)

---

### **39. Toast Notifications**
**Purpose:** Transient success/error messages

**Toast Types:**
- Success: "RFI #42 created successfully"
- Error: "Failed to upload file. Try again."
- Warning: "This action cannot be undone"
- Info: "Export started. You'll receive an email when ready."

**Toast Features:**
- Auto-dismiss after 3-5 seconds
- Manual dismiss (X button)
- Action buttons ("View RFI", "Undo")
- Stack multiple toasts
- Position: top-right corner

---

## 📋 PHASE 3H - OPTIONAL/PHASE 4

### **40. Permitting: Visual Regulatory Alerts**
**Purpose:** Visual indicators for permit status

**Visual Enhancements:**
- Color-coded permit cards (red/yellow/green)
- Timeline view (permit application → approval)
- Dependency visualization (permit A blocks permit B)
- Jurisdiction-specific workflows

**Consider Phase 4:** Low priority unless beta feedback demands it.

---

### **41. Daily Reports: Equipment Delivery Integration**
**Purpose:** Link Daily Reports to BOM equipment status

**Integration:**
- Show equipment arrival delays in Daily Reports
- Link to BOM equipment records
- Alert if equipment delay impacts today's work
- Auto-update Build Planner critical path

**Why This Matters:** NOT an edge case. This is core feedback loop that keeps schedule live and current.

---

### **42. CloseoutIQ Integration**
**Purpose:** Standalone product that integrates with Meridian

**Auto-Dossier Feature:**
- OCR scans all filed PDFs
- Tags by Inverter ID, Block, Equipment Type
- Organizes into CSI MasterFormat folders
- "Export to O&M" button generates final book

**O&M Vault Subscription:**
- Post-construction document hosting
- $5K-$10K Exit Fee for Final Book Generation
- Recurring revenue model

**Phase 4 or Standalone:** CloseoutIQ is separate product. May integrate later.

---

## 🎯 BUILD SEQUENCE SUMMARY

**Week 1-2:** Foundation (Admin, PDF Filing, File Storage, Contracts, Locations)

**Week 3:** Documents & Materials (BOM, Drawings, Logistics Module)

**Week 4-5:** Quality & Safety (Quality Module, QC Portal, Safety Module, Constraint Dashboard)

**Week 6-7:** BUILD PLANNER - THE FLAGSHIP (CRI, Industry Standards, Auto-Scheduling, Cost Engine, Premium AI, Dynamic Adjustment, Learning Loop)

**Week 8:** Schedule Integration & Polish (P6 visuals, Build Planner integration, Daily Reports, Analytics, UX improvements)

**Phase 4 (Post-Beta):** Email threading, Drawing markup, Equipment integration, CloseoutIQ

---

## 💡 STRATEGIC PRIORITIES

**Tier 1 (Must Build - Critical for Beta):**
- Everything in Weeks 1-5 (Foundation, Documents, Quality, Safety)
- Build Planner core features (Weeks 6-7)

**Tier 2 (Should Build - Enhances Beta):**
- Build Planner Premium AI
- Schedule P6 visuals
- Analytics dashboards
- UX polish

**Tier 3 (Can Wait - Post-Beta):**
- Email threading (complex)
- Drawing markup (users have Bluebeam)
- CloseoutIQ integration (separate product)

---

## 🔥 THE TRUTH

**Build Planner isn't just a feature - it's THE PRODUCT.**

Everything else supports it:
- Contracts → feed deliverables and COD
- BOM → feeds quantities
- Locations → feeds structure
- Daily Reports → feeds actual progress
- Materials → feeds inventory
- Quality → feeds inspection data

**Build Planner is the brain. Everything else is the nervous system feeding it data.**

**This is the exit strategy. This is the $50M acquisition. This is why GCs pay $10K-$14K/month/project for Meridian.**

---

*End of Phase 3 Complete Buildout Plan*
*Last Updated: May 20, 2026 - Late Night*
*Source: April 28, 2026 foundation + all subsequent additions*
