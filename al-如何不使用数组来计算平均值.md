
## 问题
不想使用数组来累积进来的数组，一是觉得不够优雅，而是这占据了宝贵的RAM资源。

## 解决方法
- 动态更新平均值算法
- 优点:只是占据很少的RAM空间

## 代码
```C
typedef struct {
    uint32_t count;   // 调用次数
    float max;        // 最大值
    float min;        // 最小值
    float avg;        // 平均值
} Measure_Metric;

// 更新测量数据
static inline void updateMeasure_Metric(Measure_Metric *Measure_Metric, float newValue) {
    Measure_Metric->count += 1;
    Measure_Metric->max = __fmaxf(newValue, Measure_Metric->max);
    Measure_Metric->min = __fminf(newValue, Measure_Metric->min);
    Measure_Metric->avg += __divf32((newValue - Measure_Metric->avg),Measure_Metric->count);
}

```