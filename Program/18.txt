#include <iostream>
#include <vector>
#include <iomanip>
#include <algorithm>
using namespace std;
template <typename T, size_t N, size_t M>
void printMatrix(T (&matrix)[N][M])
{
    for (int i = 0; i < 15; i++)
    {
        for (int j = 0; j < 15; j++)
        {
            std::cout << std::setw(4) << matrix[i][j] << " ";
        }
        std::cout << std::endl;
    }
}
int main()
{
    int matrix[15][15] = {
        {12, 88, 57, 63, 77, 70, 6, 98, 65, 58, 19, 73, 13, 86, 1},
        {12, 66, 3, 14, 36, 65, 51, 4, 45, 78, 12, 31, 91, 12, 86},
        {61, 41, 46, 70, 39, 7, 76, 23, 3, 4, 62, 75, 63, 65, 54},
        {86, 73, 65, 44, 42, 14, 50, 92, 94, 37, 6, 78, 46, 97, 17},
        {95, 40, 51, 62, 12, 14, 58, 49, 83, 97, 70, 14, 6, 47, 55},
        {75, 43, 22, 77, 71, 53, 19, 58, 37, 69, 48, 98, 98, 89, 35},
        {22, 84, 34, 52, 37, 39, 72, 84, 19, 49, 10, 78, 75, 7, 42},
        {59, 93, 9, 90, 13, 31, 93, 54, 73, 52, 4, 94, 37, 81, 22},
        {68, 76, 84, 83, 87, 36, 26, 19, 19, 73, 24, 47, 42, 52, 5},
        {79, 12, 76, 34, 77, 2, 70, 20, 78, 49, 7, 74, 69, 90, 45},
        {90, 76, 32, 31, 46, 59, 35, 9, 10, 32, 93, 6, 19, 40, 60},
        {67, 21, 74, 59, 98, 15, 49, 70, 31, 48, 63, 52, 70, 33, 69},
        {46, 39, 51, 77, 78, 36, 46, 50, 12, 56, 75, 77, 36, 5, 11},
        {26, 62, 85, 7, 15, 74, 39, 94, 53, 89, 53, 55, 3, 49, 4},
        {21, 94, 40, 22, 35, 50, 85, 61, 29, 89, 18, 62, 52, 94, 16}};
    int newmatrix[15][15];
    newmatrix[14][0] = 21;
    for (int i = 13; i >= 0; i--)
    {
        newmatrix[i][0] = newmatrix[i + 1][0] + ((matrix[i][0] > matrix[i + 1][0]) ? matrix[i][0] : 0);
    }
    for (int j = 1; j <= 14; j++)
    {
        newmatrix[14][j] = newmatrix[14][j - 1] + ((matrix[14][j] > matrix[14][j - 1]) ? matrix[14][j] : 0);
    }
    for (int i = 13; i >= 0; i--)
    {
        for (int j = 1; j <= 14; j++)
        {
            int a = newmatrix[i + 1][j] + ((matrix[i][j] > matrix[i + 1][j]) ? matrix[i][j] : 0);
            int b = newmatrix[i][j - 1] + ((matrix[i][j] > matrix[i][j - 1]) ? matrix[i][j] : 0);
            newmatrix[i][j] = max(a, b);
        }
    }
    printMatrix(newmatrix);
}