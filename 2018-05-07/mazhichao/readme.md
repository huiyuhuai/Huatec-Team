![](https://github.com/felixmzc/Huatec-Team/blob/master/2018-05-07/mazhichao/21.PNG "title")

```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>实时票房</title>
		<script src="echarts.js"></script>
		<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
	</head>
	<body>
		<div id="res" style="width: 800px;height: 400px;"></div>
		<script>
		$.ajax({
			type: "get",
			url: "http://api.shenjian.io/",
			data: {
				appid: "dd648129b0e17057b8901c27f4a88021"
			},
			dataType: "jsonp",
			success: function(cs) {
				var x1 = [];
				var y1 = [];
				for(var i = 0; i < cs.data.length; i++) {
					x1.push(cs.data[i].MovieName);
					y1.push(cs.data[i].BoxOffice);
				}
				var myChart = echarts.init(document.getElementById('res'));
				var option = {
				legend: {
					data: ['实时票房']
				},
				grid: {
					y2: 140
				},
				xAxis: {
					name:'电影名称',
					data: x1,
					axisLabel: {
						interval: 0,     //横轴信息全部显示
						rotate: -30      //-30°角倾斜显示
					}
				},
				yAxis: {
					name:'金额/万元'
				},
				series: [{
					name: '实时票房',
					type: 'bar',
					data: y1,
				}]
			};
			myChart.setOption(option);
			}
		});
		</script>
	</body>
</html>
```
