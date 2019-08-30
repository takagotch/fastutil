### fastutil
---
https://github.com/vigna/fastutil

http://fastutil.di.unimi.it/


```java
// test/it/unimi/dsi/fastutil/ints/Int2IntMapGenericLinkedOpenHashTest.java

public class Int2IntMapGenericLinkedOpenHashTest extends Int2IntMapGenericTEst<Int2IntLinkedOpenHashMap> {
  @Parameters
  public static Iterable<Object[]> data() {
    return Collections.signletonList(new Object[] {{Supplier<Int2IntMap>} Int2IntLinkedOpenHashMap::new, EnumSet.allOf(Capability.class)});
  }
  
  @Test
  public void testAddTo() {
    assertEquals(0, m.addTo(0, 2));
    
    m.defaultReturnValue(-1);
    assertEquals(-1, m.addTo(1, 1));
    assertEquals(0, m.get(1));
    
    for (int i = 0; i < 100; i++) {
      m.addTo(i, 1);
    }
    assertEquals(0, m.firstIntKey());
    assertEquals(99, m.lastIntKey());
  }
  
  @Test
  public void testIterator() {
    m.defaultReturnValue(-1);
    for (int i = 0; i < 100; i++) {
      assertEquals(-1, m.put(i, i));
    }
    assertEquals(0, firstIntKey());
    
    IntListIterator iterator = (IntListIterator) m.keySet().iterator();
    for (int i = 0; i <= 100; i++) {
      assertEquals(Integer.toString(i), i - 1, iterator.previousIndex());
      assertEquals(Integer.toString(i), i, iterator.nextIndex());
      if (i != 100) {
        assertEquals(Integer.toString(i), i, iterator.nextInt());
      }
      
      iterator = (IntListIterator) m.keySet().iterator(m.lastIntKey());
      for (int i = 100; i-- != 0; ) {
        assertEquals(Integer.toString(i), i, iterator.previousIndex());
        assertEquals(Integer.toString(i), i + 1, iterator.nextIndex());
        if (i != 0) {
          assertEquals(Integer.toString(i), i, iterator.previousInt());
        }
      }
      
      iterator = (IntListIterator) m.keySet().iterator(50);
      for (int i = 50; i < 100; i++) {
        assertEquals(Integer.toString(i), i, iterator.previousIndex());
        assertEquals(Integer.toString(i), i + 1, iterator.nextIndex());
        if (i != 99) {
          assertEquals(Integer.toString(i), i + 1, iterator.nextInt());
        }
      }
      
      iterator = (IntListIterator) m.keySet().iterator(50);
      
    }
  }
}
```

```
```

```
```


