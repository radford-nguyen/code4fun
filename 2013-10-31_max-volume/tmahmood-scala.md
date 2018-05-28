My attempt in scala

```scala
  def calculateVolume(v: Vector[Int]): Int = {
    def calc(startIndex: Int, index: Int, minSoFar: Int): List[Int] = {
      if (index == v.length) Nil
      else if (startIndex == -1 && v(index) < v(index - 1)) {
        if (v(index) < minSoFar) calc(index - 1, index + 1, v(index))
        else calc(index - 1, index + 1, minSoFar)
      } else if (startIndex != -1 && (v(index) >= v(startIndex) || (index == v.length - 1 && v(index) >= minSoFar))) {
        val min = if (v(startIndex) <= v(index)) v(startIndex) else v(index)
        (for (j <- startIndex + 1 until index; if (min - v(j) > 0)) yield min - v(j)).toList ++ calc(-1, index + 1, Integer.MAX_VALUE)
      } else if (startIndex != -1 && v(index) < minSoFar) {
        calc(startIndex, index + 1, v(index))
      } else {
        calc(startIndex, index + 1, minSoFar)
      }
    }
    calc(-1, 1, Integer.MAX_VALUE) match {
      case Nil => 0
      case xs => xs.reduce(_ + _)
    }

  }
```

## Submitted by

Tabiul Mahmood
2013/11/01
