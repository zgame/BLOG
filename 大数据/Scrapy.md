# 创建项目

	scrapy startproject tutorial

# 定义item

	编辑 tutorial 目录中的 items.py 文件
	import scrapy
	class DmozItem(scrapy.Item):
	    title = scrapy.Field()
	    link = scrapy.Field()
	    desc = scrapy.Field()

# spider

	Spider代码，保存在 tutorial/spiders 目录下的 dmoz_spider.py 文件中
	import scrapy
	class DmozSpider(scrapy.Spider):
	    name = "dmoz"
	    allowed_domains = ["dmoz.org"]
	    start_urls = [
	        "http://www.dmoz.org/Computers/Programming/Languages/Python/Books/",
	        "http://www.dmoz.org/Computers/Programming/Languages/Python/Resources/"
	    ]
	
	    def parse(self, response):
	        filename = response.url.split("/")[-2]
	        with open(filename, 'wb') as f:
	            f.write(response.body)


# 爬取

	命令 scrapy crawl dmoz


# XPath

	/html/head/title: 选择HTML文档中 <head> 标签内的 <title> 元素
	/html/head/title/text(): 选择上面提到的 <title> 元素的文字
	//td: 选择所有的 <td> 元素
	//div[@class="mine"]: 选择所有具有 class="mine" 属性的 div 元素

	 def parse(self, response):
        for sel in response.xpath('//ul/li'):
            item = DmozItem()
            item['title'] = sel.xpath('a/text()').extract()
            item['link'] = sel.xpath('a/@href').extract()
            item['desc'] = sel.xpath('text()').extract()
            yield item

# 输出

	scrapy crawl dmoz -o items.json
	该命令将采用 JSON 格式对爬取的数据进行序列化，生成 items.json 文件。



# https://scrapy-chs.readthedocs.io/zh_CN/0.24/intro/overview.html