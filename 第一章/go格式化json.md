# 解析json
> 使用gjson库进行解析
```go
package main 

import (
	"log"
	"github.com/tidwall/gjson"
)

var jsondata =
`{
    "nav": [
        {
            "前言": [
                {
                    "介绍": "README.md"
                },
                {
                    "准备工作": "installation.md"
                },
                {
                    "快速开始": "quick_start.md"
                }
            ]
        },
        {
            "主题": [
                {
                    "主题的使用": "plugins/plugins.md"
                },
                {
                    "Admin插件使用": "plugins/admin.md"
                }
            ]
        },
        {
            "发展规划": "plan.md"
        }
    ]
}`
func main() {
	log.Println("----原始json字符串------", jsondata)
	log.Println("----解析其中的markdown路径如下：")
	res := gjson.Parse(string(jsondata))
	for _, v := range res.Map() {
		for _, v1 := range v.Array() {
			// log.Println("data", k1, v1)
			for k2, v2 := range v1.Map() {
				if v2.Type == gjson.String {
					log.Println("--md", k2, v2)
				}

				if v2.Type == gjson.JSON {
					for k11, v11 := range v2.Array() {
						if v11.Type == gjson.String {
							log.Println("data2", k11, v11)
						}
						for k21, v21 := range v11.Map() {
							log.Println(k21, ":", v21)
						}
					}
				}
			}
		}
	}

	// ioutil.WriteFile("aa.json", jsondata, 0666)
}
```