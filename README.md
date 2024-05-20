# sys-devel/llvm patches
Building the kernel with LLVM=1 crashes LLD with LLVM >= 18

The relevant issue is llvm/llvm-project#82431

These patches correspond to two PRs: llvm/llvm-project#82881 and llvm/llvm-project#85081. The first one is already merged to main branch, the second isn't. These patches are just the two commits from the pull requests cherry-picked on the 18.1.5 and 18.1.6 tags.
