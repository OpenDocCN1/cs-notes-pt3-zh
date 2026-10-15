# Bounded Minimization Operator

Bounded search:

μz<y(f(\tilde{x},z)=0) ≜ { the least z < y, such that f(\tilde{x},z)=0; y, if there is no such z. }

# Proposition

If f(\tilde{x},z) is primitive recursive, then so is μz<y(f(\tilde{x},z)=0)

Proof

μz<y(f(\tilde{x},z)=0) = Σ_{v<y}(Π_{u<v+1} sg(f(\tilde{x},u)))