# How-To Guide: Settings & Access

> Practical step-by-step instructions for Access, Membership, and Institutional management in Q-Collider.

---

## Table of Contents

1. [How to Check Your Current Membership Tier](#1-how-to-check-your-current-membership-tier)
2. [How to Upgrade Your Membership](#2-how-to-upgrade-your-membership)
3. [How to Understand Your Permission Flags](#3-how-to-understand-your-permission-flags)
4. [How to Manage Users as an Admin](#4-how-to-manage-users-as-an-admin)
5. [How to Set Up Your Institutional Account](#5-how-to-set-up-your-institutional-account)
6. [How to Manage Institutional Members](#6-how-to-manage-institutional-members)
7. [How to View Org-Level Analytics](#7-how-to-view-org-level-analytics)
8. [How to Log Out](#8-how-to-log-out)

---

## 1. How to Check Your Current Membership Tier

**Route:** `/AccessAndMembership`

1. Navigate to **Access & Membership** from the sidebar.
2. The **My Membership** card at the top shows:
   - Your current **Account Type** (subscriber, sponsor, institutional, etc.)
   - Your current **Status** (pending, active, paused, invited, revoked)
   - The date your profile was created
3. Below the card, a **Permissions Summary** lists which capabilities are enabled for your account.

---

## 2. How to Upgrade Your Membership

**Route:** `/AccessAndMembership`

1. Navigate to **Access & Membership**.
2. Browse the **Membership Tiers** section — each tier card lists its features.
3. Click **Upgrade** on the tier you want to move to.
4. A confirmation dialog appears summarising:
   - What new permissions you will gain
   - Any requirements (e.g. institutional affiliation)
5. Click **Confirm Upgrade** to submit the request.
6. Your status temporarily changes to `pending` while an admin reviews.
7. Once approved, your account type updates and you gain the new permissions immediately.

**Tier upgrade paths:**
```
subscriber → sponsor
subscriber → institutional (requires organisation record)
sponsor → institutional_sponsor
institutional → institutional_sponsor
```

---

## 3. How to Understand Your Permission Flags

**Route:** `/AccessAndMembership` → Permissions Summary

| Flag | What it Enables |
|---|---|
| `can_manage_team` | Invite and manage team members in your organisation |
| `can_manage_site` | Register compute sites and change node configuration |
| `can_join_campaigns` | Participate in global research campaigns |
| `can_vote_on_programs` | Vote on program proposals in the Roadmap |
| `can_submit_publications` | Create and submit scientific publications |
| `can_sponsor_campaigns` | Create and fund research campaigns |

- Green = enabled for your account
- Grey = not enabled for your current tier
- Click **Upgrade** next to any locked permission to see which tier unlocks it.

---

## 4. How to Manage Users as an Admin

**Route:** `/AccessAndMembership` · **Requires:** Admin role

1. Navigate to **Access & Membership**.
2. Scroll to the **All Users** table (visible to admins only).
3. The table lists all registered users with their account type, status, and role.
4. To **edit a user's access profile**:
   - Click the user row.
   - Change `account_type`, `status`, or toggle individual permission flags.
   - Click **Save Changes**.
5. To **revoke access**, change `account_status` to `revoked`.
6. To **reactivate** a user, change status back to `active`.

**Note:** You cannot change another admin's role unless you are also an admin. You cannot downgrade your own role.

---

## 5. How to Set Up Your Institutional Account

**Route:** `/InstitutionalDashboard` · **Requires:** Admin or Institutional account type

**Step 1 — Create an Organisation record:**
1. Navigate to **Institutional Dashboard**.
2. If no organisation exists yet, click **Create Organisation**.
3. Fill in:
   - Organisation Name
   - Organisation Type (university, research institute, national lab, etc.)
   - Country and City
   - Website URL
   - Logo URL (optional)
4. Click **Save Organisation**.

**Step 2 — Link to your Access Profile:**
1. Go to **Access & Membership**.
2. In your profile, the `institution_name` field should now match the org you created.
3. If not, click **Edit Profile** and select the organisation from the dropdown.

---

## 6. How to Manage Institutional Members

**Route:** `/InstitutionalDashboard` → Members tab

1. Open the **Institutional Dashboard**.
2. Click the **Members** tab.
3. The table shows all users associated with your institution.
4. To **add a member**:
   - Click **Add Member**.
   - Enter the user's email address.
   - They receive an invitation; once accepted, they appear in the list.
5. To **remove a member**:
   - Click the member's row.
   - Click **Remove from Organisation**.
   - Confirm the dialog.
6. Members can be assigned the `institutional` account type by the admin via **Access & Membership**.

---

## 7. How to View Org-Level Analytics

**Route:** `/InstitutionalDashboard` → Overview tab

1. Navigate to **Institutional Dashboard**.
2. The **Overview Cards** show:
   - Total members
   - Active compute sites registered under the org
   - Total jobs completed by org members
   - Publications authored by org members
3. The **Contribution Summary** section shows the org's total contribution score and ledger entries.
4. Switch to the **Sites** tab to see all compute sites linked to the organisation.
5. Switch to the **Analytics** tab for charts of job volume and contribution trends over time.

---

## 8. How to Log Out

**Via Sidebar:**
1. Scroll to the **bottom of the sidebar**.
2. Click the **Logout** button (door/arrow icon).
3. You are immediately logged out and redirected to the **Landing** page.

**Via SDK (developers):**
```js
await base44.auth.logout('/Landing');
```

**Session behaviour:**
- Sessions persist across browser refreshes until you explicitly log out.
- Closing the browser tab does **not** log you out.
- If your session expires, you are automatically redirected to the login page.