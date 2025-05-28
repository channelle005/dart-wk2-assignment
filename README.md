# dart-wk2-assignment

void main() {
  // Sample item prices
  List<double> itemPrices = [5.99, 12.50, 8.75, 20.00, 3.00];

  // === Anonymous Function to filter items >= $10 ===
  List<double> filteredPrices = itemPrices.where((price) => price >= 10.0).toList();
  print("Filtered Prices (>= \$10): $filteredPrices");

  // === Apply Discount ===
  List<double> discountedPrices = applyDiscount(filteredPrices, (price) => price * 0.90); // 10% discount
  print("Prices after 10% Discount: $discountedPrices");

  // === Calculate Total with optional tax (e.g., 8%) ===
  double total = calculateTotal(discountedPrices, taxRate: 0.08);
  print("Total after Tax: \$${total.toStringAsFixed(2)}");

  // === Factorial Discount ===
  int itemCount = discountedPrices.length;
  int factorialDiscount = calculateFactorialDiscount(itemCount); // e.g., 3! = 6
  print("Factorial Discount: $factorialDiscount%");

  // === Final Total after Factorial Discount ===
  double finalPrice = total * ((100 - factorialDiscount) / 100);
  print("Final Total after Factorial Discount: \$${finalPrice.toStringAsFixed(2)}");
}

// === Standard Function with Optional Parameter ===
double calculateTotal(List<double> prices, {double taxRate = 0.0}) {
  double subtotal = prices.reduce((a, b) => a + b);
  return subtotal + (subtotal * taxRate);
}

// === Higher-Order Function ===
List<double> applyDiscount(List<double> prices, double Function(double) discountFn) {
  return prices.map(discountFn).toList();
}

// === Recursive Function ===
int calculateFactorialDiscount(int n) {
  if (n <= 1) return 1;
  return n * calculateFactorialDiscount(n - 1);
}
