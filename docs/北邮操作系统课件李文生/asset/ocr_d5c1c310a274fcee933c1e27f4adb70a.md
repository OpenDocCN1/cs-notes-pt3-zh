# 9.3 Copy-on-Write—process creation

+   - Copy-on-Write (COW) allows both parent and child processes to initially *share* the same pages in memory

If either process modifies a shared page, only then is the page copied.

+   - COW allows more efficient process creation as only modified pages are copied. (see P.326 Figure9.7-9.8)

+   - Free pages are allocated from a *pool* of zeroed-out pages.