# Solution

```cpp
#include <bits/stdc++.h>

using namespace std;

vector<string> split_string(string);

int num_of_swap;
vector<int> arr;

int swap(int curIndex){
    if(arr[curIndex] == curIndex+1)
        return 0;

    int temp = arr[curIndex];
    arr[curIndex] = arr[temp-1];
    arr[temp-1] = temp;
    num_of_swap++;


    return 1;
}

// Complete the minimumSwaps function below.
int minimumSwaps(vector<int> arr) {
    for(int i = 0; i < arr.size(); i++){
        while(swap(i));
    }

    return num_of_swap;
}

int main()
{
    ofstream fout(getenv("OUTPUT_PATH"));

    int n;
    cin >> n;
    cin.ignore(numeric_limits<streamsize>::max(), '\n');

    string arr_temp_temp;
    getline(cin, arr_temp_temp);

    vector<string> arr_temp = split_string(arr_temp_temp);

    //changed arr to global variable;
    //int vector<int> arr(n);
    arr.resize(n);

    for (int i = 0; i < n; i++) {
        int arr_item = stoi(arr_temp[i]);

        arr[i] = arr_item;
    }

    int res = minimumSwaps(arr);

    fout << res << "\n";

    fout.close();

    return 0;
}

vector<string> split_string(string input_string) {
    string::iterator new_end = 
        unique(input_string.begin(), input_string.end(), [] (const char &x, const char &y) {
            return x == y and x == ' ';
        });

    input_string.erase(new_end, input_string.end());

    while (input_string[input_string.length() - 1] == ' ') {
        input_string.pop_back();
    }

    vector<string> splits;
    char delimiter = ' ';

    size_t i = 0;
    size_t pos = input_string.find(delimiter);

    while (pos != string::npos) {
        splits.push_back(input_string.substr(i, pos - i));

        i = pos + 1;
        pos = input_string.find(delimiter, i);
    }

    splits.push_back(input_string.substr(i, min(pos, input_string.length()) - i + 1));

    return splits;
}

```

![counting-valleys-English-1](https://user-images.githubusercontent.com/45588457/74312739-9015f980-4db5-11ea-9f1e-0e67988aab23.jpg)

