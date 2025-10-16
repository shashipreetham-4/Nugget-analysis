# 🎯 Nugget Deep Analysis - Multiple Specialized Prompts

**Purpose:** Deep analysis of Nugget failures on specific issues  
**Input:** 50 conversations + Agent SOPs + Bot SOPs  
**Use Case:** Choose prompt based on what insights you need

---

## 📋 **How to Use These Prompts**

### **What to Provide to LLM:**

1. ✅ **CSV Data:** 50 conversations for specific issue (from `nugget_llm_ready_conversations.sql`)
2. ✅ **Agent SOP:** PDF/Doc of agent-facing SOP
3. ✅ **Bot SOP:** PDF/Doc/Sheet of bot-facing SOP
4. ✅ **One of the prompts below**

### **Choose Prompt Based On:**

| Prompt | Best For | Time | Depth |
|--------|----------|------|-------|
| **#1: Root Cause** | Understanding WHY bot fails | 15 min | Deep |
| **#2: SOP Compliance** | Checking if bot follows its SOP | 20 min | Very Deep |
| **#3: Conversation Flow** | Finding WHERE bot fails in flow | 15 min | Medium |
| **#4: User Experience** | Understanding user frustration | 10 min | Medium |
| **#5: Capability Gap** | Identifying missing APIs/features | 15 min | Deep |
| **#6: Quick Fixes** | Finding immediate improvements | 10 min | Shallow |
| **#7: Bot vs Agent** | Comparing bot and agent behavior | 20 min | Deep |
| **#8: Pattern Recognition** | Finding common failure patterns | 15 min | Medium |
| **#9: Escalation Analysis** | Understanding escalation triggers | 10 min | Medium |
| **#10: Context Awareness** | Checking if bot remembers context | 15 min | Deep |

---

# 🔍 **PROMPT 1: Root Cause Analysis**

**Best for:** Understanding the fundamental reasons why bot fails for this specific issue

### **Copy-Paste This:**

