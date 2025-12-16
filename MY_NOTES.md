1. Git never tracks empty Directory!
2. Simple analogy: VCS = Engine and SCM = Full vehicle (engine + controls + safety + process)
3. VCS tracks code changes; SCM manages how code is developed, reviewed, and released.
4. Git = tool (VCS)
5. GitHub = platform (SCM)
6. SCM = discipline/process
7. VCS = version tracking system
8. GIT SUBMODULES: Key Points to Remember

Submodules are separate Git repos inside your repo.

Your parent repo tracks a specific commit of the submodule, not the branch by default.

You need to update submodules manually after cloning or pulling changes.

Nested submodules (submodules inside submodules) are also possible with --recursive.

Visual Concept

ParentRepo/
│
├── main_code/
├── libs/
│   └── library/   <-- This is a submodule (tracks its own Git repo)
└── README.md


ParentRepo only tracks which commit of library it is using.

The library repo can evolve independently, and you can update the commit in the parent when ready.

💡 Tip: Submodules are perfect when you reuse libraries across multiple projects, but if you want a simpler approach, sometimes just copying the code or using Git subtree might be easier




