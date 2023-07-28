<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <title>开发者学习能力指标</title>
    <!-- 引入 echarts.js -->
    <script src="echarts.min.js"></script>
    <script src="jquery.min.js"></script>
    <script type="text/javascript" src="data.json"></script>
</head>

<body>
    <div id="main" style="width: 1000px;height:800px;"></div>
    <script>
        $(document).ready(function () {
            var myChart = echarts.init(document.getElementById('main'), "dark");
           
            option = {
                title: {
                    text: '开发者项目中使用的编程语言数量与开发者人数的关联性'
                },
                tooltip: { trigger: 'axis' },
                legend: {
                    data: ['人数']
                },
                toolbox: {
                    show: true,
                    feature: {
                        mark: { show: true },
                        dataView: { show: true, readOnly: false },
                        magicType: { show: true, type: ['line', 'bar'] },
                        restore: { show: true },
                        saveAsImage: { show: true }
                    }
                },
                calculable: true,


                xAxis: {
                    name: '编程语言数量',
                    data: []
                },
                yAxis: {},
                series: [{

                    type: 'bar',
                    data: []
                },
                ]
            };

            
            $.getJSON("data.json", function (data) {

                myChart.setOption({
                    xAxis: {
                        data: data.categories
                    },
                    series: [{
                        
                        name: '人数',
                        data: data.data
                    }]
                });
            });
            myChart.setOption(option);
        });
    </script>
</body>

</html>