```
I'm analyzing why Nugget (chatbot) fails to resolve a specific issue category. I've attached:

📊 **DATA:**
- CSV with 50 conversations where:
  * Bot failed to resolve
  * Agent successfully resolved
  * All for the same issue: [PRODUCT_CATEGORY] > [PRODUCT_CATEGORY_DETAILS] > [SUBCATEGORY]

📚 **DOCUMENTS:**
- Agent-facing SOP (what agents are supposed to do)
- Bot-facing SOP (what bot is programmed to do)

---

## 🎯 YOUR TASK: ROOT CAUSE ANALYSIS

Analyze these conversations and identify **WHY** Nugget fails. Focus on root causes, not symptoms.

---

### **1. CATEGORIZE FAILURES**

For each conversation, identify the PRIMARY root cause:

**A. CAPABILITY GAPS** (Bot CAN'T do it)
- Missing API access (e.g., can't check freeze status)
- Missing data access (e.g., can't see transaction details)
- Missing feature (e.g., can't create callback)
- Missing integration (e.g., can't update ticket status)

**B. LOGIC ERRORS** (Bot SHOULD do it but doesn't)
- Incorrect flow logic
- Wrong decision tree
- Missing conditional branches
- Incorrect priority/sequencing

**C. KNOWLEDGE GAPS** (Bot doesn't KNOW how)
- SOP not implemented in bot
- Incomplete information in bot's knowledge base
- Outdated/incorrect information
- Missing edge cases

**D. UNDERSTANDING FAILURES** (Bot doesn't GET it)
- Can't understand user's intent
- Misinterprets user's question
- Can't handle variations in phrasing
- Fails on context switches

**E. EXECUTION FAILURES** (Bot tries but fails)
- API calls fail
- Data retrieval errors
- Timeout issues
- Integration problems

---

### **2. ROOT CAUSE FREQUENCY TABLE**

Provide breakdown:

```
| Root Cause Category | Count | % | Severity | Fixable? |
|---------------------|-------|---|----------|----------|
| CAPABILITY GAPS     | X     | XX% | [H/M/L] | [Y/N/Partial] |
| LOGIC ERRORS        | X     | XX% | [H/M/L] | [Y/N/Partial] |
| KNOWLEDGE GAPS      | X     | XX% | [H/M/L] | [Y/N/Partial] |
| UNDERSTANDING FAILS | X     | XX% | [H/M/L] | [Y/N/Partial] |
| EXECUTION FAILURES  | X     | XX% | [H/M/L] | [Y/N/Partial] |
```

---

### **3. SPECIFIC ROOT CAUSES (Top 5)**

**ROOT CAUSE #1:** [Specific issue]
- **Category:** [CAPABILITY/LOGIC/KNOWLEDGE/UNDERSTANDING/EXECUTION]
- **Frequency:** XX% of conversations
- **Examples:** Conv #[X], #[Y], #[Z] - interaction_ids: [IDs]
- **Symptom:** [What user sees]
- **Actual Root Cause:** [Technical reason]
- **Agent's Solution:** [What agent does instead]
- **Fixable?** [Yes/No/Partial]
- **If Fixable:** [Implementation approach]
- **If Not Fixable:** [What capability is needed]

[Repeat for Root Causes #2-5]

---

### **4. SOP COMPLIANCE ANALYSIS**

**Bot SOP Coverage:**
- ✅ Steps bot implements correctly: [list]
- ⚠️ Steps bot implements partially: [list]
- ❌ Steps bot doesn't implement: [list]

**Why Bot Can't Follow SOP:**
1. [Reason 1 - with examples]
2. [Reason 2 - with examples]
3. [Reason 3 - with examples]

**Agent SOP vs Bot Reality:**
| Agent SOP Step | Bot Implementation | Gap | Impact |
|----------------|-------------------|-----|--------|
| [Step] | [What bot does] | [Gap] | [Impact] |

---

### **5. DEPENDENCY ANALYSIS**

**What Bot Needs to Succeed:**

**APIs Required:**
1. [API name] - [Purpose] - [Usage in agent conversations]
2. [API name] - [Purpose] - [Usage in agent conversations]

**Data Required:**
1. [Data point] - [Purpose] - [How agents use it]
2. [Data point] - [Purpose] - [How agents use it]

**Features Required:**
1. [Feature] - [Purpose] - [How agents use it]
2. [Feature] - [Purpose] - [How agents use it]

**Integrations Required:**
1. [System] - [Purpose] - [How agents use it]
2. [System] - [Purpose] - [How agents use it]

---

### **6. CASCADE ANALYSIS**

**Primary Failure → Secondary Failures:**

Many conversations have multiple failures. Identify cascades:

**Example:**
```
Primary: Bot lacks freeze status API
  ↓
Secondary: Bot asks generic questions
  ↓
Tertiary: User gets frustrated
  ↓
Result: User demands agent
```

**Most Common Cascades:**
1. [Primary] → [Secondary] → [Result]
   - Frequency: XX%
   - Examples: Conv #[X], #[Y]

[Continue for top 5 cascades]

---

### **7. CRITICAL ROOT CAUSES (Fix First)**

Priority ranking based on:
- Frequency (how often)
- Severity (how bad)
- Fixability (how easy)

**PRIORITY 1: [Root Cause]**
- Frequency: XX%
- Severity: [High/Med/Low]
- Fixability: [Easy/Medium/Hard]
- Fix Approach: [Detailed approach]
- Expected Impact: [What will improve]
- Examples: Conv #[X], #[Y], #[Z]

**PRIORITY 2-5:** [Similar format]

---

### **8. CONVERSATION EXAMPLES**

Provide 3-5 detailed examples showing different root causes:

**EXAMPLE 1: [ROOT CAUSE TYPE]**

**Conversation #[N]**
- interaction_id: [ID]
- conversation_id: [ID]
- Date: [date]

**What Happened:**
```
Message #1 (User): [Quote]
Message #2 (Bot): [Quote]
...
Message #10 (Agent): [Quote - shows solution]
```

**Root Cause Analysis:**
- **Surface Symptom:** [What seems to be the problem]
- **Actual Root Cause:** [The real underlying issue]
- **Why Bot Failed:** [Technical reason]
- **What Bot Needed:** [Specific capability/knowledge/fix]
- **Agent's Advantage:** [What agent had that bot didn't]
- **How to Fix:** [Specific implementation]

[Repeat for 2-4 more examples]

---

### **9. SYSTEMIC ISSUES**

Beyond individual conversations, identify systemic problems:

**Issue #1:** [Systemic problem]
- **Affects:** XX% of conversations
- **Root Cause:** [Why it exists]
- **Examples:** Conv #[X], #[Y], #[Z]
- **Fix Required:** [Architectural/design change needed]
- **Effort:** [High/Med/Low]
- **Impact if Fixed:** [Expected improvement]

[Continue for 3-5 systemic issues]

---

### **10. IMPLEMENTATION ROADMAP**

Based on root cause analysis, provide implementation priority:

**Phase 1: Immediate Fixes (< 2 weeks)**
1. [Fix] - Addresses [Root Cause] - Impact: XX%
2. [Fix] - Addresses [Root Cause] - Impact: XX%

**Phase 2: Short-term (2-4 weeks)**
1. [Fix] - Addresses [Root Cause] - Impact: XX%
2. [Fix] - Addresses [Root Cause] - Impact: XX%

**Phase 3: Medium-term (1-2 months)**
1. [Fix] - Addresses [Root Cause] - Impact: XX%
2. [Fix] - Addresses [Root Cause] - Impact: XX%

**Phase 4: Long-term (3+ months)**
1. [Fix] - Addresses [Root Cause] - Impact: XX%

**Expected Overall Impact:**
- Resolve XX% more conversations without agent
- Reduce escalation time by XX%
- Improve user satisfaction by XX%

---

**OUTPUT FORMAT:** Provide all sections above with specific examples and conversation IDs.
```

