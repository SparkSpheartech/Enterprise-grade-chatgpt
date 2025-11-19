# Synthetic Data for California Fiber Outage - Obsidian Web Graph

## Scenario Overview
**Date:** November 17, 2024  
**Location:** San Francisco & Oakland, California  
**Root Cause:** Fiber line cut by CalTrans Construction Inc during highway expansion work  
**Duration:** 5.25 - 8.5 hours  
**Total Customers Affected:** 4,991 (Residential: 4,370, Business: 598, Internal: 23)

## Data Files Generated

### 1. **01_OUTAGE_EVENTS.csv** (5 outage events)
Primary outage tracking data showing the main incident and related sub-incidents.

**Key Fields:**
- `Outage_Event_ID` - Primary Key
- `NOC_Ticket_ID` - Foreign Key → NOC_OPERATORS
- `Network_Engineer_ID` - Foreign Key → NETWORK_ENGINEERS
- `Repair_Crew_ID` - Foreign Key → REPAIR_CREWS
- `Construction_Company` - Foreign Key → CONSTRUCTION_COMPANIES
- `Fiber_Cable_ID` - Foreign Key → FIBER_INFRASTRUCTURE
- `CLLI` - Foreign Key → CLLI_LOCATIONS

**Outage Events:**
- OUT-2024-CA-001: Gigabit Fiber residential (2,847 customers, 8.5 hours)
- OUT-2024-CA-002: Business Fiber 500 (412 customers, 8.5 hours)
- OUT-2024-CA-003: Internal Network (23 employees, 8.5 hours)
- OUT-2024-CA-004: Gigabit Fiber residential secondary (1,523 customers, 5.25 hours)
- OUT-2024-CA-005: Business Fiber 1Gig secondary (186 customers, 5.25 hours)

---

### 2. **02_CUSTOMER_INTERACTIONS.csv** (50 interactions)
Customer service interactions during the outage including phone calls, chat, SMS, and IVR contacts.

**Key Fields:**
- `InteractionId` - Primary Key
- `UCID` - Foreign Key → CUSTOMERS
- `ACCT_NO` - Foreign Key → CUSTOMERS
- `Outage_Event_ID` - Foreign Key → OUTAGE_EVENTS
- `AgentName` - Foreign Key → AGENTS
- `AgentSupervisor` - Foreign Key → SUPERVISORS
- `TRANSCRIPT_ID` - Unique identifier for conversation transcripts

**Interaction Channels:**
- Phone: 28 interactions
- Chat: 8 interactions
- SMS: 8 interactions
- IVR: 6 interactions

**Customer Satisfaction Metrics:**
- NPS scores ranging from 2-6
- OSAT scores ranging from 3-7
- Issue resolution tracking
- Multiple contact tracking

---

### 3. **03_NOC_OPERATORS.csv** (3 operators)
Network Operations Center staff who managed the incident response.

**Key Fields:**
- `NOC_Operator_ID` - Primary Key
- `NOC_Ticket_ID` - Foreign Key → OUTAGE_EVENTS
- Experience levels, certifications, and response actions

**Operators:**
- NOC-OPR-001: James Rodriguez (Senior, Level 3)
- NOC-OPR-002: Maria Thompson (Senior, Level 3)
- NOC-OPR-003: David Chen (Lead, Level 4) - Lead operator

---

### 4. **04_NETWORK_ENGINEERS.csv** (3 engineers)
Network engineers who performed technical analysis and restoration coordination.

**Key Fields:**
- `Network_Engineer_ID` - Primary Key
- `NOC_Ticket_ID` - Foreign Key → OUTAGE_EVENTS
- `Fiber_Cable_ID` - Foreign Key → FIBER_INFRASTRUCTURE
- Root cause analysis and technical actions

**Engineers:**
- ENG-CA-001: Robert Martinez (GPON specialist, 12 years exp)
- ENG-CA-002: Jennifer Wong (GPON specialist, 9 years exp)
- ENG-CA-003: Michael Patel (Core Network specialist, 15 years exp)

---

### 5. **05_REPAIR_CREWS.csv** (3 crews)
Field technician crews who performed physical fiber repairs.

**Key Fields:**
- `Repair_Crew_ID` - Primary Key
- `NOC_Ticket_ID` - Foreign Key → OUTAGE_EVENTS
- `Fiber_Cable_ID` - Foreign Key → FIBER_INFRASTRUCTURE
- `Splice_Point_ID` - Foreign Key → SPLICE_POINTS
- Detailed repair activities and materials used

