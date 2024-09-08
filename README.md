def find_unique_numbers(arr, N):
    # Step 1: XOR all the numbers
    xor_all = 0
    for num in arr:
        xor_all ^= num
    
    # Step 2: Find a set bit in the xor_all result (this bit is different in the two unique numbers)
    set_bit = xor_all & -xor_all
    
    # Step 3: Divide the numbers into two groups based on the set bit
    num1 = 0
    num2 = 0
    for num in arr:
        if num & set_bit:
            num1 ^= num
        else:
            num2 ^= num
    
    # The two unique numbers
    unique_numbers = sorted([num1, num2])
    
    return unique_numbers

# Example usage:
N = 2
arr = [1, 2, 3, 2, 1, 4]
print(find_unique_numbers(arr, N))  # Output: [3, 4]
