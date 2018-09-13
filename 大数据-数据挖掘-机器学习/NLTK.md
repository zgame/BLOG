# 安装

	除了pip之外， 还需要安装辅助包
	import nltk
    nltk.download()


# 切分

	from nltk.tokenize import sent_tokenize, word_tokenize
	
	print(sent_tokenize(EXAMPLE_TEXT))	//切分成句子
	print(word_tokenize(EXAMPLE_TEXT))  //切分成单词

# 停止词

	没有意义的无用词
	stop_words = set(stopwords.words('english'))


# 词干

	ps = PorterStemmer()
	ps.stem(w)		// 可以把相似的词汇合并成一个

# 词性标注

	custom_sent_tokenizer = PunktSentenceTokenizer(train_text)   // 训练词性标记器


# 分块

	def process_content():
    try:
        for i in tokenized:
            words = nltk.word_tokenize(i)
            tagged = nltk.pos_tag(words)
            chunkGram = r"""Chunk: {**+?}"""
            chunkParser = nltk.RegexpParser(chunkGram)
            chunked = chunkParser.parse(tagged)
            
            print(chunked)
            for subtree in chunked.subtrees(filter=lambda t: t.label() == 'Chunk'):
                print(subtree)

            chunked.draw()

    except Exception as e:
        print(str(e))

	process_content()


# 缝隙 是从块中删掉

	 chunkGram = r"""Chunk: {+}
                                    }+{"""



# 命名实体识别

	 namedEnt = nltk.ne_chunk(tagged, binary=True)   // 可以把多个词识别成固定的搭配


# 



https://www.colabug.com/2312707.html