import math

# --- Helper function for numeric inputs ---
def get_float(prompt):
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Invalid input. Please enter a number.")

# --- Math Logic Functions ---
def solve_linear(a, b, c):
    if a == 0:
        return "No solution (a cannot be 0)" if b != c else "Infinitely many solutions"
    return f"x = {(c - b) / a:.6f}"

def solve_quadratic(a, b, c):
    if a == 0:
        return f"Not a quadratic equation. {solve_linear(b, c, 0)}"
    discriminant = b**2 - 4*a*c
    if discriminant > 0:
        x1 = (-b + math.sqrt(discriminant)) / (2*a)
        x2 = (-b - math.sqrt(discriminant)) / (2*a)
        return f"Two real roots: x1 = {x1:.6f}, x2 = {x2:.6f}"
    elif discriminant == 0:
        x = -b / (2*a)
        return f"One real root: x = {x:.6f}"
    else:
        real_part = -b / (2*a)
        imag_part = math.sqrt(-discriminant) / (2*a)
        return f"Complex roots: x1 = {real_part:.6f} + {imag_part:.6f}i, x2 = {real_part:.6f} - {imag_part:.6f}i"

def evaluate_f(a, b, c, x):
    return a * (x**2) + b * x + c

def derivative_exact(a, b, x):
    # f(x) = ax^2 + bx + c -> f'(x) = 2ax + b
    return 2 * a * x + b

def derivative_numeric(a, b, c, x, h=1e-5):
    # Central difference formula
    f_plus = evaluate_f(a, b, c, x + h)
    f_minus = evaluate_f(a, b, c, x - h)
    return (f_plus - f_minus) / (2 * h)

def estimate_limit(a, b, c, x0):
    # For a polynomial, the limit as x approaches x0 is simply f(x0)
    val = evaluate_f(a, b, c, x0)
    return f"As x -> {x0}, f(x) approaches {val:.6f}"

def integral_exact(a, b, c, x1, x2):
    # F(x) = (a/3)x^3 + (b/2)x^2 + cx
    def F(x): return (a / 3) * (x**3) + (b / 2) * (x**2) + c * x
    return F(x2) - F(x1)

def integral_trapezoid(a, b, c, x1, x2, n=1000):
    h = (x2 - x1) / n
    total = 0.5 * (evaluate_f(a, b, c, x1) + evaluate_f(a, b, c, x2))
    for i in range(1, n):
        total += evaluate_f(a, b, c, x1 + i * h)
    return total * h

# --- Main Application Loop ---
def main():
    print("ALGEBRA & CALCULUS 1")
    print("FIND THE VALUE OF (X) = FORMULA: f(x)=(ax2+bx+c)")

    while True:
        print("\n1. Solve a linear equation (ax + b = c)")
        print("2. Solve a quadratic equation (ax^2 + bx + c = 0)")
        print("3. Evaluate f(x) = ax^2 + bx + c")
        print("4. Find the derivative f'(x) at a point")
        print("5. Estimate a limit as x approaches a value")
        print("6. Compute a definite integral of f(x)")
        print("7. Quit")        
        
        choice = input("Choose an option: ").strip()

        if choice == "1":
            a = get_float("a: ")
            b = get_float("b: ")
            c = get_float("c: ")
            print(solve_linear(a, b, c))

        elif choice == "2":
            a = get_float("a: ")
            b = get_float("b: ")
            c = get_float("c: ")
            print(solve_quadratic(a, b, c))
        
        elif choice == "3":
            a = get_float("a: ")
            b = get_float("b: ")
            c = get_float("c: ")
            x = get_float("x: ")
            result = evaluate_f(a, b, c, x)
            print(f"f({x}) = {result:.6f}")

        elif choice == "4":
            a = get_float("a: ")
            b = get_float("b: ")
            c = get_float("c: ")
            x = get_float("x: ")
            exact = derivative_exact(a, b, x)
            numeric = derivative_numeric(a, b, c, x)
            print(f"Exact f'({x}) = {exact:.6f}")
            print(f"Numeric f'({x}) = {numeric:.6f} (via central difference)")

        elif choice == "5":
            a = get_float("a: ")
            b = get_float("b: ")
            c = get_float("c: ")
            x0 = get_float("x0 (the value x approaches): ")
            print(estimate_limit(a, b, c, x0))

        elif choice == "6":
            a = get_float("a: ")
            b = get_float("b: ")
            c = get_float("c: ")
            x1 = get_float("Lower bound x1: ")
            x2 = get_float("Upper bound x2: ")
            exact = integral_exact(a, b, c, x1, x2)
            numeric = integral_trapezoid(a, b, c, x1, x2)
            print(f"Exact integral = {exact:.6f}")
            print(f"Numeric integral = {numeric:.6f} (via trapezoidal rule, n = 1000)")

        elif choice == "7":
            print("GOODBYE!")
            break
            
        else:
            print("Invalid choice: Please choose 1-7.")

if __name__ == "__main__":
    main()