**Crews:**
- CREW-CA-NOR-012: Thomas Anderson (4 technicians, 144-strand splice)
- CREW-CA-NOR-013: Sarah Mitchell (3 technicians, 96-strand splice)
- CREW-CA-NOR-014: Marcus Williams (2 technicians, conduit repair)

---

### 6. **06_AGENTS.csv** (10 agents)
Customer service agents who handled customer interactions.

**Key Fields:**
- `Agent_ID` - Primary Key
- `AgentName` - Used in CUSTOMER_INTERACTIONS
- `AgentSupervisor` - Foreign Key → SUPERVISORS
- Performance metrics and specializations

**Agent Distribution:**
- Technical Support (Residential): 5 agents
- Business Support: 5 agents

---

### 7. **07_SUPERVISORS.csv** (3 supervisors)
Supervisors overseeing customer service teams and incident response.

**Key Fields:**
- `Supervisor_ID` - Primary Key
- `Supervisor_Name` - Used in AGENTS and CUSTOMER_INTERACTIONS
- Team management and escalation responsibilities

**Supervisors:**
- Michael Torres: Residential Technical Support (12 agents)
- Robert Kim: Business Support (8 agents)
- IT Director: Internal IT Operations (5 staff)

---

### 8. **08_FIBER_INFRASTRUCTURE.csv** (5 fiber cables)
Physical fiber optic cable infrastructure details.

**Key Fields:**
- `Fiber_Cable_ID` - Primary Key
- `Start_CLLI` / `End_CLLI` - Foreign Keys → CLLI_LOCATIONS
- `Splice_Points` - Foreign Keys → SPLICE_POINTS
- `Associated_Outages` - Foreign Keys → OUTAGE_EVENTS

**Cables:**
- FBR-CA-SNFC-TRUNK-A01: Main trunk (144 fibers, 12.3 miles) - **DAMAGED**
- FBR-CA-SNFC-TRUNK-A02: Secondary trunk (96 fibers, 8.7 miles) - **DAMAGED**
- FBR-CA-SNFC-TRUNK-B01: Backup trunk (288 fibers, 15.8 miles) - Redundancy
- FBR-CA-SNFC-TRUNK-B02: Backup trunk (144 fibers, 11.2 miles) - Redundancy
- FBR-CA-INTERNAL-01: Corporate network (48 fibers, 3.4 miles) - **DAMAGED**

---

### 9. **09_CONSTRUCTION_COMPANIES.csv** (1 company)
Construction company responsible for the line cut.

**Key Fields:**
- `Construction_Company_ID` - Primary Key
- `NOC_Ticket_ID` - Foreign Key → OUTAGE_EVENTS
- Liability and incident details

**Company:**
- CalTrans Construction Inc (Poor 811 compliance, 3 previous incidents)
- Repair cost estimate: $284,500
- Status: Under investigation

---

### 10. **10_CUSTOMERS.csv** (22 customers)
Detailed customer account information.

**Key Fields:**
- `UCID` - Primary Key (Unique Customer ID)
- `ACCT_NO` - Primary Key (Account Number)
- `Connected_CLLI` - Foreign Key → CLLI_LOCATIONS
- Customer demographics, service details, and billing information

**Customer Breakdown:**
- Residential: 16 customers (various service bundles)
- Business: 6 customers (SMB and Enterprise)
- Internal: 2 internal IT accounts

---

### 11. **11_SPLICE_POINTS.csv** (9 splice points)
Physical fiber splice locations along cable routes.

**Key Fields:**
- `Splice_Point_ID` - Primary Key
- `Fiber_Cable_ID` - Foreign Key → FIBER_INFRASTRUCTURE
- `Repair_Crew_ID` - Foreign Key → REPAIR_CREWS
- GPS coordinates, damage assessment, repair details

**Critical Splice Points:**
- SP-2847: **DESTROYED** - Primary damage (144 fibers)
- SP-1523: **DAMAGED** - Secondary damage (96 fibers)
- CONDUIT-SNFC-01: **DESTROYED** - Underground conduit

---

### 12. **12_CLLI_LOCATIONS.csv** (7 locations)
Central Office and facility locations (CLLI codes).

