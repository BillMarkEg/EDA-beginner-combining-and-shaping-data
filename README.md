# EDA-beginner-combining-and-shaping-data

  ## Combining and Shaping Data
  Janani Ravi
  ### Exploring tehniques to combine and shape data 
  #### combine and shape data using excel 
  <br> data- > load data -> data type detection -> based on entire data-set -> load if all is well || or  transaform-> use first row as header -> file menu -> close & load  
  #### to join them 
  <br> copy column header from sheet 1 to sheet 2 
  <br> do vlookup or index/match.
  <br> what is better ? 
  <br> 1 - the greatest benefit of using INDEX MATCH over VLOOKUP is the fact that,
  <br> with INDEX MATCH, you can insert columns in your table array without distorting your lookup results.
  <br> Any time you work with a large dataset,
  <br> there's a good chance you'll need to go back to edit our columns and potentially insert a new column
  <br> so using index match is more dynamic than manual lookup
  <br> 2- second : vlookup works only from right to left and on columns only but index/match is more dynamic.
  #### Labs 
  <br> Lab :  Playstore App Stats.xlsx -> joins  
  <br> Lab : Playstore App Stats.xlsx -> aggregations 
  #### Join using power quert 
  <br> get data -> merge -> select first table -> second table -> click id from each one -> select  join type.
  #### Labs  
  <br> Lab : check monthly sales sheet
  #### convert csv to table 
  <br> read csv -> save as xlsx
  <br> open sheet -> select all data in sheet -> insert menu -> table so wo now we created a table.  
  <br> NOTE : you now can selet 2 columns -> recommended charts -> do some visualizations 
  #### convert wide to long (hony production sheet) 
  <br> open sheet -> alt+ D + P -> click on (multiple consilidation range + pivot table ) -> select range : whole data you have  
  <br> then scroll down to last cell -> show details  -> Here you go long data. 
  #### create pivot table for summary stat
  <br> insert menu -> pivot table -> select range / table -> drag and drop to filter if you wanna filter on -> rows for data you wanna work on it -> facts you wanan make
  <br> Note : you can make agg on facts -> double click on its header and choose (avg/sum/count..) default is sum.
  <br> LAb : company finance sheet.
  ####  unpivot monthly sales  ->  result to "sales rep number sheet."
  <br> load file -> table 1  sheet ->  transform data -> sales rep column -> rclick <unpivot other columns > name it to : unpivot table -> close and load 
  <br> now we created new sheet from original one -> once change in original -> can refresh it by click  in unpivot table from queries and connection menu. 
  #### grouping data  
  <br> select data -> outline -> subtotal -> sum on column
  ### combining and shaping data using SQL. 
  <br> same as prev. course we create azure sql db and blob storage -> upload files -> connect them using azure data factory
  ### combining and shaping data using python
  <br> Jupyter : comining data and manually remove outliers
  <br> Jupyter : detecting outliers using z-score  
  <br> Jupyter : handling missing values  
  <br> bfill/pad to fill null like previos value
  <br> ffill to fill null like next value
  <br> dropna thred .9 means must 90% of data has value to not drop column 
  <br> Jupyter : cleaning data 
  <br> scatter plot to show correlation between 2 columns.
  <br> Jupyter : handling imbalanced data 
  <br> percision = TP / TP + FP
  <br> recall  = TP/ TP + FN
  <br> percision and recall are most imp than accuracy as it shows how many ppl with diabete the model can detect which is most imp.
  <br> i mean its okay to not detect ppl with diabete but its not okay to detect one as diabete and he is not.
  <br> so if data is imbalanced in this case ppl with diabete are very low sample compared to ppl with no diabete.
  <br> so we do oversampling -> just douplicate the data is an option so here accuracy will go down but recall and percision will be better.
  ### integrate data from different source into dwh.
  #### Azure 
  <br> just create dwh the same way as normal azure sql db.
  <br> load data from blob storage as did before using data factory
  #### gcp 
  <br> create project in gcp (same as resource group in azure)
  <br> create bucket  (like container:blob storage in azure) -> upload files to it.
  <br> in setting of bucket there is a key u can use for connection with azure 
  <br> in data factory -> copy data -> source -> connectio google cloud s3 -> access key -> in destination connect to azure dwh. the same way. 
  #### spark application (script to read data from blob and transform it then write to blob again)
  <br> 1-first we wanna make cluster for spark so 
  <br> 2-application registery menu -> and give it a name 
  <br> 3-go to home -> pay as you go subscribtion -> iam -> add role assignment -> contributer -> on app we just created 
  <br> 4-so now we created the app and user as contributer 
  <br> 5-open app u can see -> tenant key and id (service agent id/client id) 
  <br> 6-go to certificates and secrets in app page -> new client secret -> so it create a key to use later.
  <br> 7-upload pyspark script to blob storage 
  <br> 8-open data factory -> linked service -> new liked service -> compute (perviosly we used store not compute link linke like sql db or dwh as source.) 
  <br> 9-compute -> azure HD insights (stands for hadoop cluster) - > ondemand cluster (if u have cluster just connect it) -> choose blob storage (that have file)
  <br> 10- cluster type -> spark -> service princibal id in #5
  <br> 11-service princibal key -> in #6 and tenant in #5 
  <br> 12-give cluser uname and password
  <br> 13-choose resource group for ur cluster (cluster created. as linked service)
  <br> 14-finally.. go there is azure data factory new pipeline -> drag HD insights: spark  to pipeline space
  <br> 15- go to HDI cluster 1 -> select cluster linke we created.  
  <br> 16- in script area -> select script from blob storage 
  <br> 17 - trigger now. to run.
  <br> 18- create another pipeline to move data from blob (output of transformed data) -> to move it to dwh and do some sql queries.
  ### working with streaming data using data warehouse.
  <br> transformation can be stateless or statefull
  <br> stateless-> eg trigger if car speed exeeded a limit so stream is running we trigger or not no data is shared between entities
  <br> statefull-> count num of cars ber each 10 min so we need to count and share data from window to another 
  <br> count window -> window that has specific number of rows then end 
  <br> time window  -> window related to time ex. sliding and tumbling
  <br> session window -> window / session user do in website foreg.
  ### creating a stream analytics data.
  <br> resource group -> storage account -> blob -> upload json file that has input data  
  <br> create resource -> iot -> stream analytics -> give the job a name -> created. 
  <br> go to power bi padge on google to set it up -> power bi cloud collaporation sharing option -> create an account for free.
  <br> got to steaming job again 
  <br> input -> stream input -> blob storage -> choose subscription and format type of input + some configrations -> give it an alias
  <br> output -> power bi -> give dataset name -> table name to read from -> give it an alias -> authorize connection to power bi -> done. 
  <br> query -> write query for steam job to do (can write window function for aggregation) to keep it simple we just select * into output-alias from input-alias 
  <br> in normal input is streaming source like iot hub but here it is just blob storage file for simplicity.
  <br> in power bi go to datasets  -> you will find dataset created from stream output so do some visualizations.
  ##### DONE
