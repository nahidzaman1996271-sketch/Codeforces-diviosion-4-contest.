# Codeforces-diviosion-4-contest.[Codeforces contest problem.cpp](https://github.com/user-attachments/files/24696571/Codeforces.contest.problem.cpp)

#include <iostream>
using namespace std;

int main() {
    int t;
    cin >> t;

    while (t--) {
        int n;
        cin >> n;
        int a[50];
        for (int i = 0; i < n; i++) {
            cin >> a[i];
        }

        long long original_value = 0;
        int max = 0;
        for (int i = 0; i < n; i++) {
            if (a[i] > max) {
                max = a[i];
            }
            original_value += max;
        }
        long long max_val = original_value;

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = a[i];
                a[i] = a[j];
                a[j] = temp;
                long long new_value = 0;
                int curr_max = 0;
                for (int k = 0; k < n; k++) {
                    if (a[k] > curr_max) {
                        curr_max = a[k];
                    }
                    new_value += curr_max;
                }

                if (new_value > max_val) {
                    max_val = new_value;
                }

                temp = a[i];
                a[i] = a[j];
                a[j] = temp;
            }
        }

        cout << max_val << endl;
    }

    return 0;
}
