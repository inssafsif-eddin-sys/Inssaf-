#include <stdio.h>

int extgcd(int a, int b, int *x, int *y) {
    if (!b) { *x = 1; *y = 0; return a; }
    int x1, y1, d = extgcd(b, a % b, &x1, &y1);
    *x = y1;
    *y = x1 - (a / b) * y1;
    return d;
}

int main() {
    int a, b, c, x, y;
    scanf("%d %d %d", &a, &b, &c);

    int d = extgcd(a, b, &x, &y);
    if (c % d) return printf("Aucune solution.\n"), 0;

    x *= c / d;  
    y *= c / d;

    printf("x = %d + %d*k\n", x, b / d);
    printf("y = %d - %d*k\n", y, a / d);
}