---

# 📊 **PROMPT 2: SOP Compliance Analysis**

**Best for:** Checking if bot follows its SOP and comparing with agent SOP

### **Copy-Paste This:**

```
I'm analyzing SOP compliance for Nugget (chatbot). I've attached:

📊 **DATA:** 50 conversations where bot failed, agent resolved
📚 **AGENT SOP:** What agents are trained to do
📚 **BOT SOP:** What bot is programmed to do
🎯 **ISSUE:** [PRODUCT_CATEGORY] > [PRODUCT_CATEGORY_DETAILS] > [SUBCATEGORY]

---

## 🎯 YOUR TASK: SOP COMPLIANCE ANALYSIS

Compare bot's actual behavior with both SOPs and identify compliance gaps.

---

### **1. BOT SOP COMPLIANCE CHECK**

For each step in Bot SOP, check if bot actually does it:

**Bot SOP Step 1:** [Quote from bot SOP]
- ✅ **Compliant:** [Yes/No/Partial]
- 📊 **Evidence:** Conv #[X], #[Y] show: [what bot does]
- ⚠️ **Deviation:** [If not compliant, what bot does instead]
- 🔍 **Why Deviation:** [Reason - capability gap/logic error/etc]
- 💡 **Fix:** [How to make bot compliant]

[Repeat for all Bot SOP steps]

**Bot SOP Compliance Score:** [X]/[Total] steps followed correctly

---

### **2. AGENT SOP COMPLIANCE CHECK**

For each step in Agent SOP, check if agents do it:

**Agent SOP Step 1:** [Quote from agent SOP]
- ✅ **Agents Follow:** [Yes/No/Partial]
- 📊 **Evidence:** Conv #[X], #[Y] show: [what agent does]
- ⚠️ **Deviation:** [If agents deviate, what they do instead]
- 🔍 **Why Deviation:** [Reason - practical/efficient/necessary]
- 💡 **Learning:** [What this teaches us]

[Repeat for all Agent SOP steps]

**Agent SOP Compliance Score:** [X]/[Total] steps followed correctly

---

### **3. BOT vs AGENT SOP COMPARISON**

**Steps in Both SOPs:**

| Step | Bot SOP Says | Agent SOP Says | Bot Does | Agent Does | Gap |
|------|-------------|----------------|----------|------------|-----|
| [1] | [Quote] | [Quote] | [Behavior] | [Behavior] | [Analysis] |

**Steps Only in Agent SOP:**
- [Step] - Why agents need this: [Reason]
- Can bot do this?: [Yes/No/Needs capability]

**Steps Only in Bot SOP:**
- [Step] - Why bot has this: [Reason]
- Should agents do this?: [Yes/No/Reason]

---

### **4. COMPLIANCE FAILURES & IMPACT**

**Where Bot Doesn't Follow Its Own SOP:**

**Failure #1:** Bot supposed to [SOP requirement] but actually [what bot does]
- **Frequency:** XX% of conversations
- **Examples:** Conv #[X], #[Y], #[Z]
- **User Impact:** [How this affects user experience]
- **Why Non-Compliant:** [Root cause]
- **Agent Workaround:** [What agent does instead]
- **Fix:** [How to make bot compliant]

[Repeat for top 5 compliance failures]

---

### **5. AGENT DEVIATIONS (Learning Opportunities)**

**Where Agents DON'T Follow Their SOP (for good reasons):**

**Deviation #1:** Agent supposed to [SOP requirement] but actually [what agent does]
- **Frequency:** XX% of agent conversations
- **Examples:** Conv #[X], #[Y], #[Z]
- **Why Deviation:** [Practical reason]
- **Better Outcome?** [Yes/No - explain]
- **Recommendation:** [Update SOP? Teach bot this deviation?]

[Repeat for top 5 deviations]

---

### **6. SOP GAPS**

**What's Missing from Bot SOP:**
1. [Gap] - Agents do this but not in bot SOP
   - Evidence: Conv #[X], #[Y]
   - Why needed: [Reason]
   - Add to bot SOP: [Yes/No/Partial]

**What's Missing from Agent SOP:**
1. [Gap] - Common agent behavior not documented
   - Evidence: Conv #[X], #[Y]
   - Why needed: [Reason]
   - Add to agent SOP: [Yes/No]

**What's Missing from Both:**
1. [Gap] - Neither SOP covers [edge case/scenario]
   - Evidence: Conv #[X], #[Y]
   - Impact: [How this affects resolution]
   - Recommendation: [What to add]

---

### **7. SOP EFFECTIVENESS**

**Bot SOP Effectiveness:**
- ✅ **Works Well:** [Which parts of bot SOP lead to success]
- ⚠️ **Needs Improvement:** [Which parts are unclear/incomplete]
- ❌ **Doesn't Work:** [Which parts can't be implemented]

**Agent SOP Effectiveness:**
- ✅ **Works Well:** [Which parts agents follow successfully]
- ⚠️ **Agents Struggle:** [Which parts are difficult to follow]
- ❌ **Agents Ignore:** [Which parts agents consistently skip]

---

### **8. CONVERSATION EXAMPLES**

**EXAMPLE 1: Bot SOP Non-Compliance**

**Conversation #[N]** - interaction_id: [ID]

**Bot SOP Requirement:** [Quote from bot SOP]

**What Bot Actually Did:**
```
Message #3 (Bot): [Quote showing non-compliance]
Message #5 (Bot): [Quote showing non-compliance]
```

**What Bot Should Have Done:** [Per bot SOP]

**Impact:** User got frustrated because [reason]

**Agent's Compliant Approach:**
```
Message #12 (Agent): [Quote showing SOP compliance]
```

**Why Bot Couldn't Comply:** [Technical reason]

**Fix:** [Specific implementation to make bot compliant]

[Provide 3-5 more examples covering different types of non-compliance]

---

### **9. SOP UPDATE RECOMMENDATIONS**

**Bot SOP Updates Needed:**
1. **Add:** [New step/instruction]
   - **Reason:** [Why needed]
   - **Evidence:** Conv #[X], #[Y]
   - **Priority:** [High/Med/Low]

2. **Modify:** [Existing step]
   - **Current:** [What it says now]
   - **Proposed:** [What it should say]
   - **Reason:** [Why change needed]
   - **Evidence:** Conv #[X], #[Y]

3. **Remove:** [Step that doesn't work]
   - **Reason:** [Why remove]
   - **Evidence:** [Why it's not working]

**Agent SOP Updates Needed:**
[Similar format]

---

### **10. COMPLIANCE ROADMAP**

**Immediate Actions (This Week):**
1. Fix bot logic to comply with [SOP step]
   - Impact: XX% better compliance
   - Examples: Would fix Conv #[X], #[Y]

**Short-term (2-4 weeks):**
1. Update bot SOP to include [missing step]
2. Train bot on [new behavior]
   - Impact: XX% better resolution

**Long-term (1-3 months):**
1. Add capability so bot can [SOP requirement]
2. Update both SOPs based on learnings
   - Impact: XX% improvement overall

**Expected Results:**
- Bot SOP Compliance: [Current]% → [Target]%
- Resolution Rate: [Current]% → [Target]%
- User Satisfaction: [Current]% → [Target]%

---

**OUTPUT FORMAT:** Provide detailed analysis with specific conversation IDs and SOP quotes.
```

