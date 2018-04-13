# substring() 的原理

1. 检查参数的合法性, 如果参数超出范围, 那么抛出 StringIndexOutOfBoundsException 异常
2. 根据 String 的编码方式, 调用 `newString()` 方法,  `newString()` 方法当中会调用 `Arrays.copyOfRange()`, `Arrays.copyOfRange()`会调用`System.arrayCopy()`, `System.arrayCopy()` 方法是虚拟机支持的,

*System.arrCopy()* 会拷贝 srcPoint --- srcPoint+length-1
