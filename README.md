Download Link: https://assignmentchef.com/product/solved-cs5513-homework-3
<br>
<strong>REQUIRED PROBLEM:</strong> Suppose that the popular student newspaper, The Daily, has decided to obtain an online presence by posting the latest news and feature articles online and allowing readers to post comments on these news and feature articles. For this purpose, The Daily obtained 3 sites (computer nodes): gpel9.cs.ou.edu, gpel10.cs.ou.edu, and gpel11.cs.ou.edu. The editor of this newspaper wants you to create the database backend for a news article and feature article archiving system (using MongoDB) using the three sites, and ensure that the news archiving system is highly available and flexible so that news and features can be inserted at any time without having to bring the system down, and so that even in the face of network failures, readers can still access portions of the news archive. The editor of this newspaper tells you that the following queries will be frequently issued:

<ol>

 <li>Insert an (news or feature) article into the archive.</li>

 <li>Retrieve the latest news from the archive.</li>

 <li>Retrieve the top 10 most read news in the past month.</li>

 <li>Add a comment to an article.</li>

 <li>Add a story to the ‘similar stories’ section of all articles that contain a given word and that have been published within the past 2 years.</li>

</ol>




Every news or feature article has a unique ID (article_id). For each article, its attributes that must be available in the archive at the time of implementation are the following, where attributes of the form attribute_name(attr_1, attr_2,…) denote composite attributes, and attribute_name{…} denote multi-value attributes:




<ul>

 <li><strong>Article</strong>: article_type, article_section, article_id, post_on_date(day, month, year, time), reporter_name, similar_stories{…},    num_times_read,        article_text, comments{(comment_id, article_id, user_id, posted_on_date(day, month, year, time), comment_text, score)}</li>

</ul>




An example entry in the archive:

‘news article’, ’Sports’, 75, (31,12,2017,(23:59:59)) , ‘Bridgette Nolan’,{‘thedaily.com/sports/oklahomafootball-sooners-land-kentucky-graduate-transfer.html’, ‘thedaily.com/sports/oklahoma-football-sooners-look-tofill-void.html’}, 11357, ‘Despite the Cowboys’ last loss last season, they have several options to replace their linebacker…’, {(12, 75, ‘<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="9cf8e8f5f0f0f1fdf2dcfbf1fdf5f0b2fff3f1">[email protected]</a>’, (31,12,2017,(09:29:31)), ‘Keep up the work with your fake news!’, -99 )}




where the format of the date is (31,12,2017,(23:59:59)) meaning December 12<sup>th</sup>, 2017 at 23:59:59.




Using the above scenario, perform the following tasks (a-g) using MongoDB on the GPEL machines:

<ol>

 <li>Produce a dataset (real or synthetic) for the task (or use case) discussed above and write it to a file named <em>txt</em>. You can choose whatever human-readable format for your data. You can obtain this dataset directly from another source, or you can generate it yourself with a program. This dataset should have a size of at least 50 entries. Once you generate this dataset, print out its first 5 entries. Do not print out the whole dataset.</li>

 <li>Using the programming language of your preference (Java, Python, etc.), write a program ‘<em>txt_parser</em>’ that takes your dataset file <em>txt</em> as input, and then generates a MongoDB script named ‘<em>dataInsertion.js</em>’ that contains the “MongoDB commands” to create the collection(s) that implement the database, and then inserts every data entry contained in <em>articleData.txt</em> into the database.</li>

 <li>Run the ‘<em>txt_parser</em>’ program and generate your ‘dataInsertion.js’ script. Then populate your MongoDB database by running ‘dataInsertion.js’ at the MongoDB shell.</li>

 <li>Create the necessary indexes to support your queries. Justify your decision for creating them.</li>

 <li>Implement the five queries (1-5) described above <u>using only the MongoDB query</u> <u>language (not Java, Python or any other programming language)</u>. Run each of your queries one time. Provide screenshots of the output of each run.</li>

 <li>Design a suitable replication scheme to answer your queries. This replication scheme must use at least three GPEL machines (for example: gpel9.cs.ou.edu, gpel10.cs.ou.edu and gpel11.cs.ou.edu). <u>You need to describe and justify your replication design <strong>in</strong></u><strong> <u>detail</u></strong>. Then, implement your design in MongoDB. Your implementation must include the code to set up the replication scheme. For this task, you only need to implement replication; you do not need to implement sharding. You also need to provide a screenshot of the output of the command rs.status() when you run it in your replica set. This is to ensure that your replica set has been properly configured.</li>

 <li>In this task, you will do a simple simulation of the failure of the primary node. To do this, perform the following sub-tasks:

  <ol>

   <li>Connect to the machine running the primary of your replica set and stop the MongoDB process running on that machine, using kill instrustion. Do not attempt to shut down or restart the entire GPEL machine (you do not have user privileges to do so).</li>

   <li>Immediately connect to another active MongoDB server in your replica set and run the command rs.status(). Take a screenshot that shows that no primary has yet been elected.</li>

  </ol></li>

</ol>

<ul>

 <li>Wait until a primary has been elected, and then run your queries one time each again with the remaining nodes. Provide screenshots for the output of each run.</li>

</ul>




<strong>BONUS PROBLEM  (optional) (10 points) </strong>your answer to this bonus problem will be graded only if you also completed ALL the tasks of the required problem in this homework assignment):




Select a commercial or open-source <strong><em>graph</em></strong> NoSQL system of your choice. Read its documentation and perform the following two tasks:

<ul>

 <li>Describe the system’s data model <strong>in detail</strong>.</li>

 <li>Describe <strong>in detail</strong> an appropriate use case for that system and justify it based on your description of the system. Explain <strong>in detail </strong>why that use case is not appropriate for a relational database system.</li>

</ul>

Note that the intention of this problem is for you to understand the fundamental and/or innovative database concepts implemented by that NoSQL system. The intention of the problem is not for you to only report the query syntax of the system. <u>You need to provide</u> <u>references for your answers to this problem. The PDF files for the references must be submitted</u> <u>as a part of your submission (submit them as separate PDF files; do not submit them as one</u> <u>ZIP file).</u>




<strong><u>References</u></strong>:

<ol>

 <li>David Hows, Eelco Plugge, Peter Membrey, and Tim Hawkins. <strong><u>The Definitive Guide</u> <u>to MongoDB. A complete guide to dealing with Big Data using MongoDB</u></strong>. Appress, 2<sup>nd</sup> edition, 2015. <em>Available at the OU Digital Library</em>.</li>

 <li><strong>The MongoDB manual</strong> https://docs.mongodb.org/manual/</li>

 <li><strong>MongoDB use       cases   description</strong>     <a href="https://docs.mongodb.org/ecosystem/use-cases/product-catalog/">https://docs.mongodb.org/ecosystem/use</a><a href="https://docs.mongodb.org/ecosystem/use-cases/product-catalog/">cases/product</a><a href="https://docs.mongodb.org/ecosystem/use-cases/product-catalog/">–</a><a href="https://docs.mongodb.org/ecosystem/use-cases/product-catalog/">catalog/</a></li>

</ol>