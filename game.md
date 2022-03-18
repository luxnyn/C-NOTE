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
