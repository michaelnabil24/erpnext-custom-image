# erpnext-custom-image

Custom ERPNext v16 image for erpnext.ainzm.com (Dokploy on hcp.michaelnabil.com).

| App | Branch |
|---|---|
| erpnext | version-16 |
| hrms (Frappe HR + Payroll) | version-16 |
| telephony (required by helpdesk) | develop |
| helpdesk | version-16 |
| erpnext_egypt_compliance (Axentor ETA) | version-16 |

## Build
GitHub → Actions → "Build ERPNext custom image" → Run workflow.
The image is pushed to `ghcr.io/<owner>/erpnext-custom:version-16` plus a dated tag `v16-YYYYMMDD-<sha>`.

## Add or update an app
Edit `apps.json` and push to `main`: the workflow rebuilds automatically.

## Use in Dokploy
Environment of the `erpnext-v16` compose:

```
IMAGE_NAME=ghcr.io/<owner>/erpnext-custom
VERSION=v16-YYYYMMDD-<sha>
```

Then deploy, and install the new apps on the site once (backend container terminal):

```
bench --site erpnext.ainzm.com install-app hrms telephony helpdesk erpnext_egypt_compliance
```
