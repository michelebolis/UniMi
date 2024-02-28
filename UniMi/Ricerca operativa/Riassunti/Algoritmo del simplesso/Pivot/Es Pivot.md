Data la forma canonica

| Vincolo | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $x_5$ |
| ------- | ----- | ----- | ----- | ----- | ----- |
| 0       | -1    | -2    | 0     | 0     | 0     |
| 8       | -1    | 2     | 1     | 0     | 0     |
| 10      | 1     | 1     | 0     | 1     | 0     |
| 7       | 1     | 0     | 0     | 0     | 1     |

1. Scelgo 2, quindi riga = 1, colonna=2

| Vincolo | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $x_5$ |
| ------- | ----- | ----- | ----- | ----- | ----- |
| 0       | -1    | -2    | 0     | 0     | 0     |
| 8       | -1    | ==2== | 1     | 0     | 0     |
| 10      | 1     | 1     | 0     | 1     | 0     |
| 7       | 1     | 0     | 0     | 0     | 1     |

2. Divido la riga 1 per il pivot, quindi 2

| Vincolo | $x_1$          | $x_2$ | $x_3$          | $x_4$ | $x_5$ |
| ------- | -------------- | ----- | -------------- | ----- | ----- |
| 0       | -1             | -2    | 0              | 0     | 0     |
| 4       | $-\frac{1}{2}$ | ==1== | $-\frac{1}{2}$ | 0     | 0     |
| 10      | 1              | 1     | 0              | 1     | 0     |
| 7       | 1              | 0     | 0              | 0     | 1     |

3. Sottraggo ad ogni riga tranne la 1, la riga 1 moltiplicata per $a_{ic}$

| Vincolo | $x_1$ | $x_2$ | $x_3$ | $x_4$ | $x_5$ |
| ------- | ----- | ----- | ----- | ----- | ----- |
| 8       | -2    | 0     | 1     | 0     | 0     |
| 4       | -1/2  | ==1== | 1/2   | 0     | 0     |
| 6       | 3/2   | 1     | -1/2  | 1     | 0     |
| 7       | 1     | 0     | 0     | 0     | 1     |

Per la riga 0, $a_{ic}=-2$, infatti $$x_1 =  -1-(-2*-\frac{1}{2}) = -2$$
Entra in base la colonna del pivot, quindi la 2 ed esce dalla base la colonna corrispondente alla riga del pivot, cioe la 1

| Vettore delle x | |  z   |  |
| --------------- | ---| --- | --- |
| prima | dopo | prima | dopo | 
| 0     | 0    | 0 | -8 | 
| 0     | 4    | | |
| 8     | 0    | | |
| 10    | 6    | | |
| 7     | 7    |                |     |
