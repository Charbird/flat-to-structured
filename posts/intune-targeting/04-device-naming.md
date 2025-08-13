# Post 4 — Device Naming for Visibility and Targeting

*Hang on… I thought we were treating our systems like farm animals. So why are we naming them like pets?*

If we’re managing at scale, device names shouldn’t be one-offs.  
They should be part of a structure that makes devices easy to see, sort, and target.

---

## Why Device Naming Matters

In the last post, we covered **group tags** — great for automation at enrollment.  
But group tags are invisible in the Intune console. You can’t sort by them, filter by them, or see them at a glance.

Device names, on the other hand:

1. **Make targeting visible** – sortable, searchable, filterable in the console  
2. **Enable dynamic groups** – drive queries without static assignments  
3. **Build a synthetic hierarchy** – name segments let you scope at multiple levels

---

## The Visibility Problem in Intune

This is a **fundamental deficiency** in Intune:  
Entra ID groups don’t give you complete information from the perspective of an Intune admin, and group tags — while powerful — are invisible in the Intune console.

Out of the box, the only real visibility you have is in the console’s device list view:  
- **Filter**  
- **Sort**  
- **Export**

That’s it.  
No layered drill-downs. No way to surface group tag logic. No dynamic cross-view without building your own system on Microsoft Graph.

Structured device naming is how you improve this without building custom solutions.  
It uses the tools you already have, works with Intune’s built-in visibility, and supports both **targeting** and **management at scale**.

---

## Example Naming Structure

`SU-ACCT-123456`

| Segment   | Purpose                             |
|-----------|-------------------------------------|
| `SU`      | Device type (Single User, KSK for Kiosk, etc.) |
| `ACCT`    | Business unit/persona (e.g., Accounting) |
| `123456`  | Serial number or unique ID           |

This allows you to:

- Target all `SU-*` devices (single-user devices)  
- Target all `SU-ACCT-*` devices (single-user devices in accounting)  
- Still find individual devices quickly

---

## Realigning Your Fleet

If your current names don’t give targeting or management value, fix them:

- Use **Intune PowerShell scripts** or remediation scripts to rename at scale  
- Pull attributes like group tag, serial number, or business unit from Entra ID  
- Roll out changes gradually — no need for full re-enrollment

---

## Evaluate Your Current Standard

If your devices are named `ORG-123456`, what does that tell you?  
You already know they’re in your tenant — the name should add **management context**, not just uniqueness.

---

Group tags handle the invisible automation layer.  
Device names give you **visible control** to manage at scale.

---

Earlier posts in the series:  
🔗 [github.com/Charbird/flat-to-structured](https://github.com/Charbird/flat-to-structured)

#Intune #EndpointManagement #DeviceManagement #Automation #Targeting #EntraID
