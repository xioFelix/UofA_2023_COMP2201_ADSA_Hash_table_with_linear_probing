# Practical: Hash Table with Linear Probing

## 1. Task Description

You are required to implement:

- A **hash table** with **linear probing** using C++.

---

### **Specifications**

1. **Keys**:  
   - Lower-case English words (e.g., `apple`, `pear`).  
   - Maximum length: 10 characters.  

2. **Hash Function**:  
   - Use the **last character** of the key as the hash value.  
     - Example:  
       - `apple` → `e`
       - `pear` → `r`

3. **Table Properties**:  
   - Contains **exactly 26 slots** (hash values from `a` to `z`).  
   - The total number of keys to handle is at most **26** (the table will never be too small).  

4. **Slot Status**:  
   - `never used`: Slot has never been occupied.
   - `tombstone`: Slot was previously occupied but is now empty.
   - `occupied`: Slot is currently occupied by a key.

---

### **Operations**

#### **1. Search**

- Given a key:
  - Compute the hash value using the **last character**.
  - Check the corresponding slot:
    - If the slot contains the **objective key**, return the key.
    - If the slot is `never used`, terminate as the key is not in the table.
    - If the slot is `occupied` but contains a **different key**, or is a `tombstone`, move to the next slot (wrapping around if necessary).
  - Repeat until the key is found or the table is fully checked.

---

#### **2. Insertion**

- First, search for the key:
  - If the key **already exists**, do nothing.
  - If the key **does not exist**, compute its hash value:
    - If the corresponding slot is not `occupied` (`never used` or `tombstone`), insert the key and mark the slot as `occupied`.
    - If the slot is already `occupied`, move to the next slot (wrapping around if necessary) until an unoccupied slot is found.

---

#### **3. Deletion**

- Search for the key:
  - If the key is not found, do nothing.
  - If the key is found, mark the slot as a `tombstone`.

---

## 2. Submission Guidelines

**Important**: Follow these guidelines exactly. Submissions are marked automatically. Failure to comply will result in a **0**.

1. Submit **exactly one file** named `main.cpp`.
2. Do not include a design document.
3. Implement the specified hash table as described.

---

## 3. Program Behavior

1. **Initialization**:  
   - Start with an empty hash table containing 26 `never used` slots.

2. **Input**:  
   - A single line containing `n` modification moves (1 ≤ `n` ≤ 26), separated by spaces.  

3. **Modification Moves**:  
   - **`AWord`**:  
     - Insert `Word` into the hash table.  
     - Example: `Aapple` inserts `apple`.
   - **`DWord`**:  
     - Delete `Word` from the hash table.  
     - Example: `Dapple` deletes `apple`.

4. **Output**:  
   - At the end of the program, traverse the hash table slots from `a` to `z` and output all keys separated by spaces.

---

### **Examples**

#### **Input 1**:
```text
Aaaa Accc Abbb
```

#### **Output 1**:
```text
aaa bbb ccc
```

---

#### **Input 2**:
```text
Abba Aaaa Acca
```

#### **Output 2**:
```text
bba aaa cca
```

---

#### **Input 3**:
```text
Abba Aaaa Acca Daaa
```

#### **Output 3**:
```text
bba cca
```

---

## 4. Marking Scheme

- **Total Marks**: 10  
  - 1 mark for successful compilation.  
  - 9 marks for passing 9 test cases.

---

## 5. Submission Instructions

- Use the **websubmission system** at:  
  [https://cs.adelaide.edu.au/services/websubmission/](https://cs.adelaide.edu.au/services/websubmission/)
- Select the correct semester, course, and assignment.
- The system automatically fetches the latest version from your SVN repository.  
  You can also choose to submit older versions.

---

### **Compilation and Testing**

- **Compilation Command**:
  ```bash
  g++ -o main.out -std=c++11 -O2 -Wall main.cpp
  ```

- **Ensure Compatibility**:
  - Your code must compile on the university system.  
    (e.g., lab computers or via SSH to `uss.cs.adelaide.edu.au`.)

---

### **Submission Steps**

1. Write your implementation in `main.cpp`.
2. Submit your work via the web interface.
3. View the feedback after submission:
   - The system will check the format of your submission and provide feedback.
   - Your final mark will be calculated offline after the deadline.

---

### **Notes**

- Ensure your code is compatible with **g++** on the university system.
- Debug on a lab computer or use SSH if needed.
- Submissions are unlimited before the deadline.

---
```