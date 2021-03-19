This post focuses on the similarities and differences between the **Proper Generalized Decomposition** (**PGD**) and the **Principal Component Analysis** (**PCA**).

Both Principal Component Analysis (PCA) and Proper Generalized Decomposition (PGD) are two mathematical tools that can be used as dimensionality reduction methods, but each one has a well-defined scope of application.

The main difference between them lies in the fact that PCA is applied directly to data sets, whereas PGD can only be applied to differential equations constrained by some boundary conditions (that is, boundary value problems--BVP) y no todas: su solución tiene que ser separable. That is, if your problem can not be expressed as a BVP, PGD is not for you!But in the case that it can, PGD requires you to perform a complex mathematical development with the equations, so you will still need paper and pencil.

Producto de matrices vs método iterativo. Ortogonalidad de los componentes principales.

SIMILITUDES
1. Pueden usarse como métodos de reducción de la dimensionalidad.
2. Como resultado se obtienen componentes principales (o modos).
3. Todas 
3. En algunas aplicaciones pueden usarse de manera combinada (como en mi paper de daño).

DIFERENCIAS
1. PCA es un método antiguo, PGD es un método reciente.