# Bug Report

This is a report of all Tokay bugs found during the AOC2022


## Expected identifier, found reserved word 'else'

Bug `Line 2, column 18: Expected identifier, found reserved word 'else'`:
```
x = 1
x += if x > 0 -1 else 1
```

Workaround:
```
x = 1
x += if x > 0 (-1) else 1
```

## Loops alone in a block break

Bug (loop is always only executed once!):
```
Int {
    for i = 0; i < $1; i++ {
        print(i)
    }
}
```

Workaround:
```
Int {
    void
    for i = 0; i < $1; i++ {
        print(i)
    }
}
```

## Misleading behavior with methods

### Example 1

Bug `Line 3, column 6: Method 'int_add' not found`:
```
l = (1 2 3)
i = l.len     # returns a method call to l.len, not the result
i += 5
```

Workaround I:
```
l = (1 2 3)
i = l.len()
i += 5
```

Workaround 2:
```
l = (1 2 3)
i = l.len
i = i + 5
```

### Example 2

Bug `Line 2, column 14: Method 'method_len' not found`:
```
d = (a => 1, b => 2, c => 3)
print(d.keys.len)
```

Workaround:
```
d = (a => 1, b => 2, c => 3)
print(d.keys().len)
```

## Crash when invalid character class is specified

Bug:
```
monkey = []
```

## Value sequence item always takes highest precedence

Bug:
```
i => Ident _ v => {
    _ '=' _ {
        Int
        ('true' true | 'false' false)
    }+
}+ print($i, $v)

#--- or equally with same result ---

i => Ident _ v => {
    _ '=' _ (Int | ('true' true | 'false' false))+
}+ print($i, $v)
```

- Given the input: `x = 1 = 2 = 3` it outputs `x (1, 2, 3)`
- Given the input: `x = 1 = true = false = 4` it outputs `x (true, false)`

Workaround (does only partly work):
```
i => Ident _ v => {
    _ '=' _ (Int $6 | ('true' true | 'false' false))+
}+ print($i, $v)
```

Workaround (does fully work):
```
i => Ident _ v => {
    _ '=' _ (i => Int $i | ('true' true | 'false' false))+
}+ print($i, $v)
```
