
## ����
����ʹ���������ۻ����������飬һ�Ǿ��ò������ţ�������ռ���˱����RAM��Դ��

## �������
- ��̬����ƽ��ֵ�㷨
- �ŵ�:ֻ��ռ�ݺ��ٵ�RAM�ռ�

## ����
```C
typedef struct {
    uint32_t count;   // ���ô���
    float max;        // ���ֵ
    float min;        // ��Сֵ
    float avg;        // ƽ��ֵ
} Measure_Metric;

// ���²�������
static inline void updateMeasure_Metric(Measure_Metric *Measure_Metric, float newValue) {
    Measure_Metric->count += 1;
    Measure_Metric->max = __fmaxf(newValue, Measure_Metric->max);
    Measure_Metric->min = __fminf(newValue, Measure_Metric->min);
    Measure_Metric->avg += __divf32((newValue - Measure_Metric->avg),Measure_Metric->count);
}

```