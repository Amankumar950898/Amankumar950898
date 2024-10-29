#include <stdio.h>
#include <stdbool.h>

// Function to check if the set contains a specific element
bool contains(int set[], int size, int element) {
    for (int i = 0; i < size; i++) {
        if (set[i] == element) {
            return true;
        }
    }
    return false;
}

// Function to check if the set has an identity element (0 for addition)
bool has_identity(int set[], int size) {
    return contains(set, size, 0);
}

// Function to check if each element has an inverse (i.e., -a for each a in the set)
bool has_inverse(int set[], int size) {
    for (int i = 0; i < size; i++) {
        int inverse = -set[i];
        if (!contains(set, size, inverse)) {
            return false; // If inverse is missing for any element
        }
    }
    return true;
}

int main() {
    int set[100], size;

    // Input size of the set
    printf("Enter the number of elements in the set: ");
    scanf("%d", &size);

    // Input elements of the set
    printf("Enter the elements of the set: ");
    for (int i = 0; i < size; i++) {
        scanf("%d", &set[i]);
    }

    // Check properties
    bool identity = has_identity(set, size);
    bool inverse = has_inverse(set, size);

    // Determine if it forms a group under addition
    if (identity && inverse) {
        printf("The set forms a group under addition.\n");
    } else {
        printf("The set does not form a group under addition.\n");
        if (!identity) {
            printf("The set does not have an identity element.\n");
        }
        if (!inverse) {
            printf("Not all elements have an inverse.\n");
        }
    }

    return 0;
}
