---
title: "Highchart 예제들"

categories: 
  - javascript
tags:
  - [Programming, Javascript]

highchart: true 

date: 2022-10-31 17:00:00 +0900
last_modified_at: 2022-10-31 17:00:00 +0900
---
# Highchart doc & demo
* Highchart doc  : [Highchart doc](https://www.highcharts.com/docs/index, "Highchart doc")
* Highchart demo : [Highchart demo](https://www.highcharts.com/demo, "Highchart demo")

# Line chart

 <div id="highchart_line_sample">
 </div>
 <script>
  Highcharts.chart('highchart_line_sample', {
    title: {
        text: 'U.S Solar Employment Growth by Job Category, 2010-2020'
    },
    subtitle: {
        text: 'Source: <a href="https://irecusa.org/programs/solar-jobs-census/" target="_blank">IREC</a>'
    },
    yAxis: {
        title: {
            text: 'Number of Employees'
        }
    },
    xAxis: {
        accessibility: {
            rangeDescription: 'Range: 2010 to 2020'
        }
    },
    legend: {
        layout: 'vertical',
        align: 'right',
        verticalAlign: 'middle'
    },
    plotOptions: {
        series: {
            label: {
                connectorAllowed: false
            },
            pointStart: 2010
        }
    },
    series: [{
        name: 'Installation & Developers',
        data: [43934, 48656, 65165, 81827, 112143, 142383,
            171533, 165174, 155157, 161454, 154610]
    }, {
        name: 'Manufacturing',
        data: [24916, 37941, 29742, 29851, 32490, 30282,
            38121, 36885, 33726, 34243, 31050]
    }, {
        name: 'Sales & Distribution',
        data: [11744, 30000, 16005, 19771, 20185, 24377,
            32147, 30912, 29243, 29213, 25663]
    }, {
        name: 'Operations & Maintenance',
        data: [null, null, null, null, null, null, null,
            null, 11164, 11218, 10077]
    }, {
        name: 'Other',
        data: [21908, 5548, 8105, 11248, 8989, 11816, 18274,
            17300, 13053, 11906, 10073]
    }],
    responsive: {
        rules: [{
            condition: {
                maxWidth: 500
            },
            chartOptions: {
                legend: {
                    layout: 'horizontal',
                    align: 'center',
                    verticalAlign: 'bottom'
                }
            }
        }]
    }
});
 </script>

# Multi axis line chart

 <div id="highchart_multi_axis_line_sample">
 </div>
 <script>
  Highcharts.chart('highchart_multi_axis_line_sample', {
    title: {
        text: 'Tank pressure, Ship speed, BOG'
    },
    yAxis: [{
        title: {
            text: 'Pressure, mbarg',
            style: {
                color: '#f29416'
            }
        },
        labels: {
            format: '{value}',
            style: {
                color: '#f29416'
            }
        }
    },{
    	title: {
            text: 'Ship speed, kt',
            style: {
                color: '#239148'
            },
            rotation: 270
        },
    	opposite: true,
      labels: {
            align: 'right',
            format: '{value}',
            style: {
                color: '#239148'
            }
        },
    },{
    	title: {
            text: 'M/E load, %',
            style: {
                color: '#ffe13b'
            },
            rotation: 270
        },
      opposite: true,
      labels: {
            align: 'right',
            format: '{value}',
            style: {
                color: '#ffe13b'
            }
        },
    }],
    xAxis: {
    	type: "category",
      gridLineWidth: 1
    },
    legend: {
        layout: 'horizontal',
        align: 'center',
        verticalAlign: 'bottom'
    },
    plotOptions: {
        series: {
            label: {
                connectorAllowed: false
            },
            marker: {
                enabled: false,
                states: {
                    hover: {
                        enabled: false
                    }
                }
            }
        }
    },
    tooltip: {
        crosshairs: true,
        animation: true,
        shared: true
    },
    series: [{
        name: 'Pressure (predicted)',
        color: '#f29416',
        yAxis: 0,
        dashStyle: 'dash',
        tooltip: {
            valueSuffix: ' mbarg'
        },
        data: [
            ["22-03-07<br>17:54", 43934], 
            ["22-03-12<br>18:35", 48656], 
            ["22-03-15<br>06:55", 65165], 
            ["22-03-17<br>19:16", 81827], 
            ["22-03-20<br>07:36", 112143], 
            ["22-03-22<br>19:57", 142383],
            ["22-03-25<br>08:17", 171533], 
            ["22-03-27<br>20:38", 165174], 
            ["22-03-30<br>08:59", 155157]
        ]
    }, {
        name: 'Pressure (acture)',
        color: '#f29416',
        yAxis: 0,
        tooltip: {
            valueSuffix: ' mbarg'
        },
        data: [
            ["22-03-07<br>17:54", 43934], 
            ["22-03-12<br>18:35", 48656], 
            ["22-03-15<br>06:55", 65165], 
            ["22-03-17<br>19:16", 81827], 
            ["22-03-20<br>07:36", 112143], 
            ["22-03-22<br>19:57", null],
            ["22-03-25<br>08:17", null], 
            ["22-03-27<br>20:38", null], 
            ["22-03-30<br>08:59", null]
        ]
    }, {
        name: 'Ship speed (predicted)',
        color: '#239148',
        yAxis: 1,
        dashStyle: 'dash',
        tooltip: {
            valueSuffix: ' knot'
        },
        data: [
            ["22-03-07<br>17:54", 24916], 
            ["22-03-12<br>18:35", 37941], 
            ["22-03-15<br>06:55", 29742], 
            ["22-03-17<br>19:16", 29851], 
            ["22-03-20<br>07:36", 32490], 
            ["22-03-22<br>19:57", 30282],
            ["22-03-25<br>08:17", 38121], 
            ["22-03-27<br>20:38", 36885], 
            ["22-03-30<br>08:59", 33726]
        ]
    }, {
        name: 'Ship speed (actural)',
        color: '#239148',
        yAxis: 1,
        tooltip: {
            valueSuffix: ' knot'
        },
        data: [
            ["22-03-07<br>17:54", 24916], 
            ["22-03-12<br>18:35", 37941], 
            ["22-03-15<br>06:55", 29742], 
            ["22-03-17<br>19:16", 29851], 
            ["22-03-20<br>07:36", 32490], 
            ["22-03-22<br>19:57", null],
            ["22-03-25<br>08:17", null], 
            ["22-03-27<br>20:38", null], 
            ["22-03-30<br>08:59", null]
        ]
    }, {
        name: 'M/E load % (predicted)',
        color: '#ffe13b',
        yAxis: 2,
        dashStyle: 'dash',
        tooltip: {
            valueSuffix: ' %'
        },
        data: [
            ["22-03-07<br>17:54", 11744], 
            ["22-03-12<br>18:35", 30000], 
            ["22-03-15<br>06:55", 16005], 
            ["22-03-17<br>19:16", 19771], 
            ["22-03-20<br>07:36", 20185], 
            ["22-03-22<br>19:57", 24377],
            ["22-03-25<br>08:17", 32147], 
            ["22-03-27<br>20:38", 30912], 
            ["22-03-30<br>08:59", 29243]
        ]
    }, {
        name: 'M/E load % (actual)',
        color: '#ffe13b',
        yAxis: 2,
        tooltip: {
            valueSuffix: ' %'
        },
        data: [
            ["22-03-07<br>17:54", 11744], 
            ["22-03-12<br>18:35", 30000], 
            ["22-03-15<br>06:55", 16005], 
            ["22-03-17<br>19:16", 19771], 
            ["22-03-20<br>07:36", 20185], 
            ["22-03-22<br>19:57", null],
            ["22-03-25<br>08:17", null], 
            ["22-03-27<br>20:38", null], 
            ["22-03-30<br>08:59", null]
        ]
    }],
    responsive: {
        rules: [{
            condition: {
                maxWidth: 500
            },
            chartOptions: {
                legend: {
                    layout: 'horizontal',
                    align: 'center',
                    verticalAlign: 'bottom'
                }
            }
        }]
    }
});
 </script>

# Stacked area chart

 <div id="highchart_stacked_area_sample">
 </div>
 <script>
Highcharts.chart('highchart_stacked_area_sample', {
    title: {
        text: 'BOG usage'
    },
    chart: {
        type: 'area'
    },
    yAxis: {
        title: {
            text: 'Mass flow, kg/h'
        }
    },
    tooltip: {
        crosshairs: true,
        animation: true,
        shared: true,
        headerFormat: '<span style="font-size:12px"><b>{point.key}</b></span><br>'
    },
    legend: {
    		enabled: false
    },
    plotOptions: {
        series: {
            marker: {
                enabled: false
            },
            type: 'area',
        },
        area: {
            stacking: 'normal',
            lineColor: '#666666',
            lineWidth: 1,
            marker: {
                lineWidth: 1,
                lineColor: '#666666',
                enabled: false,
                states: {
                    hover: {
                        enabled: false
                    }
                }
            }
        }
    },
    series: [{
        name: 'BOG (predicted)',
        type: 'line',
        lineWidth: 5,
        dashStyle: 'dash',
        color: '#f29416',
        data: [2000, 2050, 2110, 2050, 1950, 2100, 1850, 1920, 2300, 2350]
    }, {
        name: 'BOG (actual)',
        type: 'line',
        lineWidth: 5,
        color: '#f29416',
        data: [2000, 2050, 2110, 2050, 1950, null, null, null, null, null]
    }, {
        name: 'LDC_GCU',
        type: 'area',
        color: '#239148',
        data: [0, 0, 0, 10, 50, 1100, 1150, 900, 0, 0]
    }, {
        name: 'LDC_Engine',
        type: 'area',
        color: '#ffe13b',
        data: [2000, 2050, 2100, 2040, 1900, 1000, 700, 1020, 2300, 2350]
    }]
});
 </script>

# Progress bar chart

 <div id="highchart_progress_bar_sample">
 </div>
 <script>
Highcharts.chart('highchart_progress_bar_sample', {
  chart: {
    type: 'bar',
    height: 70
  },  
  title: {
    text: '',
    align: 'center',
    margin: 0
  },
  credits: false,
  legend: false,
  tooltip: false,
  plotOptions: {
    bar: {
      borderWidth: 0,
      borderRadius: 3,
      animation: false,
      enableMouseTracking: false
    },
    series: {
      pointWidth: 16,
      color: {
        pattern: {
          path: {
            d: 'M 0 0 L 8 10 L 16 0 M 0 4 L 8 13 L 16 3',
            strokeWidth: 3
          },
          width: 16,
          height: 17,
          x: 7
        }
      }
    }
  },
  xAxis: {
    visible: false
  },
  yAxis: {
    visible: false,
    min: 0,
    max: 100,
    title: {
      text: null
    },
    gridLineWidth: 0,
    labels: {
      style: {
        color: Highcharts.getOptions().colors[0]
      }
    }
  },
  series: [
   {
    name: "Fill",
    data: [100],
    color: {
      pattern: {
        color: 'gray'
      }
    },
    grouping: false
  },
  {
    name: "Percentage",
    data: [75],
    color: {
      pattern: {
        color: '#f29416'
      }
    },
    dataLabels: {
      enabled: true,
      inside: false,
      align: 'right',
      position: 'bottom',
      x: 28,
      y: 28,
      format: 'Current',
      shape: 'callout',
      crop: false,
      overflow: "allow",
      backgroundColor: 'rgba(0, 0, 0, 0.75)',
      style: {
        color: '#FFFFFF',
        textOutline: false
      }
    }
  }
  ]
})
 </script>