The squared norm of the error vector $\mathbf{e}$ is:
\begin{align}
    ||\mathbf{e}||_2^2 &= \\
    &= \left(\mathbf{x} - \frac{\mathbf{p}^T\mathbf{x}}{\mathbf{p}^T\mathbf{p}}\mathbf{p}\right)^T\left(\mathbf{x} - \frac{\mathbf{p}^T\mathbf{x}}{\mathbf{p}^T\mathbf{p}}\mathbf{p}\right)\\
    &= \mathbf{x}^T\mathbf{x} + \left(\frac{\mathbf{p}^T\mathbf{x}}{\mathbf{p^T}\mathbf{p}}\right)^2 \mathbf{p}^T\mathbf{p} - 2\left(\frac{\mathbf{p}^T\mathbf{x}}{\mathbf{p}^T\mathbf{p}}\right)\mathbf{p}^T\mathbf{x}\\
    &= \mathbf{x}^T\mathbf{x} + \frac{\left(\mathbf{p}^T\mathbf{x}\right)^2}{\mathbf{p}^T\mathbf{p}} - 2\frac{\left(\mathbf{p}^T\mathbf{x}\right)^2}{\mathbf{p}^T\mathbf{p}}\\
    &= \mathbf{x}^T\mathbf{x} - \frac{\left(\mathbf{p}^T\mathbf{x}\right)^2}{\mathbf{p}^T\mathbf{p}}\\
    &= \mathbf{x}^T\mathbf{x} - \frac{\mathbf{p}^T\mathbf{x}\mathbf{x}^T\mathbf{p}}{\mathbf{p}^T\mathbf{p}}\\
\end{align}