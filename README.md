# Customer-segmentation-analysis-Using-R
library(tidyverse)
# Attaching packages ----- tidyverse 1.3.1 --
 v ggplot2 3.3.5     v purrr   0.3.4
 
 v tibble  3.1.6     v dplyr   1.0.8
 
 v tidyr   1.2.0     v stringr 1.4.0
 
 v readr   2.1.2     v forcats 0.5.1
 
 -- Conflicts -------- tidyverse_conflicts() --
 
 x dplyr::filter() masks stats::filter()
 
 x dplyr::lag()    masks stats::lag()
 
Implementation of Customer Segmentation

# Reading in the dataset “customer_data”.

customer_data <- read.csv(file.choose())

str(customer_data)

'data.frame':    200 obs. of  5 variables:
 
 $ CustomerID            : int  1 2 3 4 5 6 7 8 9 10 ...
 
 $ Gender                : chr  "Male" "Male" "Female" "Female" ...

$ Age                   : int  19 21 20 23 31 22 35 23 64 30 ...

$ Annual.Income..k..    : int  15 15 16 16 17 17 18 18 19 19 ...

$ Spending.Score..1.100.: int  39 81 6 77 40 76 6 94 3 72 ...

# Viewing the column names included by the dataset.

names(customer_data)

[1] "CustomerID"  "Gender" "Age"                   

[4] "Annual.Income..k.."  "Spending.Score..1.100."

# View the first 6 rows of the dataset using head() function.

head(customer_data)

CustomerID

<int>

 Gender

 <chr>

  Age

  <int>

   Annual.Income..k..

   Spending.Score..1.100.

   <int>

  1	Male	19	15	39

  2	Male	21	15	81

  3	Female	20	16	6

  4	Female	23	16	77

  5	Female	31	17	40
 
  6	Female	22	17	76

  6 rows

 # Summarizing the columns “Age” and “Annual.Income..k..” and find standard deviations.
 
 Summarizing the "Age" column
 
 summary(customer_data$Age)
   
    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 
    18.00   28.75   36.00   38.85   49.00   70.00

Standard deviation of Age

    sd(customer_data$Age)

    [1] 13.96901

    # Summarizing the column "Annual.Income..k.."

    summary(customer_data$Annual.Income..k..)

    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 
    15.00   41.50   61.50   60.56   78.00  137.00

    Standard deviation pf column "Annual.Income..k.."

    sd(customer_data$Annual.Income..k..)
 
    [1] 26.26472

    Find standard deviation of “Spending.Score..1.100.” column.


    sd(customer_data$Spending.Score..1.100.)

    [1] 25.82352

    Customer Gender Visualization

    Plot a barplot and a piechart to show the gender distribution across our “customer_data” dataset

    a = table(customer_data$Gender)

    barplot(a, main = "Using BarPlot to display Gender Comparision",
      
    ylab = "Count",
       
    xlab = "Gender",
     
    col = rainbow(2),
    
    legend=rownames(a) )  
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/0513c975-0e10-4fab-a51e-b89a5be608a4)

    pct = round(a/sum(a)*100)

    lbs = paste(c("Female","Male")," ",pct,"%",sep=" ")

    library(plotrix)

    pie3D(a, labels=lbs, 
  
    main = "Pie Chart Depicting Ratio of Female and Male")

![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/7ddd5313-5a4a-495c-b8e2-314df75efa3d)

    # Visualization of Age Distribution

    Plotting a histogram to view the distribution to plot the frequency of customer ages.

    hist(customer_data$Age,
   
    col = "Magenta",
   
    main = "Histogram to Show Count of Age Class",
   
    xlab = "Age Class",
 
    ylab = "Frequency",

    labels = TRUE)

