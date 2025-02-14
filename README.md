# Leetcode---1352-
Product of the Last K Numbers
//code in java
import java.util.ArrayList;
import java.util.List;

class ProductOfNumbers {
    private List<Integer> productList;

    public ProductOfNumbers() {
        productList = new ArrayList<>();
        productList.add(1); // Initializing with 1 for multiplication purposes
    }

    public void add(int num) {
        if (num == 0) {
            productList = new ArrayList<>();
            productList.add(1); // Resetting the list when 0 is encountered
        } else {
            productList.add(productList.get(productList.size() - 1) * num);
        }
    }

    public int getProduct(int k) {
        int n = productList.size();
        if (k >= n) {
            return 0; // If there are fewer than k elements in the product list, return 0
        }
        return productList.get(n - 1) / productList.get(n - 1 - k);
    }

    public static void main(String[] args) {
        ProductOfNumbers productOfNumbers = new ProductOfNumbers();
        productOfNumbers.add(3); // [3]
        productOfNumbers.add(0); // [3, 0]
        productOfNumbers.add(2); // [3, 0, 2]
        productOfNumbers.add(5); // [3, 0, 2, 5]
        productOfNumbers.add(4); // [3, 0, 2, 5, 4]
        System.out.println(productOfNumbers.getProduct(2)); // Output: 20 (5 * 4)
        System.out.println(productOfNumbers.getProduct(3)); // Output: 40 (2 * 5 * 4)
        System.out.println(productOfNumbers.getProduct(4)); // Output: 0 (because there is a 0 in the last 4 numbers)
        productOfNumbers.add(8); // [3, 0, 2, 5, 4, 8]
        System.out.println(productOfNumbers.getProduct(2)); // Output: 32 (4 * 8)
    }
}
