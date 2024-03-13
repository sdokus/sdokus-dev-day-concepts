# Support Workflow

```mermaid
graph TD
    A[Start Here]
    A --> B
    B[Is it clear what is the experienced behavior versus the expected behavior?]
    B -->|Yes| C
    B -->|No| D
    D[Ask the customer to clarify]
    D -->|Only move on once we have a 
    clear understanding of the issue|B
C[Does the issue persist with only TEC plugins and a default theme?]
C -->|Yes|E
C -->|No|F
E[Can you recreate the unintended behavior on a sandbox?]
F[Likely caused by a conflict]
click F href "https://theeventscalendar.com/knowledgebase/testing-for-conflicts/"
E -->|Yes|G
E -->|No|H
G[Open a bug ticket in JIRA]
H[Can you recreate the behavior on the customer's staging site?]
H -->|Yes|I
H -->|No|J
I[Get a db dump - can you reproduce the issue locally?]
I -->|Yes|N
I -->|No|M
M[Most likely an edge case related to the hosting configuration]
N[Most likely due to a specific setting we're missing]
M --> G
N --> G
J[Is the issue only happening on one instance - i.e. a single event or single ticket?]
J -->|No|I
J -->|Yes|K

K[Most likely corrupt data]

style A fill: #6FBF56, stroke: #ffffff,stroke-width: 2px;
style F fill: #FF5733, stroke: #ffffff, stroke-width: 2px;
style K fill: #FF5733, stroke: #ffffff,stroke-width: 2px;
style G fill: #FF5733, stroke: #ffffff, stroke-width: 2px;

%% Second Graph - Information Gathering
A2[Information Needed By Step]
A2 --> B2
B2[Steps to Recreate]
B2 --> C2
C2[
System Information
Conflict Test
]
click C2 href "#system-info"
C2 ---> D2
D2[Staging Site]
click D2 href "#staging-site"
D2 ---> E2
E2[DB Dump]
click E2 href "#db-dump"

style A2 fill: #6FBF56, stroke: #ffffff, stroke-width:2px;
```

## Info Collection
### System Info
- Make sure that you check for the site's language (there have been some issues with French sites, specifically)
- Look for the site's migration status - if the migration is incomplete, even if it is likely unrelated we should offer to help get them migrated. 
- Even if a customer says they have completed a conflict test, do not fully rule out the possibility until you can test yourself

### Staging Site
- You can match the customer's settings for testing purposes by using [this plugin](https://theeventscalendar.com/extensions/settings-import-export/)

### DB Dump
- [How to use a database dump](https://www.loom.com/share/471ae3b4fcaf4a7f8df2e67a7feb37a4)
