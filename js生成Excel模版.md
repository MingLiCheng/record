```javascript
 let str = ''
  const jsonData = [{ '仓库代码': '', '货号': '', '尺码': '', '条码': '', '切货数量': '', '折扣': '' }]
  console.log(jsonData)
  for (var k in jsonData[0]) {
    str += k + ','
  }
  str = str.slice(0, str.length - 1) + '\n'
  console.log(str)
  // 增加\t为了不让表格显示科学计数法或者其他格式
  for (let i = 0; i < jsonData.length; i++) {
    for (const item in jsonData[i]) {
      str += `${jsonData[i][item] + '\t'},`
    }
    str += '\n'
  }
  // encodeURIComponent解决中文乱码
  const uri = 'data:application/vnd.ms-excel;charset=utf-8,\ufeff' + encodeURIComponent(str)
  // 通过创建a标签实现
  const link = document.createElement('a')
  link.href = uri
  // 对下载的文件命名
  link.download = '订单模板.xls'
  document.body.appendChild(link)
  link.click()
  document.body.removeChild(link)
```

