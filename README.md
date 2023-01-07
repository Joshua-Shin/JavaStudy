자바 개념을 기록하는 저장소 입니다.
---------------------

### Comparable, Comparator, 익명클래스, 람다식 회상용 구현 문제
1. Person 클래스를 정의 해서 TreeSet에 담아 오름차순으로 정렬 해라.
2. Comparator를 구현한 클래스를 활용하여 내림차순으로 정렬해라.
3. Comparator를 구현할때 익명클래스를 활용해라.
4. Comparator를 구현할때 람다식을 활용해라.
5. Comparator를 구현할때 메소드 참조를 활용해라.

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

--------------------

