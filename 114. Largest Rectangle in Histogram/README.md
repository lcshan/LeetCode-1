
     _           _
    | |  _   _  | |
    | | | |_| | | |
    | | |*|*|*| | |
    | |_|*|*|*| | |
    | | |*|*|*|_| |
    |_|_|_|_|_|_|_|
     6 2 5 4 5 1 6
         ^ ^ ^
     0 1 2 3 4 5 6

��ͼ��ʾ����ֱ�ۣ�`3 * 4 == 12`.����˼������������εõ������� 12 �ģ�

���Ƿ��֣�Ҫ���� Largest Rectangle ���ؼ�����**�̰�**����������ѡ�� 4�����ƵĻ�����Щ�أ��и�����

|min_height|rectangle|area|
|:--------:|:-------:|:--:|
|     2    |  0 -> 4 | 2*5|
|     4    |  2 -> 4 | 4*3|
|     1    |  0 -> 6 | 1*6|

���պ����ԣ�area ���ļ�Ϊ�м����У����Ϊ 12.

�ٽ�һ��˼����

1. �̰������ժ�����ģ��������Ȼ����˥��������ʱ����ֵġ��� 6->2, 5->4, 5->1.
2. �̰��������εó���ϸ�¹۲�󣬷����Ƕ̰�֮��������ָ���ġ��� 2->4:(2), 2->1, 4->1:(4), 2 �� 4 ���Ƿָ�����

���ˣ����ڷ����˹��ɣ������׼ȷ�ҵ���������ݽṹ�أ�

���ǵĵ�һ��Ŀ����Ȼ��Ҫ�ҳ��̰壬�̰�������ǣ�

    height[i] < height[i-1]

ò�Ƶ���һ�鼴�ɣ����̰�����ڷָ�����εó��أ����ǲ���Ҫ�ҳ��̰壬����Ҫ���¶̰��Լ��̰�� index, �Ա�Ѱ�ҷָ�����

����������Ҫһ��ɸ�ӣ�ɸ�������϶̰������ģ����¶̰塣

**ջ**�ǳ�����ɸ�ӵ����ԣ��������߶�ʮһ��push ��ȥ���������� pop ������

```cpp
int max_area = 0, i = 0, size = height.size();
for (stack<int> stk; i<size || !stk.empty(); ) { // ����� for ѭ���ڶ���������Ŀ�ﾭ�����֣�DFS��
    if (stk.empty() || (i != size && height[stk.top()] <= height[i])) stk.push(i++); // ���Ƕ̰壬�� push
    else {
        int tp = stk.top(); stk.pop();
        max_area = std::max(max_area, height[tp] * (stk.empty() ? i : i-stk.top()-1));
    }
}
```

�����߼��ܼ򵥣�5 �н�����