![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/cbfa97d2-d79e-440f-9dc2-0e7833b81843)

    # Plot boxplot for descriptive analysis of “Age” column.

    boxplot(customer_data$Age,
  
    col = "orange",
  
    main = "Boxplot for Descriptive Analysis of Age")
 
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/ab5b769f-75cc-4a07-8e52-4ead701f555c)

    # Analysis of the Annual Income of the Customers

    Get the summary and then plotting a histogram to analyze the annual income.

    summary(customer_data$Annual.Income..k..)
 
    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 
    15.00   41.50   61.50   60.56   78.00  137.00

    hist(customer_data$Annual.Income..k..,
 
    col="#660033",
  
    main="Histogram for Annual Income",
  
    xlab="Annual Income Class",
 
    ylab="Frequency",
  
    labels=TRUE)
 
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/a6c1d7b6-d854-4572-880b-9bec0b51e417)

    # Density plot analysis.

    plot(density(customer_data$Annual.Income..k..),
 
    col="blue",
  
    main="Density Plot for Annual Income",
   
    xlab="Annual Income Class",
  
    ylab="Density")

    polygon(density(customer_data$Annual.Income..k..),
        col="yellow")
 
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/b682c352-4d50-49a7-bb84-e63f34fa8bf5)

    # Analyzing Spending Score of the Customers

    Creating summary and boxplot for anlyzing spending score of customers.

    summary(customer_data$Spending.Score..1.100.)
  
    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
 
    1.00   34.75   50.00   50.20   73.00   99.00

    boxplot(customer_data$Spending.Score..1.100.,
 
    horizontal=TRUE,
 
    col="#990000",
  
    main="BoxPlot for Descriptive Analysis of Spending Score")
 
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/2c67247b-4032-49a0-8680-8d22a79336d8)

    Now, plotting a histogram for the spending score data of customers.

    hist(customer_data$Spending.Score..1.100.,

    main="HistoGram for Spending Score",

    xlab="Spending Score Class",
  
    ylab="Frequency",
  
    col="#6600cc",
  
    labels=TRUE)

![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/6451ac56-bc44-4db4-a39c-4bd0a50c7616)

    # Determining Optimal Clusters

    #Elbow Method

    we proceed to plot iss(sum of square) based on the number of k clusters. This plot denotes the appropriate number of clusters required in our model. In the plot, the 
    location of a bend or a knee is the indication of the optimum number of clusters.

    library(purrr)

    set.seed(123)

    # function to calculate total intra-cluster sum of square 

    iss <- function(k) {

           kmeans(customer_data[,3:5],k,iter.max=100,nstart=100,algorithm="Lloyd" )$tot.withinss

           }

           k.values <- 1:10

    iss_values <- map_dbl(k.values, iss)

                  plot(k.values, iss_values,
  
                  type="b", pch = 19, frame = FALSE, 
 
                  xlab="Number of clusters K",
   
                  ylab="Total intra-clusters sum of squares")
  
                  
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/e0cd1570-b8d7-4556-a81b-adadfeb515ae)

                  Gap Statistic Method

                  We can utilize the clusGap function for providing gap statistic as well as standard error for a given output.

                  library(cluster)          #clustering algorithms
