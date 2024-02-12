- Polimorfismo
```java
Shape c = new Circle();
Shape r = new Rectangle();
Shape t = new Triangle();

List<Shape> figure = new List<Shape>();

figure.Add(c);
figure.Add(r);
figure.Add(t);
```

- Collegamento dinamico
```java
foreach (Shape x in figure)
	x.Draw();
```
