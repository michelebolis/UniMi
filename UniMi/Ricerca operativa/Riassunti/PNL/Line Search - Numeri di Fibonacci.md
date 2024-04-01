La sequenza dei numeri di Fibonacci inizia con $F_0=0$ e $F_1=1$ e si ricava con la ricorsione $F_k=F_{k-1}+F_{k-2}$

Proprieta: dati 4 numeri di Fibonacci consecutive a partire dal k-esimo, si ha
$$F_{k+1}F_{k+2}-F_{k}F_{k+3}=(-1)^k, \forall k\geq 0 $$
DIM per induzione
- Base $k =0$
$$F_1F_2-F_0F_3=1*1-0*2=1^0$$
- Passo induttivo: da $k-1$ a $k$ per ogni $k \geq 1$
$$F_kF_{k+1}-F_{k-1}F_{k+2} = (-1)^{k-1}$$
$$F_{k+1}F_{k+2}-F_{k}F_{k+3} = (-1)^{k}$$
Infatti
$F_{k+1}F_{k+2}-F_{k}F_{k+3} = [F_{k+1}(F_k+F_{k+1})]-[F_k(2F_{k+1}+F_k)] =$
$= F_kF_{k+1}+F^2_{k+1}-2F_kF_{k+1}-F^2_{k} = (F^2_{k+1}-F^2_K)-F_kF_{k+1} =$
$=(F_{k+1}+F_k)(F_{k+1}-F_k)-F_kF_{k+1}=F_{k+2}F_{k-1}-F_kF_{k+1} =$
$=-(-1)^{k-1}=(-1)^k$