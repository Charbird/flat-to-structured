# Post 2 – Why Device Targeting Should Be the Default

You can target users or devices in Intune. Everyone says either is fine.

That’s where the trouble starts.

Most organizations default to user-based targeting. It’s convenient user groups already exist. But that convenience comes at the cost of predictability and control.

Once you start mixing target types or expanding scope without structure, symptoms show up fast:
- Assignments overlap
- Policies conflict
- Licensed software installs where it shouldn’t
- Security configurations silently fail to apply
- Static groups multiply with no clear purpose

Then you check the deployment: it’s targeting both users and devices. That breaks exclusions. Intune won’t warn you. It just ignores them.

You can also create mixed-object groups in Entra ID users and devices in the same group. And again, there’s no in-product check or validation. If something lands where it shouldn’t, your only option is to start at the device and reverse-engineer every assignment path.

Unlike Group Policy or SCCM, Intune doesn’t let you open a group and see what’s scoped to it. This makes auditing difficult and scale even harder.

## So why device targeting?

It’s not perfect. Dynamic rule criteria for devices in Entra ID is limited. You can’t filter by registry key, software presence, or real-time configuration state like you could in ConfigMgr. But:

- It’s **cleaner**: Devices are single objects, not identity proxies
- It’s **predictable**: A device’s targeting is scoped to what it *is*, not who’s signed in
- It’s **manageable**: Exclusions work as expected, personas can apply at the point of enrollment, and conflicts drop dramatically

## My baseline rules:

- Target **devices** by default  
- Target **users** only when explicitly required (e.g., per-user licensing, training apps) 
- Never mix user and device groups in the same assignment  
- Avoid Entra ID mixed-object groups unless you want to introduce chaos  
- Build clarity into group naming so target intent is visible  

## What’s next

Yes, device targeting can feel limited. But it’s manageable if you build structure around it.

In the next post, I’ll show how naming conventions and group construction can be used to create reliable dynamic targeting even when the native tools are flat. It’s not magic, but it works.

---

📁 GitHub repo: https://github.com/Charbird/flat-to-structured

If you found this helpful, feel free to star the repo or open a comment thread.
