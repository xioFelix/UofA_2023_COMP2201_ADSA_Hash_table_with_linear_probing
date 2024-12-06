#include <iostream>
#include <string>
#include <vector>

enum SlotStatus { NEVER_USED, TOMBSTONE, OCCUPIED };

struct Slot {
  std::string key;
  SlotStatus status;

  Slot() : key(""), status(NEVER_USED) {}
};

class HashTable {
 private:
  std::vector<Slot> table;

  int hash(const std::string& key) { return key.back() - 'a'; }

 public:
  HashTable(int size) : table(size) {}

  bool search(const std::string& key) {
    int idx = hash(key);
    while (table[idx].status != NEVER_USED) {
      if (table[idx].key == key && table[idx].status == OCCUPIED) {
        return true;
      }
      idx = (idx + 1) % table.size();
    }
    return false;
  }

  void insert(const std::string& key) {
    if (search(key)) return;

    int idx = hash(key);
    while (table[idx].status == OCCUPIED) {
      idx = (idx + 1) % table.size();
    }
    table[idx].key = key;
    table[idx].status = OCCUPIED;
  }

  void remove(const std::string& key) {
    int idx = hash(key);
    while (table[idx].status != NEVER_USED) {
      if (table[idx].key == key && table[idx].status == OCCUPIED) {
        table[idx].status = TOMBSTONE;
        return;
      }
      idx = (idx + 1) % table.size();
    }
  }

  void display() {
    for (const Slot& slot : table) {
      if (slot.status == OCCUPIED) {
        std::cout << slot.key << " ";
      }
    }
    std::cout << std::endl;
  }
};

int main() {
  HashTable ht(26);

  std::string input;
  getline(std::cin, input);

  size_t pos = 0;
  while ((pos = input.find(' ')) != std::string::npos) {
    std::string token = input.substr(0, pos);
    if (token[0] == 'A') {
      ht.insert(token.substr(1));
    } else if (token[0] == 'D') {
      ht.remove(token.substr(1));
    }
    input.erase(0, pos + 1);
  }
  if (input[0] == 'A') {
    ht.insert(input.substr(1));
  } else if (input[0] == 'D') {
    ht.remove(input.substr(1));
  }

  ht.display();

  return 0;
}
