# HBase

	Apache HBase是一种Key/Value系统，它运行在HDFS之上。
	HBase通过存储key/value来工作。它支持四种主要的操作：增加或者更新行，查看一个范围内的cell，获取指定的行，删除指定的行、列或者是列的版本。


# 应用

	Hbase非常适合用来进行大数据的实时查询。Facebook用Hbase进行消息和实时的分析。它也可以用来统计Facebook的连接数。



#  命令

	hbase(main):001:0 > list		// 列出所有表
	
	put ’<table name>’,’row1’,’<colfamily:colname>’,’<value>’	//使用put命令，可以插入行到一个表
	put 'emp','1','personal data:name','raju'					

	put ‘table name’,’row ’,'Column family:column name',’new value’	//更新也是put

	get ’<table name>’,’row1’		// 获取数据
	delete ‘<table name>’, ‘<row>’, ‘<column name >’, ‘<time stamp>’	// 删除

	


# HBase的Web界面

	要访问 HBase 的 Web界面，在浏览器中键入以下URL
	http://localhost:60010


# Java API 控制

	import java.io.IOException;
	
	import org.apache.hadoop.hbase.HBaseConfiguration;
	import org.apache.hadoop.hbase.HColumnDescriptor;
	import org.apache.hadoop.hbase.HTableDescriptor;
	import org.apache.hadoop.hbase.client.HBaseAdmin;
	import org.apache.hadoop.hbase.TableName;
	
	import org.apache.hadoop.conf.Configuration;
	
	public class CreateTable {
	      
	   public static void main(String[] args) throws IOException {
	
	   Configuration con = HBaseConfiguration.create();
	
	   HBaseAdmin admin = new HBaseAdmin(con);
	
	   HTableDescriptor tableDescriptor = new
	   TableDescriptor(TableName.valueOf("emp"));
	
	   tableDescriptor.addFamily(new HColumnDescriptor("personal"));
	   tableDescriptor.addFamily(new HColumnDescriptor("professional"));
	
	   admin.createTable(tableDescriptor);
	   System.out.println(" Table created ");
	   }
	 }