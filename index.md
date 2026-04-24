# Guiding Question
We wanted to consider whether COMP110 teachers should make it more explicit what exactly the autograder is looking for in exercises, so that students have an easier time learning from their mistakes.

# Analysis

Based on our raw survey data and our guiding idea we want to look at the specific columns : oh_visits, programming_effective, oh_effective, understanding, algorithms_objective. We use the head function here to make it easier to confirm that the rest of our functions are working properly.
'from data_utils import select
from data_utils import head

from data_utils import columnar

row_table = read_csv_rows("data/survey_izzi.csv")

column_table = columnar(row_table)

s_column_table = select(column_table, ["oh_visits", "programming_effective", "oh_effective", "understanding", "algorithms_objective"])

head(select(column_table, ["oh_visits", "programming_effective", "oh_effective", "understanding", "algorithms_objective"]), 5)
'

Next we create a line graph with programming effectiveness as the explainatory variable and office hour visits as the response variable. We chose to compare these to see whether a students office hour visits may depend on how they view the assignments. We hypothesize that a negative view of these assignments would tend towards lower engagement with the class which would show as lower office hour visits in the data.
'from data_utils import select
from data_utils import convert_columns_to_int
from data_utils import columnar
from data_utils import filter_empty_values
from data_utils import columnar_inv
from data_utils import read_csv_rows
import seaborn as sns
sns.set_theme()

row_table = read_csv_rows("data/survey_izzi.csv")

column_table = columnar(row_table)

s_column_table = select(column_table, ["oh_visits", "programming_effective"])
s_row_table = columnar_inv(s_column_table)
filtered_s_row_table = filter_empty_values(s_row_table)
filtered_s_column_table = columnar(filtered_s_row_table)
int_column_table = convert_columns_to_int(filtered_s_column_table, ["oh_visits", "programming_effective", "oh_effective", "understanding", "algorithms_objective"])

sns.relplot(int_column_table, kind="line",
            x="programming_effective", y="oh_visits")
'
Then we create a line graph comparing general understanding of coures content to views of the effectiveness of the programming exercises. We hypothesize that those that understand the course content will have a more positive view of the assignments which will show up  as a positive relationship in the graph. This would point towards assignments being difficult to understand especially for beginners or those struggling.

'from data_utils import select
from data_utils import convert_columns_to_int
from data_utils import columnar
from data_utils import filter_empty_values
from data_utils import columnar_inv
from data_utils import read_csv_rows
import seaborn as sns
sns.set_theme()

row_table = read_csv_rows("data/survey_izzi.csv")

column_table = columnar(row_table)

s_column_table = select(column_table, ["understanding", "programming_effective"])
s_row_table = columnar_inv(s_column_table)
filtered_s_row_table = filter_empty_values(s_row_table)
filtered_s_column_table = columnar(filtered_s_row_table)
int_column_table = convert_columns_to_int(filtered_s_column_table, ["oh_visits", "programming_effective", "oh_effective", "understanding", "algorithms_objective"])

sns.relplot(int_column_table, kind="line",
            x="understanding", y="programming_effective")
'

For this graph we use a point plot comparing course understanding to office hour visits. We wanted to see whether understanding contributed or detracted from students desire to seek out help at office hours. We hypothesize that these variable would have a negative relationship.

'from data_utils import select
from data_utils import convert_columns_to_int
from data_utils import columnar
from data_utils import filter_empty_values
from data_utils import columnar_inv
from data_utils import read_csv_rows
import seaborn as sns
sns.set_theme()

row_table = read_csv_rows("data/survey_izzi.csv")

column_table = columnar(row_table)

s_column_table = select(column_table, ["understanding", "oh_visits"])
s_row_table = columnar_inv(s_column_table)
filtered_s_row_table = filter_empty_values(s_row_table)
filtered_s_column_table = columnar(filtered_s_row_table)
int_column_table = convert_columns_to_int(filtered_s_column_table, ["oh_visits", "programming_effective", "oh_effective", "understanding", "algorithms_objective"])

sns.catplot(int_column_table, kind="point",
            x="understanding", y="oh_visits")'

Finally we use a line graph to compare course understanding to views on algorithm objectiveness. We wanted to see how understanding of computer programming effected braoder views than just those that are strictly related to COMP110. We hypothesized that there would be a negative correlation between these 2 values because those with greater computing knowledge would better understand the pitfalls of algorithms, and thus have a more modest view while those with lesser undertanding would have a more all encompoassingly positive view of algorithms.

'from data_utils import select
from data_utils import convert_columns_to_int
from data_utils import columnar
from data_utils import filter_empty_values
from data_utils import columnar_inv
from data_utils import read_csv_rows
import seaborn as sns
sns.set_theme()

row_table = read_csv_rows("data/survey_izzi.csv")

column_table = columnar(row_table)

s_column_table = select(column_table, ["understanding", "algorithms_objective"])
s_row_table = columnar_inv(s_column_table)
filtered_s_row_table = filter_empty_values(s_row_table)
filtered_s_column_table = columnar(filtered_s_row_table)
int_column_table = convert_columns_to_int(filtered_s_column_table, ["oh_visits", "programming_effective", "oh_effective", "understanding", "algorithms_objective"])

sns.relplot(int_column_table, kind="line",
            x="understanding", y="algorithms_objective")'

# Conclusion
