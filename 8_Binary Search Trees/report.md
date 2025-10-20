# Activity 8: Binary Search Trees

## Tasks

1. Binary Search Tree Diagram
   Here is the diagram of the binary search tree after inserting the sequence [1, 5, 9, 2, 4, 10, 6, 3, 8] in order.
       1
       \
        5
       / \
      2   9
       \ / \
        4 6  10
       /   \
      3     8
2. Maximum Search Steps in a Balanced BSTFor a well-balanced binary search tree with N values, the maximum number of steps required to search for a value is related to the height of the tree, which is approximately $\lfloor log_2(N) \rfloor + 1$.Number of values (N): 1,000Calculation: $\lfloor log_2(1000) \rfloor + 1$We know that $2^9 = 512$ and $2^{10} = 1024$.Therefore, $log_2(1000)$ is approximately 9.97.The maximum number of steps is $\lfloor 9.97 \rfloor + 1 = 9 + 1 = 10$.The maximum number of steps it would take is 10.****

3. Algorithm to Find the Greatest Value
The greatest value in a binary search tree is always located at the rightmost node. To find it, you start at the root and traverse as far to the right as possible.

Algorithm: findMax(rootNode)

If the tree is empty (rootNode is null), return an error or null.

Initialize a pointer currentNode to rootNode.

While currentNode.right is not null:

Set currentNode = currentNode.right.

Return the value of currentNode.

4. 
```cpp
#include <iostream>
#include <vector>
// Node structure for the Binary Search Tree
struct Node {
    int data;
    Node* left;
    Node* right;

    // Constructor to initialize a new node
    Node(int value) {
        data = value;
        left = nullptr;
        right = nullptr;
    }
};

// Function to insert a value into the BST
// Returns the root of the modified tree
Node* insert(Node* root, int value) {
    // If the tree is empty, create a new node and return it as the new root
    if (root == nullptr) {
        return new Node(value);
    }

    // Otherwise, recur down the tree
    if (value < root->data) {
        // Insert in the left subtree
        root->left = insert(root->left, value);
    } else if (value > root->data) {
        // Insert in the right subtree
        root->right = insert(root->right, value);
    }

    // Return the (unchanged) node pointer
    return root;
}

// Function to perform an inorder traversal of the BST (prints sorted values)
void inorderTraversal(Node* root) {
    if (root == nullptr) {
        return;
    }
    inorderTraversal(root->left);   // Visit left subtree
    std::cout << root->data << " "; // Visit root
    inorderTraversal(root->right);  // Visit right subtree
}

int main() {
    // Initialize an empty BST
    Node* root = nullptr;

    // The sequence of numbers to be inserted
    std::vector<int> numbers = {1, 5, 9, 2, 4, 10, 6, 3, 8};

    std::cout << "Inserting numbers into the BST..." << std::endl;
    // Loop through the vector and insert each number into the tree
    for (int num : numbers) {
        root = insert(root, num);
    }
    std::cout << "All numbers inserted." << std::endl;

    // Print the inorder traversal to verify the BST structure
    // The output should be a sorted list of the numbers
    std::cout << "\nInorder traversal of the BST: ";
    inorderTraversal(root);
    std::cout << std::endl;

    return 0;
}
```

## Video
