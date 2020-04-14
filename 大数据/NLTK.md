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


# 词形还原

	lemmatizer = WordNetLemmatizer()
	lemmatizer.lemmatize("cats")

# 语料库

	from nltk.corpus import gutenberg
	sample = gutenberg.raw("bible-kjv.txt")

# Wordnet英语词汇数据库

	from nltk.corpus import wordnet
	syns = wordnet.synsets("program")	// 同义词
	.antonyms // 反义词
	w1.wup_similarity(w2) // 相似度

# 文本分类

	random.shuffle(documents)	//打乱文件
	all_words = nltk.FreqDist(all_words)
	print(all_words.most_common(15))
	print(all_words["stupid"])	

# 单词转换为特征

	
# 朴素贝叶斯分类器

	classifier = nltk.NaiveBayesClassifier.train(training_set) //训练
	print("Classifier accuracy percent:",(nltk.classify.accuracy(classifier, testing_set))*100) // 测试准确率
	classifier.show_most_informative_features(15)//正面或负面评论中最有价值的词汇

# 保存分类器

	save_classifier = open("naivebayes.pickle","wb")
	pickle.dump(classifier, save_classifier)
	save_classifier.close()

	classifier_f = open("naivebayes.pickle", "rb")
	classifier = pickle.load(classifier_f)
	classifier_f.close()

# sklearn 

	from sklearn.linear_model import LogisticRegression,SGDClassifier
	from sklearn.svm import SVC, LinearSVC, NuSVC		//可以引入scikit-learn的计算方法


# 组合算法

	
# 情感分析




https://www.colabug.com/2312707.html