## Pull Request (PR) Process Guidelines

### 1. Self-Review Before Creating a PR
- Review your own code thoroughly before requesting a review from others.
- Ask yourself whether the current state of the code is maintainable, follows best practices, and meets the project's coding standards.

### 2. Product Owner (PO) Approval
- **Before creating a PR to the ```development``` branch**, ensure that the Product Owner has accepted the work.
- This ensures that each task has been formally validated before proceeding.

### 3. Merging PRs and Workflow Sequence
- After approval from all reviewers, the **last reviewer** to approve the PR will be responsible for merging it into the ```development``` (Dev) branch.
- **Immediately** after merging into Dev, check if the feature works in ```development``` branch before creating a **new PR** to ```staging```. If it works create a new PR to staging ASAP to ensure that the PBI (Product Backlog Item) is merged one at a time, minimizing conflicts.

### 4. Checklist for PRs:
- Always include the **Acceptance Criteria** and **Definition of Done (DoD)** in the PR as a checklist.
  - Example Checklist:
    - Does the code meet the defined Acceptance Criteria?
    - Is the Definition of Done (DoD) fulfilled?
    - Has the Product Owner approved?
- Attach **pictures, videos, or GIFs** illustrating that the acceptance criteria are met.
  - For frontend work, include **screenshots** of the changes.

### 5. Code Quality and Review Etiquette
- Be **constructive** and **critical** of the code, focusing on **improving quality** rather than personal criticism.
- When reviewing, ask yourself: “Would I be comfortable working on this file in its current state?”

### 6. Keeping Up to Date
- **Pull the latest ```development``` branch** into your working branch before you request a code review to ensure compatibility and prevent conflicts.

### 7. Rotating Review Teams
- **Switch review teams weekly** to ensure a diverse range of feedback across all groups.
  - Example: Group 1 reviews for Group 2, Group 3 reviews for Group 4, and so on.
  - This enhances cross-group collaboration and knowledge sharing.

### 8. Dedicated PR Review Pairs
- **Each PR should be reviewed by a pair of teams**, with a minimum of two reviewers. At least **one reviewer must be from a different team**.
  - This rule ensures fresh perspectives and prevents group-specific biases.

### 9. Codescene Analysis
- **Before creating a PR**, run the branch through **Codescene** (or any similar tool) to detect any code quality or technical debt improvements.
- After running Codescene, ensure you **pull the latest ```development``` branch** into your working branch once again before creating the PR.

### 10. Review Deadlines
- Each PR must have a **clear deadline for review and merging**. Ensure the code is reviewed and merged promptly to avoid bottlenecks and allow continuous progress.

### 11. Acceptance Criteria Fulfillment
- Include **visual proof** (e.g., screenshots, GIFs) showing how the Acceptance Criteria are met for every PR.
- Ensure that the code is tested and **does not break existing functionality**.
- Add the criteria of ESlint passing the test on the front-end.

### 12. How to Push into Staging
- Open a PR for the ```staging``` branch and **use the provided template** from the resources folder.
- Ensure that **all tests pass** before finalizing the PR.
- Verify that the PR has **sufficient reviews**, meeting the minimum requirements (at least two reviewers, with one from another team).
- If the **staging deployment fails, it must be fixed immediately** before proceeding with any other PRs to staging. This ensures that the staging environment remains functional.
- If you push a **hotfix** directly to staging, **ensure that the ```development``` branch is also updated** to reflect those changes, maintaining consistency across environments.
