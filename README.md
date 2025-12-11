#include <stdio.h>

// Euclide étendu : calcule d = PGCD(a,b) + trouve x,y tels que a*x + b*y = d
int euclide_etendu(int a, int b, int *x, int *y) {
    if (b == 0) {
        *x = 1;
        *y = 0;
        return a;
    }

    int x1, y1;
    int d = euclide_etendu(b, a % b, &x1, &y1);

    *x = y1;
    *y = x1 - (a / b) * y1;

    return d;
}

int main() {
    int a, b, c, x, y;

    printf("Entrez a, b, c : ");
    scanf("%d %d %d", &a, &b, &c);

    int d = euclide_etendu(a, b, &x, &y);

    if (c % d != 0) {
        printf("Aucune solution.\n");
        return 0;
    }

    // Solution particulière
    x *= c / d;
    y *= c / d;

    printf("Solution particuliere : x = %d, y = %d\n", x, y);

    // Solutions générales
    printf("Solutions generales :\n");
    printf("x = %d + %d*k\n", x, b / d);
    printf("y = %d - %d*k\n", y, a / d);
    printf("(k entier)\n");

    return 0;
}
