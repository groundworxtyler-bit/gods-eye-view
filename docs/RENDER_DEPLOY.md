# Deploy this God's Eye View fork on Render

This fork includes a Render Blueprint (`render.yaml`) that runs the **existing** Dockerfile and the app's Node/Vite server rather than publishing a broken static copy.

## Fast setup

1. Sign in to [Render](https://dashboard.render.com/) with an account you control.
2. Go to [New > Blueprint](https://dashboard.render.com/select-repo?type=blueprint), connect GitHub, and choose `groundworxtyler-bit/gods-eye-view`.
3. Render reads `render.yaml`. Review the **Free** plan and select **Apply/Deploy**. Do not add any API keys.
4. Once the service is marked **Live**, open the actual `https://...onrender.com` URL displayed in Render. Bookmark it or use Safari's **Share > Add to Home Screen**.

**Important limitations:** The free service can spin down after 15 minutes of inactivity and cold start on the next visit. It is not guaranteed to be available instantly or 24/7. It also has 512 MB memory and may be too small for this large app; if builds or runtime fail with out-of-memory, an appropriate paid tier or a lighter deployment is needed. Free services can have monthly limits.

**Security:** This creates an **internet-accessible** public website. God's Eye View is local-first and is not documented by upstream as a hardened production service. Keep it keyless as configured; do not add paid provider credentials without putting authentication in front of the whole service and configuring limits/quotas. The Blueprint disables gateway-based access to Provider Settings and restricts Vite to the actual Render hostname. Avoid committing any `.env` or credentials. See upstream [SECURITY.md](../SECURITY.md).

**Data and provider caveat:** Some data feeds can block hosting providers or have use/licensing limitations. Publicly hosted use is subject to their terms. Local data caches are ephemeral on the Free plan.

To switch to truly always-on hosting, select an appropriate paid instance plan after reviewing recurring costs. Do not assume the cheapest tier has adequate memory.
