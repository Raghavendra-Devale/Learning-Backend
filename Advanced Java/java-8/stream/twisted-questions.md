# Java Streams — Twisted / Trap Questions

---

1. Will this execute?

   list.stream().map(String::toUpperCase);

   Answer:
   No terminal operation.

---

2. What happens here?

   Stream<String> s = list.stream();
   s.forEach(System.out::println);
   s.forEach(System.out::println);

   Answer:
   IllegalStateException.

---

3. Is this good practice?

   List<String> result = new ArrayList<>();
   list.stream().forEach(result::add);

   Answer:
   Works but violates functional style (side effects).

---

4. Why might distinct() fail to remove duplicates?

   equals() and hashCode() not overridden.

---

5. What happens if toMap has duplicate keys and no merge function?

   IllegalStateException.

---

6. Is parallelStream always faster?

   No.

---

7. Why can limit() stop early?

   It is short-circuiting.

---

End of Twisted Questions.
