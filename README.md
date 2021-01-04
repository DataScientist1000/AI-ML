My GitHub Pages Repository


    //Type Safe Data Set
    val surveyDS:Dataset[SurveyRecord] = rawDF.select("Age", "Gender", "Country", "state").as[SurveyRecord]

    //Type safe Filter
    val filteredDS = surveyDS.filter(r => r.Age < 40)
    //Runtime Filter
    val filteredDF = surveyDS.filter("Age  < 40")

    //Type safe GroupBy
    val countDS = filteredDS.groupByKey(r => r.Country).count()
    //Runtime GroupBy
    val countDF = filteredDF.groupBy("Country").count()

    logger.info("DataFrame: " + countDF.collect().mkString(","))
    logger.info("DataSet: " + countDS.collect().mkString(","))

    //Uncomment if you want to investigate SparkUI
    //scala.io.StdIn.readLine()
    spark.stop()
    
    
