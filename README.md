# South African ID Number Generator

https://digifend.github.io/Generate-SA-ID-Number/

This project generates valid South African ID numbers based on the following format:

**YYMMDDGSSSCAZ**


### Breakdown of the ID Format:
- **YYMMDD**: Represents the date of birth (DoB) in the format `YYMMDD`.
- **GSSS**: This is the daily sequence number:
  - Female newborns: Assigned numbers from `0001` to `4999`.
  - Male newborns: Assigned numbers from `5000` to `9999`.
  - The sequence resets each day.
- **C**: Citizenship status:
  - `0` if the person is a South African citizen.
  - `1` if the person is a permanent resident.
- **A**: This number is always `8`:
- **Z**: The final digit is a checksum calculated using the **Luhn algorithm**.

  ![ID Numbers As Explained By The Western Cape Government](https://raw.githubusercontent.com/Digifend/Generate-SA-ID-Number/main/WC_ID_Decoded.png)


### Luhn Algorithm Checksum Calculation:

The checksum ensures the validity of the ID number. Here's how it's calculated:

1. Starting from the right (Z position), double every second digit. If doubling results in a number greater than 9, sum the digits (e.g., 16 becomes 1 + 6 = 7).
2. Sum all the digits.
3. If the total modulo 10 is `0`, the ID number is valid. Otherwise, the checksum digit is adjusted accordingly.

### Luhn Algorithm Code Snippet (Python)

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

# Example: If your generated number is 800101500908, the Luhn checksum is appended as the last digit
id_number = '800101500908'
checksum = calculate_luhn(id_number)
print(f"ID Number: {id_number}{checksum}")
```
See ![Luhn Algorithm in Other Languages]()


### Features
- Random ID Generation: Generate random valid ID numbers with customizable parameters like birthdate and gender.
- Export Functionality: Export the generated ID numbers to a text file.
- Validation: Ensures that the ID number conforms to the South African format and is validated using the Luhn algorithm.
- Generate Sequential ID Numbers


### Usage
Visit https://digifend.github.io/Generate-SA-ID-Number/ to use the tool and generate South African ID numbers.