library(factoextra)       #clustering algorithms & visualization

                  Warning: package 'factoextra' was built under R version 4.1.3

                  set.seed(125)

                  stat_gap <- clusGap(customer_data[,3:5], FUN = kmeans, nstart = 25,
          
    K.max = 10, B = 50)

    fviz_gap_stat(stat_gap)
 
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/256b514c-f27f-486a-b264-ab5a337e9f04)

    Now, take k = 6 as our optimal cluster –

    k6<-kmeans(customer_data[,3:5], 6, iter.max=100, nstart=50, algorithm="Lloyd")

                                    k6

                                    K-means clustering with 6 clusters of sizes 45, 21, 35, 39, 38, 22
 
                                    Cluster means:

                                    Age Annual.Income..k.. Spending.Score..1.100.
 
                                    1 56.15556           53.37778               49.08889

                                    2 44.14286           25.14286               19.52381
 
                                    3 41.68571           88.22857               17.28571

                                    4 32.69231           86.53846               82.12821
 
                                    5 27.00000           56.65789               49.13158

                                    6 25.27273           25.72727               79.36364
 

                                    Clustering vector:
 
                                    [1] 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2 6 2
 
                                    [38] 6 2 6 1 6 1 5 2 6 1 5 5 5 1 5 5 1 1 1 1 1 5 1 1 5 1 1 1 5 1 1 5 5 1 1 1 1
 
                                    [75] 1 5 1 5 5 1 1 5 1 1 5 1 1 5 5 1 1 5 1 5 5 5 1 5 1 5 5 1 1 5 1 5 1 1 1 1 1
 
                                    [112] 5 5 5 5 5 1 1 1 1 5 5 5 4 5 4 3 4 3 4 3 4 5 4 3 4 3 4 3 4 3 4 5 4 3 4 3 4
 
                                    [149] 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4 3

                                    [186] 4 3 4 3 4 3 4 3 4 3 4 3 4 3 4
 

                                    Within cluster sum of squares by cluster:
 
                                    [1]  8062.133  7732.381 16690.857 13972.359  7742.895  4099.818
  
                                    (between_SS / total_SS =  81.1 %)
 
                                    Available components:
 
 
                                    [1] "cluster"      "centers"      "totss"        "withinss"     "tot.withinss"

                                    [6] "betweenss"    "size"         "iter"         "ifault"

                                    Visualizing the Clustering Results using the First Two Principle Components

                                    pcclust=prcomp(customer_data[,3:5],scale=FALSE)              

                                    #principal component analysis

                                    summary(pcclust)
 
                                    Importance of components:
  
                                    PC1     PC2     PC3

                                    Standard deviation     26.4625 26.1597 12.9317
 
                                    Proportion of Variance  0.4512  0.4410  0.1078
 
                                    Cumulative Proportion   0.4512  0.8922  1.0000

                                    pcclust$rotation[,1:2]

                                    PC1        PC2

                                    Age 0.1889742 -0.1309652

                                    Annual.Income..k..     -0.5886410 -0.8083757

                                    Spending.Score..1.100. -0.7859965  0.5739136

                                    set.seed(1)

                                    ggplot(customer_data, aes(x =Annual.Income..k.., y = Spending.Score..1.100.)) + 
 
                                    geom_point(stat = "identity", aes(color = as.factor(k6$cluster))) +
 
                                    scale_color_discrete(name=" ",
          
                                    breaks=c("1", "2", "3", "4", "5","6"),
             
                                    labels=c("Cluster 1", "Cluster 2", "Cluster 3", "Cluster 4", "Cluster 5","Cluster 6")) +
 
                                    ggtitle("Segments of Mall Customers", subtitle = "Using K-means Clustering")
                                
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/88882780-b5ee-4b92-b43d-97dd1208cd08)

                                    ggplot(customer_data, aes(x =Spending.Score..1.100., y =Age)) + 
  
                                    geom_point(stat = "identity", aes(color = as.factor(k6$cluster))) +
  
                                    scale_color_discrete(name=" ",
                     
                                    breaks=c("1", "2", "3", "4", "5","6"),
                    
                                    labels=c("Cluster 1", "Cluster 2", "Cluster 3", "Cluster 4", "Cluster 5","Cluster 6")) +
  
                                    ggtitle("Segments of Mall Customers", subtitle = "Using K-means Clustering")

                                    kCols=function(vec){cols=rainbow (length (unique (vec)))

                                    return (cols[as.numeric(as.factor(vec))])}

                                    digCluster<-k6$cluster; dignm<-as.character(digCluster);         

                                                                                             # K-means clusters

                                                                                             plot(pcclust$x[,1:2], col =kCols(digCluster),pch =19,xlab ="K-  means",ylab="classes")legend("bottomleft",(dignm),fill=unique(kCols(digCluster)))
 
![image](https://github.com/AishwaryaHarikrishnan/Customer-segmentation-analysis-Using-R/assets/123670163/012683ec-a272-40b6-a76d-83871384eec5)
                                                        
