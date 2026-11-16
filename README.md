# Batch10_Group10_AgroTinyC

#include <stdio.h>

int main()
{
    float temp, moisture, humidity, light, ph;
    int a, b, c, votes;

    printf("AGROTINY-C: CROP STRESS CHECK\n");

    printf("Enter temperature: ");
    scanf("%f", &temp);

    printf("Enter soil moisture (0-100): ");
    scanf("%f", &moisture);

    printf("Enter humidity (0-100): ");
    scanf("%f", &humidity);

    printf("Enter light level (0-1000): ");
    scanf("%f", &light);

    printf("Enter soil pH (0-14): ");
    scanf("%f", &ph);

    if (temp < -10 || temp > 60 || moisture < 0 || moisture > 100 ||
        humidity < 0 || humidity > 100 || light < 0 || light > 1000 ||
        ph < 0 || ph > 14)
    {
        printf("Invalid input!\n");
        return 0;
    }

    printf("\nSENSOR RESULTS\n");

    if (moisture < 30)
        printf("Soil moisture: LOW\n");
    else
        printf("Soil moisture: NORMAL\n");

    if (temp > 35)
        printf("Temperature: HIGH\n");
    else
        printf("Temperature: NORMAL\n");

    if (humidity < 35)
        printf("Humidity: LOW\n");
    else
        printf("Humidity: NORMAL\n");

    if (moisture < 30 || (moisture < 40 && humidity < 35))
        a = 1;
    else
        a = 0;

    if (temp > 35 && humidity < 40)
        b = 1;
    else
        b = 0;

    if ((light > 900 && humidity < 30) || ph < 5.5 || ph > 7.5)
        c = 1;
    else
        c = 0;

    votes = a + b + c;

    printf("\nDECISION TREE RESULTS\n");
    printf("Tree 1: %d\n", a);
    printf("Tree 2: %d\n", b);
    printf("Tree 3: %d\n", c);

    printf("Total votes: %d out of 3\n", votes);

    if (votes >= 2)
    {
        printf("\nPOSSIBLE CROP STRESS\n");

        if (moisture < 30 && temp > 35)
            printf("Water and heat stress\n");
        else if (moisture < 30)
            printf("Water stress\n");
        else if (temp > 35)
            printf("Heat stress\n");
        else
            printf("Other environmental stress\n");
    }
    else
    {
        printf("\nNO STRESS DETECTED\n");
    }

    printf("\nNote: This is a basic demonstration program.\n");

    return 0;
}