---

# 🔀 **PROMPT 3: Conversation Flow Analysis**

**Best for:** Understanding WHERE in the conversation flow bot fails

### **Copy-Paste This:**

```
I'm analyzing conversation flow to identify WHERE Nugget (chatbot) fails. I've attached:

📊 **DATA:** 50 conversations (bot failed, agent resolved)
📚 **SOPS:** Agent and Bot facing SOPs
🎯 **ISSUE:** [PRODUCT_CATEGORY] > [PRODUCT_CATEGORY_DETAILS] > [SUBCATEGORY]

---

## 🎯 YOUR TASK: CONVERSATION FLOW ANALYSIS

Map the conversation flow and identify exact failure points.

---

### **1. TYPICAL CONVERSATION STAGES**

Identify common stages in these conversations:

**Stage 1: [Name]** (e.g., "Initial Greeting & Intent Recognition")
- **Bot's Goal:** [What bot tries to achieve]
- **Success Rate:** XX% of conversations
- **Failure Point:** [If fails, why]
- **Examples:** Conv #[X], #[Y]

**Stage 2: [Name]** (e.g., "Information Gathering")
- **Bot's Goal:** [What bot tries to achieve]
- **Success Rate:** XX% of conversations
- **Failure Point:** [If fails, why]
- **Examples:** Conv #[X], #[Y]

[Continue for all identified stages]

---

### **2. FAILURE POINT HEATMAP**

Where do failures happen most?

```
Conversation Stage → Failure %
═══════════════════════════════════
[Stage 1] ░░░░░░ 10%
[Stage 2] ████████████ 35% ⚠️
[Stage 3] ████████████████ 45% 🔥
[Stage 4] ████ 15%
[Stage 5] ░░ 5%
```

**Critical Failure Points:**
1. **[Stage with highest failure]** - XX% fail here
   - Why: [Reason]
   - Examples: Conv #[X], #[Y], #[Z]
   
[Continue for top 3 critical points]

---

### **3. FLOW DIVERGENCE ANALYSIS**

**When Bot vs Agent Paths Diverge:**

**Divergence Point #1:** Message #[N] in typical conversation
- **Bot Path:**
  ```
  Bot: [What bot does]
  User: [User response]
  Bot: [Bot's next action]
  → Result: Failure
  ```
  
- **Agent Path:**
  ```
  Agent: [What agent does instead]
  User: [User response]
  Agent: [Agent's next action]
  → Result: Success
  ```

- **Why Divergence:** [Reason bot takes different path]
- **Frequency:** XX% of conversations
- **Fix:** [How to make bot follow agent path]

[Repeat for top 5 divergence points]

---

### **4. CONVERSATION LENGTH ANALYSIS**

**Bot Phase (Before Agent):**
- Average messages: [N]
- Average time: [X minutes]
- Average user frustration signals: [N]

**Agent Phase (After Agent Joins):**
- Average messages to resolution: [N]
- Average time to resolution: [X minutes]
- Resolution success rate: [XX]%

**Key Insight:**
Bot takes [N] messages and [X] minutes without resolution.
Agent resolves in [N] messages and [X] minutes.

**Why the Difference:** [Analysis of what agent does differently]

---

### **5. LOOPING & CIRCULAR PATTERNS**

**Where Bot Gets Stuck:**

**Loop Pattern #1:** [Description]
```
Bot: [Message A]
User: [Response]
Bot: [Message B]
User: [Response]
Bot: [Message A again] ← LOOP
User: [Frustration]
```

- **Frequency:** XX% of conversations
- **Examples:** Conv #[X], #[Y], #[Z]
- **Why Loop Exists:** [Technical reason]
- **How Agent Breaks It:** [Agent's approach]
- **Fix:** [How to prevent loop]

[Repeat for all identified loop patterns]

---

### **6. ESCALATION TRIGGERS**

**What Triggers Escalation:**

**Trigger #1:** [Specific event]
- **When:** [At which stage]
- **Frequency:** XX% of escalations
- **Examples:** Conv #[X], #[Y]
- **User Signal:** [What user says/does]
- **Bot Response:** [How bot handles it]
- **Better Approach:** [What could prevent escalation]

**Escalation Timeline:**
```
Avg time until escalation: [X] minutes
Avg messages until escalation: [N]
Most common trigger: [Trigger]
```

---

### **7. SUCCESSFUL vs FAILED FLOWS**

**Compare flows that agents resolve quickly vs slowly:**

**Quick Resolution (<5 agent messages):**
- **Common Flow:** [Describe typical flow]
- **Agent's Approach:** [What agent does]
- **Key Success Factor:** [What makes it quick]
- **Examples:** Conv #[X], #[Y]
- **Bot Could Do This?** [Yes/No/Needs capability]

**Slow Resolution (10+ agent messages):**
- **Common Flow:** [Describe typical flow]
- **Why Slow:** [Reason for complexity]
- **Examples:** Conv #[X], #[Y]
- **Bot Could Handle?** [Yes/No/Partial]

---

### **8. CONVERSATION EXAMPLES**

Provide 3-5 examples showing different flow patterns:

**EXAMPLE 1: TYPICAL FAILURE FLOW**

**Conversation #[N]** - interaction_id: [ID]

**Flow Map:**
```
Stage 1: Initial Contact
├─ Msg #1 (User): "I need help with [issue]"
├─ Msg #2 (Bot): [Generic greeting]
└─ ✅ PASS

Stage 2: Intent Recognition
├─ Msg #3 (User): [Clarification]
├─ Msg #4 (Bot): [Bot's understanding]
└─ ⚠️ PARTIAL - Bot understands but lacks data

Stage 3: Information Gathering ← FAILURE HERE
├─ Msg #5 (Bot): "What's your [X]?"
├─ Msg #6 (User): [Provides X]
├─ Msg #7 (Bot): "What's your [X]?" ← Loops
├─ Msg #8 (User): "I just told you!"
└─ ❌ FAIL - Looping error

Stage 4: Escalation
├─ Msg #9 (Bot): "Let me connect you..."
└─ Agent joins

Stage 5: Agent Resolution
├─ Msg #10 (Agent): [Uses the X user provided]
├─ Msg #11 (Agent): [Takes action]
└─ ✅ RESOLVED
```

**Failure Analysis:**
- **Failed at:** Stage 3 (Information Gathering)
- **Reason:** Bot didn't store user's input
- **Agent's Advantage:** Agent read chat history
- **Fix:** Implement context memory

[Provide 2-4 more flow examples]

---

### **9. FLOW OPTIMIZATION RECOMMENDATIONS**

**Stage-by-Stage Improvements:**

**Stage 1 Improvements:**
1. [Specific improvement]
   - Impact: [Expected result]
   - Examples: Would help Conv #[X], #[Y]

**Stage 2 Improvements:**
[Similar format]

**Stage 3 Improvements:**
[Similar format]

**Overall Flow Optimization:**
- **Remove:** [Unnecessary steps]
- **Add:** [Missing steps]
- **Reorder:** [Better sequence]
- **Combine:** [Steps to merge]

**Expected Impact:**
- Reduce avg messages by: [N]
- Reduce avg time by: [X] minutes
- Reduce escalations by: [XX]%

---

### **10. IDEAL FLOW vs CURRENT FLOW**

**IDEAL FLOW (Based on Agent Success):**
```
1. [Step] - [Duration]
2. [Step] - [Duration]
3. [Step] - [Duration]
4. Resolution ✅
Total: [N] messages, [X] minutes
```

**CURRENT BOT FLOW:**
```
1. [Step] - [Duration]
2. [Step] - [Duration]
3. [Step - with issues] - [Duration]
4. [Loop/Error] - [Duration]
5. Escalation ❌
Total: [N] messages, [X] minutes
```

**Gap Analysis:**
- Bot adds [N] unnecessary steps
- Bot loops [N] times on average
- Bot lacks [capability] at step [N]

**Roadmap to Ideal Flow:**
[Implementation plan]

---

**OUTPUT FORMAT:** Provide detailed flow analysis with visual maps and conversation IDs.
```

---

# 👤 **PROMPT 4: User Experience Analysis**

**Best for:** Understanding how failures affect users and their frustration points

### **Copy-Paste This:**

```
I'm analyzing user experience when Nugget (chatbot) fails. I've attached:

📊 **DATA:** 50 conversations (bot failed, agent resolved)
📚 **SOPS:** Agent and Bot SOPs
🎯 **ISSUE:** [PRODUCT_CATEGORY] > [PRODUCT_CATEGORY_DETAILS] > [SUBCATEGORY]

---

## 🎯 YOUR TASK: USER EXPERIENCE ANALYSIS

Analyze from the user's perspective - their journey, frustrations, and pain points.

---

### **1. USER FRUSTRATION SIGNALS**

Identify specific phrases/behaviors showing frustration:

**High Frustration Signals:**
- "[Exact phrase users say]" - Frequency: XX% - Examples: Conv #[X], #[Y]
- "[Exact phrase]" - Frequency: XX% - Examples: Conv #[X], #[Y]

**Medium Frustration Signals:**
- "[Exact phrase]" - Frequency: XX%

**Low Frustration Signals:**
- "[Exact phrase]" - Frequency: XX%

**Frustration Timeline:**
```
Message 1-3: Users generally patient
Message 4-6: Frustration starts (XX% show signals)
Message 7-10: High frustration (XX% show signals)
Message 11+: User demands agent (XX%)
```

---

### **2. USER JOURNEY MAPPING**

**Typical User Journey:**

**Phase 1: Hope** (Messages 1-2)
- **User Emotion:** [Hopeful/neutral/urgent]
- **User Expectation:** [What user hopes for]
- **Bot Delivers:** [What bot provides]
- **Gap:** [Expectation vs reality]

**Phase 2: Engagement** (Messages 3-5)
- **User Emotion:** [Engaged/impatient]
- **User Action:** [Provides info, answers questions]
- **Bot Response:** [How bot handles it]
- **User Reaction:** [User's feelings]

**Phase 3: Frustration** (Messages 6-8)
- **User Emotion:** [Frustrated/annoyed]
- **Trigger:** [What caused frustration]
- **User Signal:** [How user shows frustration]
- **Bot Misses:** [What bot doesn't pick up on]

**Phase 4: Demand for Human** (Messages 9-11)
- **User Emotion:** [Very frustrated/angry]
- **User Demand:** [How user asks for agent]
- **Bot Response:** [How bot escalates]

**Phase 5: Relief** (Agent joins)
- **User Emotion:** [Relief/hope]
- **Agent Approach:** [How agent changes experience]
- **User Satisfaction:** [Final outcome]

---

### **3. PAIN POINT ANALYSIS**

**Top User Pain Points:**

**Pain Point #1:** [Specific issue]
- **User Quote:** "[Exact frustration quote]"
- **Frequency:** XX% of conversations
- **Examples:** Conv #[X], #[Y], #[Z]
- **Caused By:** [Bot behavior that creates pain]
- **User Impact:** [How this affects user]
- **Agent Solution:** [How agent alleviates pain]
- **Prevention:** [How to avoid this pain point]

[Repeat for top 10 pain points]

---

### **4. EMOTIONAL TRAJECTORY**

**Emotional State Throughout Conversation:**

```
Sentiment Score (1-10)
10 │
 9 │ ●                                    ●───● (Agent joins)
 8 │   ╲
 7 │     ●
 6 │       ╲
 5 │         ●
 4 │           ╲  
 3 │             ●
 2 │               ╲
 1 │                 ●─────●
   └─────────────────────────────────────────→
     Msg 1  3  5  7  9  11 13 15 (Message #)
     
     Bot Phase │ Agent Phase
```

**Key Observations:**
- Sentiment drops [X] points during bot phase
- Sentiment recovers [X] points when agent joins
- Lowest point: Message #[N] when [event]

---

### **5. USER EFFORT ANALYSIS**

**How Much Effort User Puts In:**

**Information Provided by User:**
- Average pieces of info shared: [N]
- Questions answered: [N]
- Repetitions (user repeats same info): [N] times
- Screenshots/docs shared: [N]

**User Effort Score:**
```
Low Effort (1-3): User shares minimal info, bot resolves
Medium Effort (4-6): Normal Q&A, reasonable
High Effort (7-8): User answers many questions
Excessive Effort (9-10): User repeats info, frustrated ⚠️
```

**Distribution:**
- Low: XX% of conversations
- Medium: XX%
- High: XX%
- Excessive: XX% ← Problem area

**Where Effort Becomes Excessive:**
[Analysis of what causes high effort]

---

### **6. EXPECTATION vs REALITY**

**What Users Expect:**
1. [User expectation #1]
   - **Reality:** [What bot actually does]
   - **Gap:** [Difference]
   - **Impact:** [User frustration level]
   - **Examples:** Conv #[X], #[Y]

**Where Expectations Are Met:**
- [List positive moments]

**Where Expectations Are Violated:**
- [List disappointments]

**Biggest Expectation Gaps:**
[Priority ranking]

---

### **7. USER VERBATIM ANALYSIS**

**Most Common User Phrases:**

**Frustration Phrases:**
- "[Exact quote]" - Appears [N] times
- "[Exact quote]" - Appears [N] times
- What triggers this: [Bot behavior]

**Confusion Phrases:**
- "[Exact quote]" - Appears [N] times
- What triggers this: [Bot behavior]

**Desperation Phrases:**
- "[Exact quote]" - Appears [N] times
- What triggers this: [Bot behavior]

**Demand for Agent:**
- "[Exact quote]" - Appears [N] times

**Analysis:**
These phrases appear when: [Pattern analysis]

---

### **8. CONVERSATION EXAMPLES**

**EXAMPLE 1: TYPICAL USER FRUSTRATION JOURNEY**

**Conversation #[N]** - interaction_id: [ID]

**User's Emotional Journey:**

```
Message #1 (User): "Hi, I need help with [issue]"
└─ Emotion: Neutral, hopeful
└─ Expectation: Bot will help

Message #3 (User): "My account number is [X]"
└─ Emotion: Cooperative
└─ Expectation: Bot will use this info

Message #5 (User): "I already told you! [X]!"
└─ Emotion: Frustrated 😤
└─ Trigger: Bot asked again
└─ Pain: Feels unheard

Message #8 (User): "Can I speak to a person please?"
└─ Emotion: Giving up, frustrated 😠
└─ Trigger: No progress
└─ Pain: Wasted time

Message #11 (User - to Agent): "Finally! I've been trying..."
└─ Emotion: Relief but annoyed
└─ Residual frustration from bot experience

Message #15 (User - to Agent): "Thank you so much!"
└─ Emotion: Satisfied, relieved 😊
└─ Experience: Agent solved quickly
```

**Key UX Issues:**
1. Bot made user repeat info (Pain Point #1)
2. Bot didn't show empathy for frustration
3. Bot gave no progress updates
4. User had to explicitly request agent

**How Agent Fixed UX:**
1. Acknowledged user's frustration immediately
2. Used info user already provided
3. Gave clear next steps
4. Resolved quickly

[Provide 3-5 more examples]

---

### **9. UX IMPROVEMENT RECOMMENDATIONS**

**Quick UX Wins:**

**Win #1:** [Specific improvement]
- **Current UX:** [Bad experience]
- **Improved UX:** [Better experience]
- **Implementation:** [How to do it]
- **Impact:** [Expected improvement]
- **Examples:** Would fix Conv #[X], #[Y]

**Prioritized UX Fixes:**

**HIGH PRIORITY:**
1. [Fix] - Affects XX% - User pain level: [High/Med/Low]
2. [Fix] - Affects XX% - User pain level: [High/Med/Low]

**MEDIUM PRIORITY:**
[List]

**LOW PRIORITY:**
[List]

---

### **10. USER SATISFACTION PREDICTION**

**Current Bot UX:**
- User Frustration Rate: XX%
- Avg Frustration Onset: Message #[N]
- Excessive Effort Rate: XX%
- Users Demanding Agent: XX%

**After Improvements:**
- User Frustration Rate: [Target]%
- Avg Frustration Onset: Message #[N] (delayed)
- Excessive Effort Rate: [Target]%
- Users Demanding Agent: [Target]%

**Expected NPS Impact:**
- Current (estimated): [Score]
- After improvements: [Score]
- Improvement: +[N] points

---

**OUTPUT FORMAT:** Focus on user quotes, emotional journey, and specific pain points with conversation IDs.
```

---

*[Continue in next message due to length...]*

