# JAVA8 함수형 인터페이스(Functional Interface) 종류

## Supplier<T>

#### 파라미터는 없고, 리턴타입은 있는 메서드를 갖음

~~~
/*
Supplier<String> supplier = new Supplier<String>() {
    @Override
    public String get() {
        return "hello world";
    }
};
*/

Supplier<String> supplier = () -> "hello world";
String result = s.get();
~~~

---

## Consumer<T>

#### 1개의 파라미터가 있고, 리턴타입은 없는 메서드를 갖음

~~~
/*
Consumer<String> consumer = new Consumer<String>() {
    @Override
    public void accept(String text) {
        System.out.println(text);
    }
};
*/

Consumer<String> consumer = System.out::println;
consumer.accept("hello world");
~~~

---

## BiConsumer<T, U>

#### 2개의 서로 다른 타입의 파라미터가 있고, 리턴타입은 없는 메서드를 갖음

~~~
/*
BiConsumer<Integer, Integer> biConsumer = new BiConsumer<Integer, Integer>() {
    @Override
    public void accept(Integer num1, Integer num2) {
        System.out.println(num1 + num2);
    }
};
*/

BiConsumer<Integer, Integer> biConsumer = (num1, num2) -> System.out.println(num1 + num2);
biConsumer.accept(2, 4);
~~~

---

## Function<T, R>

#### 1개의 파라미터가 있고, 리턴타입도 있는 메서드를 갖음

~~~
/*
Function<Integer, String> function = new Function<Integer, String>() {
    @Override
    public String apply(Integer num) {
        return String.valueOf(num);
    }
};
*/

Function<Integer, String> function = String::valueOf;
String result = function.apply(4);
~~~

---

## BiFunction<T, U, R>

#### 2개의 서로 다른 타입의 파라미터가 있고, 리턴타입도 있는 메서드를 갖음

~~~
/*
BiFunction<Integer, Integer, String> biFunction = new BiFunction<Integer, Integer, String>() {
    @Override
    public String apply(Integer num1, Integer num2) {
        return String.valueOf(num1 + num2);
    }
};
*/

BiFunction<Integer, Integer, String> biFunction = (num1, num2) -> String.valueOf(num1 + num2);
String result = biFunction.apply(2, 4);
~~~

---

## Predicate<T>

#### 1개의 파라미터가 있고, 리턴타입은 boolean 인 메서드를 갖음

~~~
/*
Predicate<Integer> predicate = new Predicate<Integer>() {
    @Override
    public boolean test(Integer num) {
        return num == 4;
    }
};
*/

Predicate<Integer> predicate = num -> num == 4;
boolean result = predicate.test(2);
~~~

---

## BiPredicate<T, U>

#### 2개의 서로 다른 타입의 파라미터가 있고, 리턴타입은 boolean 인 메서드를 갖음

~~~
/*
BiPredicate<String, String> biPredicate = new BiPredicate<String, String>() {
    @Override
    public boolean test(String text1, String text2) {
        return text1.equals(text2);
    }
};
*/

BiPredicate<String, String> biPredicate = String::equals;
boolean result = biPredicate.test("hello", "hello");
~~~

---

## UnaryOperator<T>

#### 1개의 파라미터가 있고, 리턴타입도 있는 메서드를 갖음(파라미터와 리턴타입이 동일)

~~~
/*
UnaryOperator<String> unaryOperator = new UnaryOperator<String>() {
    @Override
    public String apply(String text) {
        return text + " world";
    }
};
*/

UnaryOperator<String> unaryOperator = text -> text + " world";
String result = unaryOperator.apply("hello");

~~~

---

## BinaryOperator<T>

#### 2개의 파라미터가 있고, 리턴타입도 있는 메서드를 갖음(2개의 파라미터와 리턴타입이 동일)

~~~
/*
BinaryOperator<Integer> binaryOperator = new BinaryOperator<Integer>() {
    @Override
    public Integer apply(Integer num1, Integer num2) {
        return num1 + num2;
    }
};
*/

BinaryOperator<Integer> binaryOperator = (num1, num2) -> num1 + num2;
int result = binaryOperator.apply(2, 4);
~~~

---