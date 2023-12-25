#include <iostream>
#include <fstream>
#include <vector>
#include <math.h>
using namespace std;
int main()
{
    std::ifstream inputFile("/Users/aleksejepifanov/Desktop/пары/пары_3_сем/pytgit/algoritm/program/17.txt");
    std::vector<int> numbers;
    int number;
    int count = 0;

    while (inputFile >> number)
    {
        numbers.push_back(number);
    }
    inputFile.close();
    int max = 0;

    for (int i = 0; i < (int)numbers.size(); i++)
    {
        if (numbers[i] % 100 == 15 && numbers[i] > max)
            max = numbers[i];
    }
    int min_sum = max;

    for (int i = 0; i <= (int)numbers.size() - 2; i++)
    {
        int c = 0, sum = 0;
        int d[] = {numbers[i], numbers[i + 1], numbers[i + 2]};

        for (int j = 0; j < 3; j++)
        {
            sum += d[j];
            if (abs(d[j]) > 999 && abs(d[j]) < 10000)
                c++;
        }
        if (c == 1 && sum < max)
        {
            count++;
            if (sum < min_sum)
                min_sum = sum;
        }
    }
    cout << count << "    " << min_sum << endl;
}