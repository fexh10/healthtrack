# Visualizzazione dei Dati



## Numeri di Passi

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed sit amet nulla ac lectus euismod ullamcorper. Vivamus laoreet ex non tortor faucibus, a efficitur ante posuere. Morbi pretium cursus tincidunt.

<div id="steps-chart" style="width: 600px; height: 400px;"></div>
<script src="https://cdn.jsdelivr.net/npm/echarts@5.3.0/dist/echarts.min.js"></script>
<script>
    var stepsChart = echarts.init(document.getElementById('steps-chart'));
    var stepsOption = {
        title: { text: "Andamento Passi Nell'Ultima Settimana" },
        tooltip: { trigger: 'axis' },
        xAxis: {
            type: 'category',
            data: ["lunedì", "martedì", "mercoledì", "giovedì", "venerdì", "sabato", "domenica"]
        },
        yAxis: { type: 'value' },
        series: [
            {
                name: 'Passi',
                type: 'bar',
                data: [5000, 8000, 6000, 10000, 12000, 15000, 14000],
                color: '#5470C6'
            }
        ]
    };
    stepsChart.setOption(stepsOption);
</script>

## Frequenza Cardiaca

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed sit amet nulla ac lectus euismod ullamcorper. Vivamus laoreet ex non tortor faucibus, a efficitur ante posuere. Morbi pretium cursus tincidunt.

### Oggi

<div id="chartFrequenzaCardiaca" style="width: 600px; height: 400px;"></div>

<script src="https://cdn.jsdelivr.net/npm/echarts@5.3.0/dist/echarts.min.js"></script>
<script>
    var myChart = echarts.init(document.getElementById('chartFrequenzaCardiaca'));
    var option = {
        title: { text: 'Battiti Cardiaci' },
        tooltip: { trigger: 'axis' },
        legend: { data: ['A Riposo', 'Durante Attività Fisica'] },
        xAxis: {
            type: 'category',
            data: ['08:00', '10:00', '12:00', '14:00', '16:00', '18:00']
        },
        yAxis: { type: 'value' },
        series: [
            {
                name: 'A Riposo',
                type: 'line',
                data: [60, 65, 72, 77, null, null],
                color: '#5470C6'
            },
            {
                name: 'Durante Attività Fisica',
                type: 'line',
                data: [null, null, null, 120, 130, 140],
                color: '#91CC75'
            }
        ]
    };
    myChart.setOption(option);
</script>

### Settimana Corrente

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed sit amet nulla ac lectus euismod ullamcorper. Vivamus laoreet ex non tortor faucibus, a efficitur ante posuere. Morbi pretium cursus tincidunt.

<div id="weekly-chart" style="width: 600px; height: 400px;"></div>
<script>
    var weeklyChart = echarts.init(document.getElementById('weekly-chart'));
    var weeklyOption = {
        title: { text: 'Media dei battiti settimanali' },
        tooltip: { trigger: 'axis' },
        xAxis: {
            type: 'category',
            data: ['lunedì', 'martedì', 'mercoledì', 'giovedì', 'venerdì', 'sabato', 'domenica']
        },
        yAxis: { type: 'value', name: 'Battiti' },
        series: [
            {
                name: 'Battiti',
                type: 'bar',
                data: [60, 65, 72, 68, 80, 85, 90],
                color: '#5470C6'
            }
        ]
    };
    weeklyChart.setOption(weeklyOption);
</script>

## Sonno

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed sit amet nulla ac lectus euismod ullamcorper. Vivamus laoreet ex non tortor faucibus, a efficitur ante posuere. Morbi pretium cursus tincidunt.

<div id="gantt-chart" style="width: 600px; height: 400px;"></div>
<script src="https://cdn.jsdelivr.net/npm/echarts@5.3.0/dist/echarts.min.js"></script>
<script>
    var chart = echarts.init(document.getElementById('gantt-chart'));
    var option = {
        title: { text: 'Fasi del Sonno durante la Notte' },
        tooltip: {
            formatter: function (params) {
                if (params.seriesName === 'Inizio') return '';
                var offset = option.series[0].data[params.dataIndex];
                var duration = params.data;
                var startHour = Math.floor(offset / 60);
                var startMin = offset % 60;
                var endMinutes = offset + duration;
                var endHour = Math.floor(endMinutes / 60);
                var endMin = endMinutes % 60;
                return params.name + '<br/>' +
                    'Da ' +
                    (startHour < 10 ? '0' + startHour : startHour) + ':' +
                    (startMin < 10 ? '0' + startMin : startMin) +
                    ' a ' +
                    (endHour < 10 ? '0' + endHour : endHour) + ':' +
                    (endMin < 10 ? '0' + endMin : endMin);
            }
        },
        grid: { left: '3%', right: '4%', bottom: '3%', containLabel: true },
        xAxis: {
            type: 'value',
            min: 0,
            max: 480,
            axisLabel: {
                formatter: function (value) {
                    var hours = Math.floor(value / 60);
                    var minutes = value % 60;
                    return (hours < 10 ? '0' + hours : hours) + ':' + (minutes < 10 ? '0' + minutes : minutes);
                }
            }
        },
        yAxis: {
            type: 'category',
            data: ['Leggero', 'Pesante', 'REM']
        },
        series: [
            {
                name: 'Inizio',
                type: 'bar',
                stack: 'total',
                itemStyle: {
                    color: 'transparent'
                },
                emphasis: {
                    itemStyle: { color: 'transparent' }
                },
                data: [0, 120, 300]
            },
            {
                name: 'Fase',
                type: 'bar',
                stack: 'total',
                label: {
                    show: true,
                    position: 'inside',
                    formatter: '{c} min'
                },
                data: [120, 180, 60],
                itemStyle: {
                    color: function (params) {
                        var colors = ['#5470C6', '#91CC75', '#EE6666'];
                        return colors[params.dataIndex];
                    }
                }
            }
        ]
    };
    chart.setOption(option);
</script>

## SpO2

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed sit amet nulla ac lectus euismod ullamcorper. Vivamus laoreet ex non tortor faucibus, a efficitur ante posuere. Morbi pretium cursus tincidunt.

<div id="chartO2" style="width: 600px; height: 400px;"></div>

<script src="https://cdn.jsdelivr.net/npm/echarts@5.3.0/dist/echarts.min.js"></script>
<script>
  var myChart = echarts.init(document.getElementById('chartO2'));
  var option = {
    title: {
      text: 'Livello di O2'
    },
    tooltip: {
      trigger: 'axis'
    },
    xAxis: {
      type: 'category',
      data: ['08:00', '10:00', '12:00', '14:00', '16:00', '18:00']
    },
    yAxis: {
      type: 'value',
      min: 90,
      max: 100,
      axisLabel: {
        formatter: '{value} %'
      }
    },
    series: [
      {
        name: 'Saturazione O2',
        type: 'line',
        data: [95, 96, 97, 95, 98, 97],
        color: '#5470C6',
        smooth: true
      }
    ]
  };
  myChart.setOption(option);
</script>
