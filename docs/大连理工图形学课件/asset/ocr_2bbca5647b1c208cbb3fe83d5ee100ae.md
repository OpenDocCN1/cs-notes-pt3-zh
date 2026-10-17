# # 1) David F. Rogers 描述

// Digital Differential Analyzer (DDA ) routine for rasterizing a line

// The line end points are (xs,ys) and (xe,ye) assumed not equal.

// Round is the function. Note: Many Round functions are floor functions, i.e Round (-8.5)=-9 rather than -8. The algorithm assumes this is the case.

// Approximate the line length

If (|xs- xe | ≥ | ys-ye |) then //插补长度 Length ← |xs- xe |; else Length ← | ys-ye |; end if