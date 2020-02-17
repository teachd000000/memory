# JAVA8 Optional API 종류

## Optional<T> ofNullable(T value)

#### Optional 객체를 생성할 수 있음(파라미터로 null 값을 허용함)

~~~
Optional<Object> opt = Optional.ofNullable(null);
~~~

---

## Optional<T> of(T value)

#### Optional 객체를 생성할 수 있음(파라미터로 null 값을 허용하지 않음)

~~~
Optional<Object> opt = Optional.of(null);

// 위의 메서드를 실행할 경우, java.lang.NullPointerException 이 발생함
~~~

---

## Optional<T> empty()

#### 빈 Optional 객체를 생성할 수 있음

~~~
Optional<Object> opt = Optional.empty();
~~~

---

## boolean isPresent()

#### 객체가 null 일 경우, false 를 리턴함

~~~
boolean isPresent = Optional.ofNullable("hello").isPresent();
~~~

---

## void ifPresent(Consumer<T> consumer)

#### 객체가 null 아닐 경우, 메서드를 실행함

~~~
/*
Optional.ofNullable("hello").ifPresent(new Consumer<String>() {
	@Override
	public void accept(String text) {
		System.out.println(text);
	}
});
*/

Optional.ofNullable("hello").ifPresent(text -> System.out.println(text));
~~~

---

## Optional<U> map(Function<T, U> mapper)

#### 객체를 변경한 후, 리턴할 수 있음

~~~
/*
Optional<Integer> opt = Optional.ofNullable("hello")
		.map(new Function<String, Integer>() {
			@Override 
			public Integer apply(String text) { 
				return text.length(); 
			}
		});
*/

Optional<Integer> opt = Optional.ofNullable("hello").map(String::length);
~~~

---

## Optional<T> filter(Predicate<T> predicate)

#### 해당 조건을 만족하는 값만 필터링함

~~~
/*
Optional<String> opt = Optional.ofNullable("hello")
        .filter(new Predicate<String>() {
            @Override
            public boolean test(String text) {
                return text.equals("hi");
            }
        });
*/

Optional<String> opt = Optional.ofNullable("hello").filter(text -> text.equals("hi"));

// opt.get() 을 실행할 경우, java.util.NoSuchElementException: No value present 이 발생함
~~~

---

## T get()

#### 객체를 꺼냄

~~~
String text = Optional.ofNullable("hello").get();
~~~

---

## T orElse(T other)

#### 객체가 null 일 경우, 디폴트값을 리턴함

~~~
String text = Optional.ofNullable("hello").orElse("hi");
~~~

---

## T orElseGet(Supplier<T> other)

#### 객체가 null 일 경우, 디폴트값을 리턴함(디폴트값으로 함수를 파라미터로 받을 수 있음)

~~~
/*
String text = Optional.ofNullable("hello")
		.orElseGet(new Supplier<String>() {
			@Override
			public String get() {
				return "hi";
			}
		});
*/

String text = Optional.ofNullable("hello").orElseGet(() -> "hi");
~~~

---

## T orElseThrow(Supplier<U> exceptionSupplier)

#### 객체가 null 일 경우, 예외를 발생시킴

~~~
/*
String text = Optional.ofNullable("hello")
		.orElseThrow(new Supplier<NullPointerException>() {
			@Override
			public NullPointerException get() {
				return new NullPointerException();
			}
		});
*/

String text = Optional.ofNullable("hello").orElseThrow(NullPointerException::new);
~~~

---
