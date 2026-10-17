# # Proof of the theorem

# ## Proof.

+   - At least one probe is always necessary.

+   - With probability _n/m_, the first probe hits an occupied slot, and a second probe is necessary.

+   - With probability (_n_-1)/(_m_-1), the second probe hits an occupied slot, and a third probe is necessary.

+   - With probability (_n_-2)/(_m_-2), the third probe hits an occupied slot, etc.

Observe that \(\frac{n-i}{m-i}<\frac{n}{m}=\alpha\) for _i_=1,2,...,n.