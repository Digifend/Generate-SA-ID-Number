# Luhn Algorithm for South African ID Numbers in 10 Different Coding Languages

The **Luhn Algorithm** is a simple checksum formula used to validate various identification numbers, including South African ID numbers. Below are implementations of the Luhn Algorithm in 10 popular programming languages, along with an analysis of their efficiency.

---

# Luhn Algorithm in Python

![Python](https://www.python.org/static/community_logos/python-logo.png)

```python
def calculate_luhn(id_number):
    digits = [int(d) for d in str(id_number)]
    checksum = 0
    reverse_digits = digits[::-1]

    for i, digit in enumerate(reverse_digits):
        if i % 2 == 1:
            doubled = digit * 2
            checksum += sum(divmod(doubled, 10))
        else:
            checksum += digit

    return (10 - (checksum % 10)) % 10

# Example usage
id_number = '800101500908'
checksum = calculate_luhn(id_number)
print(f"ID Number: {id_number}{checksum}")
```



# Luhn Algorithm in JavaScript

![JavaScript](https://www.javascript.com/images/icons/javascript.svg)

```javascript
function calculateLuhn(idNumber) {
    let digits = idNumber.split('').map(Number);
    let checksum = 0;
    let reverseDigits = digits.reverse();

    reverseDigits.forEach((digit, i) => {
        if (i % 2 === 1) {
            let doubled = digit * 2;
            checksum += Math.floor(doubled / 10) + (doubled % 10);
        } else {
            checksum += digit;
        }
    });

    return (10 - (checksum % 10)) % 10;
}

let idNumber = '800101500908';
let checksum = calculateLuhn(idNumber);
console.log(`ID Number: ${idNumber}${checksum}`);
```

# Luhn Algorithm in C++

![C++](https://isocpp.org/assets/images/cpp_logo.png)

```cpp
#include <iostream>
#include <string>
using namespace std;

int calculateLuhn(string idNumber) {
    int checksum = 0;
    int n = idNumber.size();

    for (int i = n - 1; i >= 0; i--) {
        int digit = idNumber[i] - '0';

        if ((n - i) % 2 == 0) {
            digit *= 2;
            if (digit > 9) digit -= 9;
        }

        checksum += digit;
    }

    return (10 - (checksum % 10)) % 10;
}

int main() {
    string idNumber = "800101500908";
    int checksum = calculateLuhn(idNumber);
    cout << "ID Number: " << idNumber << checksum << endl;
    return 0;
}
```


# Luhn Algorithm in Java

![Java](https://www.oracle.com/a/ocom/img/cb71-java-logo.png)

```java
public class LuhnAlgorithm {
    public static int calculateLuhn(String idNumber) {
        int checksum = 0;
        int n = idNumber.length();

        for (int i = n - 1; i >= 0; i--) {
            int digit = idNumber.charAt(i) - '0';

            if ((n - i) % 2 == 0) {
                digit *= 2;
                if (digit > 9) digit -= 9;
            }

            checksum += digit;
        }

        return (10 - (checksum % 10)) % 10;
    }

    public static void main(String[] args) {
        String idNumber = "800101500908";
        int checksum = calculateLuhn(idNumber);
        System.out.println("ID Number: " + idNumber + checksum);
    }
}
```


# Luhn Algorithm in C#

![C#](https://upload.wikimedia.org/wikipedia/commons/6/6a/C_Sharp_logo.png)

```csharp
using System;

class LuhnAlgorithm {
    public static int CalculateLuhn(string idNumber) {
        int checksum = 0;
        int n = idNumber.Length;

        for (int i = n - 1; i >= 0; i--) {
            int digit = idNumber[i] - '0';

            if ((n - i) % 2 == 0) {
                digit *= 2;
                if (digit > 9) digit -= 9;
            }

            checksum += digit;
        }

        return (10 - (checksum % 10)) % 10;
    }

    static void Main() {
        string idNumber = "800101500908";
        int checksum = CalculateLuhn(idNumber);
        Console.WriteLine($"ID Number: {idNumber}{checksum}");
    }
}
```


# Luhn Algorithm in Ruby

![Ruby](https://www.ruby-lang.org/images/ruby-logo.png)

```ruby
def calculate_luhn(id_number)
    digits = id_number.chars.map(&:to_i)
    checksum = 0

    digits.reverse.each_with_index do |digit, i|
        if i.odd?
            doubled = digit * 2
            checksum += doubled > 9 ? doubled - 9 : doubled
        else
            checksum += digit
        end
    end

    (10 - (checksum % 10)) % 10
end

id_number = '800101500908'
checksum = calculate_luhn(id_number)
puts "ID Number: #{id_number}#{checksum}"
```

# Luhn Algorithm in PHP

![PHP](https://www.php.net/images/logos/php-logo.svg)

```php
<?php
function calculateLuhn($idNumber) {
    $digits = str_split($idNumber);
    $checksum = 0;
    $reverseDigits = array_reverse($digits);

    foreach ($reverseDigits as $i => $digit) {
        $digit = (int)$digit;
        if ($i % 2 === 1) {
            $doubled = $digit * 2;
            $checksum += ($doubled > 9) ? $doubled - 9 : $doubled;
        } else {
            $checksum += $digit;
        }
    }

    return (10 - ($checksum % 10)) % 10;
}

$idNumber = '800101500908';
$checksum = calculateLuhn($idNumber);
echo "ID Number: {$idNumber}{$checksum}";
?>
```


# Luhn Algorithm in Go

![Go](https://golang.org/doc/gopher/appengine_gopher.png)

```go
package main

import (
    "fmt"
    "strconv"
)

func calculateLuhn(idNumber string) int {
    checksum := 0
    n := len(idNumber)

    for i := n - 1; i >= 0; i-- {
        digit, _ := strconv.Atoi(string(idNumber[i]))

        if (n-i)%2 == 0 {
            digit *= 2
            if digit > 9 {
                digit -= 9
            }
        }

        checksum += digit
    }

    return (10 - (checksum % 10)) % 10
}

func main() {
    idNumber := "800101500908"
    checksum := calculateLuhn(idNumber)
    fmt.Printf("ID Number: %s%d\n", idNumber, checksum)
}
```

# Luhn Algorithm in Swift

![Swift](https://swift.org/assets/images/swift.svg)

```swift
func calculateLuhn(idNumber: String) -> Int {
    let digits = idNumber.compactMap { Int(String($0)) }
    var checksum = 0
    
    for (i, digit) in digits.reversed().enumerated() {
        if i % 2 == 1 {
            let doubled = digit * 2
            checksum += (doubled > 9) ? doubled - 9 : doubled
        } else {
            checksum += digit
        }
    }

    return (10 - (checksum % 10)) % 10
}

let idNumber = "800101500908"
let checksum = calculateLuhn(idNumber: idNumber)
print("ID Number: \(idNumber)\(checksum)")
```


# Luhn Algorithm in Kotlin

![Kotlin](https://kotlinlang.org/assets/images/logo.svg)

```kotlin
fun calculateLuhn(idNumber: String): Int {
    val digits = idNumber.map { it.toString().toInt() }
    var checksum = 0

    for (i in digits.indices.reversed()) {
        var digit = digits[i]
        if ((digits.size - i) % 2 == 0) {
            digit *= 2
            if (digit > 9) digit -= 9
        }
        checksum += digit
    }

    return (10 - (checksum % 10)) % 10
}

fun main() {
    val idNumber = "800101500908"
    val checksum = calculateLuhn(idNumber)
    println("ID Number: $idNumber$checksum")
}
```