**Key Fields:**
- `CLLI_Code` - Primary Key
- `Connected_CLLIs` - Foreign Keys → Other CLLI_LOCATIONS
- `Affected_By_Outage` - Boolean indicator
- Facility details, equipment, and connectivity

**Locations:**
- SNFCCA01: San Francisco Central Office - **AFFECTED** (2,847 customers)
- SNFCCA02: SF Secondary CO - **AFFECTED** (1,709 customers)
- SNFCCA03-05: Backup and operations facilities
- OKLDCA01, SNJSCA01: Distribution hubs (not affected)

---

### 13. **13_INCIDENT_TIMELINE.csv** (28 timeline events)
Chronological sequence of events during the incident from detection to resolution.

**Key Fields:**
- `Timeline_ID` - Primary Key
- `Outage_Event_ID` - Foreign Key → OUTAGE_EVENTS
- `Actor_ID` - Foreign Key → Various tables (NOC, Engineers, Crews, Customers)
- `System_Component` - Foreign Key → FIBER_INFRASTRUCTURE, NETWORK_EQUIPMENT

**Key Milestones:**
- 06:15:00 - Outage start (fiber severed)
- 06:17:32 - NOC response initiated
- 07:15:00 - First crew arrives on site
- 07:45:00 - Repair work begins
- 11:30:00team_packet_weave - Secondary trunk restored (1,709 customers)
- 14:45:00 - Primary trunk restored (2,847 customers)
- 14:52:18 - Incident closed

---

### 14. **14_NETWORK_EQUIPMENT.csv** (11 network devices)
Network equipment deployed at CLLI locations.

**Key Fields:**
- `Equipment_ID` - Primary Key
- `Location_CLLI` - Foreign Key → CLLI_LOCATIONS
- `Connected_Fiber_Cables` - Foreign Keys → FIBER_INFRASTRUCTURE
- `Outage_Event_ID` - Foreign Key → OUTAGE_EVENTS

**Equipment Types:**
- OLT (Optical Line Terminals): 7 devices
- Core Routers: 2 devices
- Switches: 2 devices
- DWDM: 1 device

---

## Relationships for Obsidian Graph

### Primary Entity Relationships

```
OUTAGE_EVENTS (center node)
├── CUSTOMERS (via Affected_Customers count & CLLI)
│   └── CUSTOMER_INTERACTIONS (via UCID, ACCT_NO, Outage_Event_ID)
│       ├── AGENTS (via AgentName)
│       │   └── SUPERVISORS (via AgentSupervisor)
│       └── TRANSCRIPT_ID (unique conversation threads)
│
├── FIBER_INFRASTRUCTURE (via Fiber_Cable_ID)
│   ├── SPLICE_POINTS (via Splice_Point_ID in fiber)
│   │   └── REPAIR_CREWS (via Repair_Crew_ID)
│   ├── CLLI_LOCATIONS (via Start_CLLI, End_CLLI)
│   │   ├── NETWORK_EQUIPMENT (via Location_CLLI)
│   │   └── CUSTOMERS (via Connected_CLLI)
│   └── NETWORK_EQUIPMENT (via Connected_Fiber_Cables)
│
├── NOC_OPERATORS (via NOC_Ticket_ID)
│   └── INCIDENT_TIMELINE (via Actor_ID)
│
├── NETWORK_ENGINEERS (via Network_Engineer_ID)
│   ├── FIBER_INFRASTRUCTURE (via Fiber_Cable_ID)
│   └── INCIDENT_TIMELINE (via Actor_ID)
│
├── REPAIR_CREWS (via Repair_Crew_ID)
│   ├── SPLICE_POINTS (via Splice_Point_ID)
│   └── INCIDENT_TIMELINE (via Actor_ID)
│
├── CONSTRUCTION_COMPANIES (via Construction_Company)
│   └── Root cause attribution
│
└── INCIDENT_TIMELINE (via Outage_Event_ID)
    └── Links all actors and systems chronologically
```

### Key Foreign Key Relationships

