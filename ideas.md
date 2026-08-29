$$
\begin{aligned}
& type ~usuario: int \\
& type ~codigo: string \\
& type ~emisiones: list \langle usuario\rangle \\
& type ~transaccion: enum \langle emisior, receptor, vuelo, caje, referido\rangle\\
& type ~historial: list\langle struct\langle transaccion, monto, codigo\rangle\rangle \\
& type ~categoria: enum \langle bronce, plata, oro, platino\rangle \\
& \\
& \textbf{TAD}~\text{AirMiles}\langle\rangle \{ \\
& ~~~~obs~usuarios : dict\langle usuario, \langle historial, emisiones\rangle\rangle \\ 
& ~~~~obs~promocion : dict\langle codigo, tope\rangle \\
&\}
\end{aligned}
$$

> [!IMPORTANT]
>
> considero el uso de "emisiones" debido a que la exclusividad es solo en emision, no en recepccion, es decir, yo puedo percivir transferencias de otros usuarios, pero solo puedo y debo tener exclusividad en mis emisiones con el otro.
>
> att, es consideracion mia, deberiamos consultarlo, pero la imp es la misma.

>[!NOTE]
>este no es el docu de respuestas, son solo ideas propuestas en el lab!