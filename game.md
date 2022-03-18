linux 下使用命令行移动文件
```
$ mv /mnt/c/Users/Administrator/Desktop/data/site_bandwidth.csv /mnt/c/Users/Administrator/Desktop/SDK/SDK_C++/CodeCraft-2022/src
```

```
for (auto i = 0; i < demand_vec.size(); ++i) {
        for (auto j = 0; j < demand_vec[0].size(); ++j) {
            cout << demand_vec[i][j] << " ";
        }
        cout << endl;
    }
```

注释：     先CTRL+K，然后CTRL+C

取消注释： 先CTRL+K，然后CTRL+U

```
qos_vec.size()    vector 列的大小 100
qos_vec[0].size() vector 行的大小 11
```

vector 按列相加 求每列的和
```
    vector<vector<double>> array; 
    vector<double> tmp;
    for (int i = 1; i < qos_vec[0].size(); i++) //返回列数 从第一列开始 舍弃name
    {
        double sum = 0;
        for (int j = 0; j < qos_vec.size(); j++) //返回行数
        {
            sum += qos_vec[j][i];
        }
        tmp.push_back(sum);
        
    }
    array.push_back(tmp);
```

输出一维vec

```
   for (auto i = 0; i < 10; ++i) {
           cout << demandrow1_vec[i] << " ";
       }
       cout << endl;
   }

```
输出二维vec

```
    for (auto i = 0; i < demand_vec.size(); ++i) {
        for (auto j = 1; j < demand_vec[0].size(); ++j) {
            cout << demand_vec[i][j] << " ";
        }
        cout << endl;
    }
    return 0;

```


17.17
```
#include <fstream>
#include <string>
#include <sstream>
#include <vector>
#include <iostream>

using namespace std;

int main() {

    //建立一个二维vector demand_vec 储存demand.csv
    vector<vector<int>> demand_vec;
    ifstream fp("/mnt/c/Users/Administrator/Desktop/SDK/SDK_C++/CodeCraft-2022/src/demand.csv"); //定义声明一个ifstream对象，指定文件路径
    string line;
    getline(fp, line); //跳过列名，第一行不做处理  getline(输入流，对象)
    while (getline(fp, line)) { //循环读取每行数据
        vector<int> data_line;
        string number;
        istringstream readstr(line); //string数据流化 ?
        //将一行数据按'，'分割
        for (int j = 0; j < 11; j++) { //可根据数据的实际情况取循环获取
            getline(readstr, number, ','); //循环读取数据
            data_line.push_back(atoi(number.c_str())); //字符串传int
        }
        demand_vec.push_back(data_line); //插入到vector中
    }
    // 检验demand.csv
    //for (auto i = 0; i < demand_vec.size(); ++i) {
    //    for (auto j = 1; j < demand_vec[0].size(); ++j) {
    //        cout << demand_vec[i][j] << " ";
    //    }
    //    cout << endl;
    //}
    //return 0;


    vector<int> demandrow1_vec;         // 建立一个一维demand vec
    vector<vector<int>> demandrow2_vec; // 建立一个二维demand vec

    //向demandrow1_vec里添加一行demand
    for (auto i = 0; i < 1; ++i) {
        for (auto j = 1; j < demand_vec[0].size(); ++j) {
            demandrow1_vec.push_back(demand_vec[i][j]);
        }

    }

    //向demandrow2_vec里添加一行demand
    demandrow2_vec.push_back(demandrow1_vec);

    demandrow2_vec.push_back(demandrow1_vec);


    for (auto i = 0; i < demandrow2_vec.size(); ++i) {
        for (auto j = 1; j < demandrow2_vec[0].size(); ++j) {
            cout << demandrow2_vec[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}





    ////建立一个二维vector site_bandwidth_vec 储存site_bandwidth.csv
    //vector<vector<int>> site_bandwidth_vec; //
    //ifstream fp("/mnt/c/Users/Administrator/Desktop/SDK/SDK_C++/CodeCraft-2022/src/site_bandwidth.csv"); //定义声明一个ifstream对象，指定文件路径
    //string line;
    //getline(fp, line); //跳过列名，第一行不做处理  getline(输入流，对象)
    //while (getline(fp, line)) { //循环读取每行数据
    //    vector<int> data_line;
    //    string number;
    //    istringstream readstr(line); //string数据流化 ?
    //    //将一行数据按'，'分割
    //    for (int j = 0; j < 2; j++) { //可根据数据的实际情况取循环获取
    //        getline(readstr, number, ','); //循环读取数据
    //        data_line.push_back(atoi(number.c_str())); //字符串传int
    //    }
    //    site_bandwidth_vec.push_back(data_line); //插入到vector中
    //}
    //for (auto i = 0; i < site_bandwidth_vec.size(); ++i) {
    //    for (auto j = 0; j < site_bandwidth_vec[0].size(); ++j) {
    //        cout << site_bandwidth_vec[i][j] << " ";
    //    }
    //    cout << endl;
    //}
    //return 0;
 

    //建立一个二维vector qos_vec 储存qos.csv
    vector<vector<int>> qos_vec; 
    ifstream fp("/mnt/c/Users/Administrator/Desktop/SDK/SDK_C++/CodeCraft-2022/src/qos.csv"); //定义声明一个ifstream对象，指定文件路径
    string line;
    getline(fp, line); //跳过列名，第一行不做处理  getline(输入流，对象)

    while (getline(fp, line)) { //循环读取每行数据
        vector<int> data_line;
        string number;
        istringstream readstr(line); //string数据流化 ?
        //将一行数据按'，'分割
        for (int j = 0; j < 11; j++) { //可根据数据的实际情况取循环获取
            getline(readstr, number, ','); //循环读取数据
            data_line.push_back(atoi(number.c_str())); // atoi把字符串转换成整型数的一个函数
        }
        qos_vec.push_back(data_line); //插入到vector中
    }


    //qos大于等于400为0，小于400为1
    for (auto i = 0; i < qos_vec.size(); ++i) {   
        for (auto j = 1; j < qos_vec[0].size(); ++j) {
            if (qos_vec[i][j] >= 400) {
                qos_vec[i][j] = 0;
            }
            else {
                qos_vec[i][j] = 1;
            }
        } 
    }


    //vector 按列相加 求每列的和
    vector<vector<double>> array; 
    vector<double> tmp;
    for (int i = 1; i < qos_vec[0].size(); i++) //返回列数 从第一列开始 舍弃name
    {
        double sum = 0;
        for (int j = 0; j < qos_vec.size(); j++) //返回行数
        {
            sum += qos_vec[j][i];
        }
        tmp.push_back(sum);
    }
    array.push_back(tmp);

    
       for (auto i = 0; i < array.size(); ++i) {
        for (auto j = 0; j < array[0].size(); ++j) {
            cout << array[i][j] << " ";
        }
        cout << endl;
    }
```