| From Table | Field | To Table | Field |
|------------|-------|----------|-------|
| CUSTOMER_INTERACTIONS | Outage_Event_ID | OUTAGE_EVENTS | Outage_Event_ID |
| CUSTOMER_INTERACTIONS | UCID | CUSTOMERS | UCID |
| CUSTOMER_INTERACTIONS | ACCT_NO | CUSTOMERS | ACCT_NO |
| CUSTOMER_INTERACTIONS | AgentName | AGENTS | AgentName |
| OUTAGE_EVENTS | Fiber_Cable_ID | FIBER_INFRASTRUCTURE | Fiber_Cable_ID |
| OUTAGE_EVENTS | NOC_Ticket_ID | NOC_OPERATORS | NOC_Ticket_ID |
| OUTAGE_EVENTS | Network_Engineer_ID | NETWORK_ENGINEERS | Network_Engineer_ID |
| OUTAGE_EVENTS | Repair_Crew_ID | REPAIR_CREWS | Repair_Crew_ID |
| OUTAGE_EVENTS | CLLI | CLLI_LOCATIONS | CLLI_Code |
| FIBER_INFRASTRUCTURE | Start_CLLI | CLLI_LOCATIONS | CLLI_Code |
| FIBER_INFRASTRUCTURE | End_CLLI | CLLI_LOCATIONS | CLLI_Code |
| SPLICE_POINTS | Fiber_Cable_ID | FIBER_INFRASTRUCTURE | Fiber_Cable_ID |
| SPLICE_POINTS | Repair_Crew_ID | REPAIR_CREWS | Repair_Crew_ID |
| CUSTOMERS | Connected_CLLI | CLLI_LOCATIONS | CLLI_Code |
| AGENTS | AgentSupervisor | SUPERVISORS | Supervisor_Name |
| NETWORK_EQUIPMENT | Location_CLLI | CLLI_LOCATIONS | CLLI_Code |
| NETWORK_EQUIPMENT | Connected_Fiber_Cables | FIBER_INFRASTRUCTURE | Fiber_Cable_ID |
| INCIDENT_TIMELINE | Outage_Event_ID | OUTAGE_EVENTS | Outage_Event_ID |
| INCIDENT_TIMELINE | Actor_ID | Multiple Tables | Various ID fields |

---

## Graph Visualization Recommendations

### Node Types & Colors
- **Outage Events** (Red) - Central incident nodes
- **Customers** (Blue) - Affected customer accounts
- **Agents/NOC/Engineers** (Green) - Human responders
- **Infrastructure** (Orange) - Fiber cables, splice points
- **Equipment** (Purple) - Network devices
- **Facilities** (Yellow) - CLLI locations
- **Timeline Events** (Gray) - Chronological markers

### Edge Types
- **Affected_By** - Customers → Outage Events
- **Contacted** - Customers → Agents
- **Managed_By** - Agents → Supervisors
- **Assigned_To** - Outage → Engineers/Crews
- **Damaged** - Outage → Fiber Infrastructure
- **Located_At** - Equipment/Fiber → CLLI
- **Repaired_By** - Splice Points → Repair Crews
- **Caused_By** - Outage → Construction Company
- **Timeline_Link** - All entities → Timeline Events

### Key Metrics for Visualization
- **Customer Impact**: 4,991 total customers affected
- **Service Restoration**: 34% restored at 5.25 hours, 100% at 8.5 hours
- **SMS Deflection Rate**: 91.3% overall (reduced call volume)
- **Customer Satisfaction**: Mixed (NPS 2-6, OSAT 3-7)
- **Repair Complexity**: 144+96=240 individual fiber splices
- **Total Labor**: 56.5 crew hours

---

## Data Quality Notes

- All timestamps are in PST (Pacific Standard Time)
- Phone numbers follow US format: XXX-555-XXXX
- GPS coordinates use decimal degrees format
- All dollar amounts in USD
- Customer data anonymized but realistic
- Foreign keys are consistent across all tables
- Some fields may have NULL values (N/A for internal accounts)

---

## Use Cases for Obsidian Graph

1. **Customer Journey Mapping**: Trace individual customer experiences through the outage
2. **Response Timeline**: Visualize the sequential response from detection to resolution
3. **Infrastructure Impact**: Show which fiber cables affected which customers
4. **Team Coordination**: Map interactions between NOC, engineers, agents, and field crews
5. **Root Cause Analysis**: Connect construction company to damaged infrastructure to affected services
6. **Performance Analysis**: Correlate response times with customer satisfaction
7. **Capacity Planning**: Identify single points of failure and redundancy gaps

---

**Generated:** November 17, 2024  
**Dataset Version:** 1.0  
**Total Records:** 163 across 14 CSV files

