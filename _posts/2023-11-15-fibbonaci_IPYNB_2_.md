---

---

```java
public class FiboWhile extends Fibo {

    public FiboWhile() {
        super();
    }

    public FiboWhile(int nth) {
        super(nth);
    }

    @Override
    protected void init() {
        super.name = "While Extends";
        long limit = this.size;

        long a = 0, b = 1;
        this.setData(a);

        if (limit > 1) {
            this.setData(b);
        }

        int count = 2;
        while (count < limit) {
            long temp = a + b;
            this.setData(temp);

            a = b;
            b = temp;

            count++;
        }
    }

    /*
    Tester class method.
     */
    static public void main(String[] args) {
        FiboWhile fib = new FiboWhile();
        fib.print();
    }
}

FiboWhile.main(null);

```

    Init method = While Extends
    fibonacci Number 8 = 13
    fibonacci List = [0, 1, 1, 2, 3, 5, 8, 13]
    fibonacci Hashmap = {0=[0], 1=[0, 1], 2=[0, 1, 1], 3=[0, 1, 1, 2], 4=[0, 1, 1, 2, 3], 5=[0, 1, 1, 2, 3, 5], 6=[0, 1, 1, 2, 3, 5, 8], 7=[0, 1, 1, 2, 3, 5, 8, 13]}
    fibonacci Sequence 1 = [0]
    fibonacci Sequence 2 = [0, 1]
    fibonacci Sequence 3 = [0, 1, 1]
    fibonacci Sequence 4 = [0, 1, 1, 2]
    fibonacci Sequence 5 = [0, 1, 1, 2, 3]
    fibonacci Sequence 6 = [0, 1, 1, 2, 3, 5]
    fibonacci Sequence 7 = [0, 1, 1, 2, 3, 5, 8]
    fibonacci Sequence 8 = [0, 1, 1, 2, 3, 5, 8, 13]



```java
public class FiboRecursive extends Fibo {

    public FiboRecursive() {
        super();
    }

    public FiboRecursive(int nth) {
        super(nth);
    }

    @Override
    protected void init() {
        super.name = "Recursive Extends";
        for (int i = 0; i < this.size; i++) {
            this.setData(fibonacci(i));
        }
    }

    private long fibonacci(int n) {
        if (n <= 1) {
            return n;
        }
        return fibonacci(n - 1) + fibonacci(n - 2);
    }

    /*
    Tester class method.
     */
    static public void main(String[] args) {
        FiboRecursive fib = new FiboRecursive();
        fib.print();
    }
}

FiboRecursive.main(null);

```

    Init method = Recursive Extends
    fibonacci Number 8 = 13
    fibonacci List = [0, 1, 1, 2, 3, 5, 8, 13]
    fibonacci Hashmap = {0=[0], 1=[0, 1], 2=[0, 1, 1], 3=[0, 1, 1, 2], 4=[0, 1, 1, 2, 3], 5=[0, 1, 1, 2, 3, 5], 6=[0, 1, 1, 2, 3, 5, 8], 7=[0, 1, 1, 2, 3, 5, 8, 13]}
    fibonacci Sequence 1 = [0]
    fibonacci Sequence 2 = [0, 1]
    fibonacci Sequence 3 = [0, 1, 1]
    fibonacci Sequence 4 = [0, 1, 1, 2]
    fibonacci Sequence 5 = [0, 1, 1, 2, 3]
    fibonacci Sequence 6 = [0, 1, 1, 2, 3, 5]
    fibonacci Sequence 7 = [0, 1, 1, 2, 3, 5, 8]
    fibonacci Sequence 8 = [0, 1, 1, 2, 3, 5, 8, 13]


# Solve Fibonacci using two additional algorithms.


```java
public class FiboDynamic extends Fibo {

    public FiboDynamic() {
        super();
    }

    public FiboDynamic(int nth) {
        super(nth);
    }

    @Override
    protected void init() {
        super.name = "Dynamic Extends";
        if (this.size > 0) {
            this.setData(0); // First Fibonacci number
        }
        if (this.size > 1) {
            this.setData(1); // Second Fibonacci number
        }

        long prev = 0, curr = 1;
        for (int i = 2; i < this.size; i++) {
            long next = prev + curr;
            this.setData(next);
            prev = curr;
            curr = next;
        }
    }

    public static void main(String[] args) {
        FiboDynamic fib = new FiboDynamic(10); // Example for 10 numbers
        fib.print();
    }
}

FiboDynamic.main(null);

```

    Init method = Dynamic Extends
    fibonacci Number 10 = 34
    fibonacci List = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
    fibonacci Hashmap = {0=[0], 1=[0, 1], 2=[0, 1, 1], 3=[0, 1, 1, 2], 4=[0, 1, 1, 2, 3], 5=[0, 1, 1, 2, 3, 5], 6=[0, 1, 1, 2, 3, 5, 8], 7=[0, 1, 1, 2, 3, 5, 8, 13], 8=[0, 1, 1, 2, 3, 5, 8, 13, 21], 9=[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]}
    fibonacci Sequence 1 = [0]
    fibonacci Sequence 2 = [0, 1]
    fibonacci Sequence 3 = [0, 1, 1]
    fibonacci Sequence 4 = [0, 1, 1, 2]
    fibonacci Sequence 5 = [0, 1, 1, 2, 3]
    fibonacci Sequence 6 = [0, 1, 1, 2, 3, 5]
    fibonacci Sequence 7 = [0, 1, 1, 2, 3, 5, 8]
    fibonacci Sequence 8 = [0, 1, 1, 2, 3, 5, 8, 13]
    fibonacci Sequence 9 = [0, 1, 1, 2, 3, 5, 8, 13, 21]
    fibonacci Sequence 10 = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]

