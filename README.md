자바 개념을 회상하기 위해 기록하는 저장소 입니다.
---------------------

### Comparable, Comparator, 익명클래스, 람다식 회상용 구현 문제
1. Person 클래스를 정의 해서 TreeSet에 담아 오름차순으로 정렬 해라.
2. Comparator를 구현한 클래스를 활용하여 내림차순으로 정렬해라.
3. Comparator를 구현할때 익명클래스를 활용해라.
4. Comparator를 구현할때 람다식을 활용해라.
<details>
    <summary>정답</summary>

```
public class TreeSetTest {
    public static void main(String[] args) {
        Set<Person> set = new TreeSet<>(new PersonComparator());
        Set<Person> set2 = new TreeSet<>(new Comparator<>() {
            public int compare(Person p1, Person p2) {
                return -(p1.getAge() - p2.getAge());
            }
        });
        Set<Person> set3 = new TreeSet<>(
            (p1, p2) -> -(p1.getAge() - p2.getAge())
        );
    }
}
class Person implements Comparable<Person> {
    private int age;
    Person(int age) {
        this.age = age;
    }
    public int getAge() {
        return age;
    }
    @Override
    public int compareTo(Person o) {
        return this.age - o.age;
    }
}
class PersonComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return -(p1.getAge() - p2.getAge());
    }
}
```

</details>
    
-------------------

### 상한 제한, 하한 제한 개념 회상 문제
```
public void outBox(Box<? extends Toy> box) {
    Toy t = box.get();
    // box.set(new Toy()); 컴파일 오류
}
public void inBox(Box<? super Toy> box, Toy n) {
    box.set(n);
    // box.get(); 컴파일 오류
}
```
1. outBox 메소드에 몸체에 set을 넣으면 컴파일 오류가 나는 이유를 설명해라.
2. inBox 메소드 몸체에 get을 넣으면 컴파일 오류가 나는 이유를 설명해라.
<details>
    <summary>정답</summary>

- 4개의 클래스가 다음과 같다고 가정
- Product, Toy, Car, Robot
- Toy extends Product
- Car extends Toy
- Robot extends Toy
- Box<Toy> 의 경우 Toy와 Car, Robot을 담을 수 있음
- Box<Car> 의 경우 Car를 담을 수 있음
- Box<Robot>의 경우 Robot을 담을 수 있음
- Box<? extends Toy> 의 경우 ? 에 Toy, Car, Robot이 올 수 있음
- Toy가 오면 다행이지만, Car가 올 경우 Toy나 Robot을 담을 수 없게됨.
- 컴파일러는 어떠한 상황이든 가능할때 컴파일이 됨.
- 때문에 Box<? extends Toy>는 set 기능이 제한됨.
- 단, get의 경우 Toy 타입의 참조변수로 Toy든, Car든 Robot이든 어떤 구현체든 다 참조 할 수 있기 떄문에 get은 가능
- Box<? super Toy> 의 경우 ? 에 Toy, Product가 올 수 있음
- Product이 오든 Toy가 오든 Toy 를 포함한 하위 클래스들을 다 담을 수 있기에 set은 가능
- 단 get의 경우 Product 구현체를 꺼낼 경우 Toy 타입의 참조변수로 참조할 수 없음.
- 따라서 get은 기능이 제한됨.

</details>
-------------------

### 컬렉션 프레임워크
1. 컬렉션 프레임워크의 상속 구조를 그려라.
[정답](https://www.javatpoint.com/collections-in-java)

-------------------

### sort 메소드의 매개변수 해석 문제
1. Collections 의 static 메소드인 sort가 아래의 소스코드 에서 첫째줄이 아니라 둘째줄인 이유가 무엇인지 설명해라.
```
public static <T extends Comparable<T>> void sort(List<T> list)
public static <T extends Comparable<? super T>> void sort(List<T> list) 
```
<details>
    <summary>정답</summary>
    
- 두개의 클래스가 있다
- Car, ECar
- Car implements Comparable<Car>
- ECar extends Car
- 만약 sort 메소드가 두번째줄로 정의 되어 있었다면,
- Comparable<Car>를 구현하는 Car 클래스는 sort의 매개 타입으로 들어갈 수 있으나,
- Comparable<ECar>를 따로 구현하고 있지 않은 ECar 클래스는 sort의 매개 타입으로 들어갈 수 없다.
- ECar는 Comparable<Car>를 간접 구현하고 있으며, 따라서 이러한 상황에서 ECar가 매개 타입으로 들어가려면, 
- sort 메소드의 정의는 두번째 줄이여야 한다.

</details>
