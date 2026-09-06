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

*ideas auxiliares*

pred esIdVálido(in ID:id):Bool = ID >= 0; 

proc esUsuarioNuevoVálido(in clave:id,in valor:tupla<historial,emisiones>):bool{

    req{True}
    asegura{res = True <-> esIdVálido(clave) ∧ (|valor_0| = 0 ∧ |valor_1| = 0)}
}

proc esUsuarioRegistradoVálido(in clave:id,in valor:tupla<historial,emisiones>):bool{

    req{True}
    asegura{res = True <-> esIdVálido(clave) ∧ esHistorialVálido(historial) ∧ todasLasEmisionesVálidas(emisiones)}
}

    // el historial es válido si cada movimiento (type movimiento : struct<transacción,millas,código>) es válido
        
        // cada movimiento es válido si ... 
        // cada tupla de millas es válida si las 0<= disponibles >= 1000000 y totales>= 0;  
        // cada código es válido si es unico para todos los codigos q hay en en el historial y en el historial del resto de usuarios ya registrados

    // la secuencia de emsiones es válida si:
        
        // para todo ID' en la secuencia de emisiones se cumple que esta al menos una vez presente como receptor en el historial de transacciones del usuario 


proc esUsuarioVálido(in clave:id,in valor:tupla<historial,emisiones>):bool{

    req{True}
    asegura{res = True <-> esUsuarioNuevoVálido(clave,valor) ⊻ esUsuarioRegistradoVálido(clave,valor)} // ⊻ es xor u or exclusivo
}
 

> [!IMPORTANT]
>
> considero el uso de "emisiones" debido a que la exclusividad es solo en emision, no en recepccion, es decir, yo puedo percivir transferencias de otros usuarios, pero solo puedo y debo tener exclusividad en mis emisiones con el otro.
>
> att, es consideracion mia, deberiamos consultarlo, pero la imp es la misma.

>[!NOTE]
>este no es el docu de respuestas, son solo ideas propuestas en el lab!