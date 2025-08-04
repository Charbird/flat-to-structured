# Post 3 – Personas and Group Tags: Targeting Like You Mean It


The first two posts were the intro course: targeting 101.  
This is where we start the advanced course.

Let’s talk about **personas**, **group tags**, and how to automate your targeting structure from the moment a device is enrolled.

---

## Why Manual Targeting Doesn’t Scale

Most orgs start by assigning apps and policies manually.  
It’s fine when an environment starts small but it doesn’t hold up over time.

- Devices pile up  
- Exceptions multiply  
- Targeting becomes guesswork

If you’re moving devices into groups by hand, **you don’t have a structure** — you have a task list.

---

## Farm Animals and IT Devices

Every device is a little different.  
But **you don’t hand-feed every chicken**.

Enterprise IT is about **scaling structure**.  
That’s why we manage by **persona**: role-based bundles of apps, policies, and baselines.

- **Chickens get the same feed**: even if one doesn’t like it.  
- **Sheep don’t opt out of the fence**: structure is enforced.  
- **You tag the cow and assign the care plan**: not negotiate.

This is **herd management**, not pet projects.

---

## What is a Persona?

A **persona** is a predefined set of:

- Apps  
- Policies  
- Baselines  
- Enrollment settings

Assigned to a device **based on its role**.

---

### Example Personas and Group Tags

| Persona Name     | Group Tag Applied  | Example Use Case                        |
|------------------|--------------------|----------------------------------------|
| `Kiosk Device`   | `GT-Kiosk01`       | Shared public device, limited access   |
| `Power User`     | `GT-PowerUser01`   | Staff needing advanced tools/apps      |
| `Standard Staff` | `GT-Staff01`       | Default config for most office staff   |
| `Contractor`     | `GT-Contractor01`  | Restricted device with web-only access |

---

### Persona Mapping Flow

[Device Group: Kiosk Devices]  
    └── Group Tag: GT-Kiosk01  
        └── Autopilot Profile: Kiosk_Profile  
        └── ESP Profile: ESP_Kiosk  
        └── Apps: Edge, Custom Browser  
        └── Policies: Lockdown Policy, Wi-Fi Config  
        └── Baselines: Security_LowRisk  

[Device Group: Standard Staff]  
    └── Group Tag: GT-Staff01  
        └── Autopilot Profile: Staff_Profile  
        └── ESP Profile: ESP_Standard  
        └── Apps: Office, Teams, OneDrive  
        └── Policies: Password Policy, BitLocker  
        └── Baselines: Security_Standard  

[Device Group: Power Users]  
    └── Group Tag: GT-PowerUser01  
        └── Autopilot Profile: Power_Profile  
        └── ESP Profile: ESP_Standard  
        └── Apps: Office, Teams, PowerBI, Dev Tools  
        └── Policies: Password Policy, BitLocker, Local Admin  
        └── Baselines: Security_Advanced  

[Device Group: Contractors]  
    └── Group Tag: GT-Contractor01  
        └── Autopilot Profile: Contractor_Profile  
        └── ESP Profile: ESP_Light  
        └── Apps: Office Web Only  
        └── Policies: Conditional Access, Restricted Access  
        └── Baselines: Security_Minimal  

---

## How Group Tags Enforce Structure

Apply a **group tag** during Autopilot (or import), and Entra ID automatically assigns the device to the right persona.

### Example Dynamic Group Rule

```
(device.devicePhysicalIDs -any (_ -contains "[OrderID]:GT-Kiosk01"))
```

This finds devices with the tag `GT-Kiosk01` and places them in the `Kiosk Device` persona group.

For technical details on using group tags in Autopilot and Entra ID dynamic groups, see:  
🔗 [Microsoft Autopilot Enrollment Guide](https://learn.microsoft.com/en-us/autopilot/enrollment-autopilot)

---

## What Happens Next

Once in the persona group, the device gets:

- Assigned apps and policies  
- Enrollment Status Page (ESP) settings  
- Compliance and security baselines  
- A mapped enrollment profile

All of this happens **without manual intervention** from the moment the device ID is imported and tagged.

---

## Why This Matters Long-Term

This isn’t just about setup: it’s about **long-term care and feeding**.

- Devices stay in the right persona over time.  
- Apps and policies remain consistent — even as devices re-enroll or change hands.  
- **Testing is simpler**:  
  → You test the *persona*, not every device.  
  → Updates are managed **at scale**, not ad hoc.

Personas turn chaotic, reactive IT into **repeatable system management**.

---

## Real Talk: Personas Involve Tradeoffs

Not every device in a persona will need every app or policy.  
That’s fine.

**Structure beats precision** — the goal is role-based consistency, not perfection.

- Some devices will get apps they don’t use.  
- Some policies might not apply 1:1.  
- The key is: **it doesn’t interfere with the device’s main purpose.**

---

## The Goal: Automate Structure, Reduce Admin Overhead

Personas + group tags =  
**No more hand-picking apps** or chasing down exclusions.

You **design the structure once**, and **enforce it automatically** from enrollment onward.

---

## Coming Up: Naming, Layering, and Avoiding Pachinko

Next post: how naming conventions and group layering complete the picture — and how to avoid **playing pachinko with your deployments**.

---

## GitHub + Feedback

Details and examples here:  
👉 [github.com/Charbird/flat-to-structured](https://github.com/Charbird/flat-to-structured)

Star the repo or drop feedback if this helped.