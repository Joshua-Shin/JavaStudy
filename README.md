자바 개념을 기록하는 저장소 입니다.
---------------------

### Comparable, Comparator, 익명클래스, 람다식 회상용 구현 문제
Q1. Person 클래스를 정의 해서 TreeSet에 담아 오름차순으로 정렬 해라.
Q2. Comparator를 구현한 클래스를 활용하여 내림차순으로 정렬해라.
Q3. Comparator를 구현할때 익명클래스를 활용해라.
Q4. Comparator를 구현할때 람다식을 활용해라.
    <details>
        <summary> 정답</summary>

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


### 상향 제한, 하향 제한 개념 회상 문제
```
public void outBox(Box<? extends Toy> box) {
        Toy t = box.get();
        System.out.println(t);
}
public void inBox(Box<? super Toy> box, Toy n) {
    box.set(n);
}

```
Q1. outBox 메소드에 몸체에 set을 넣을 수 없는 이유를 설명해라.
Q2. inBox 메소드 몸체에 get을 넣을 수 없는 이유을 설명해라.
