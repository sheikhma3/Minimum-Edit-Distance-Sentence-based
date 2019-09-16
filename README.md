<h3>Minimum-Edit-Distance-Implementation-for-String-Word-Based-Distance</h3>

a) Character-based e.g. align “This is a cat” with “This is a dog”, distance = 6 (3
character substitutions)

b) Word-based e.g. align “This is a cat” with “That is a dog”, distance = 4 (2
word substitutions)

Implementation of Minimum Edit Distance Algorithm from scratch in Python. Minimum Edit Distance Calculates the distance between two strings Word Based Distance

Levenshtein Distance – No. of edits between two strings – Costs • Insertion = Deletion = 1 • Substitution = insertion + deletion = 2 (except substitution of identical characters, which costs 0) – E.g. from This is a cat That is a dog S S = 4 Set the cost in .ipynb file in following cell: del_cost=1 ins_cost=1 sub_cost=2

Then pass the strings in Function Parameter. It will output the minimun edit distance between the strings. There are two params in function source string and destination string

Word Based Distance
def Calculate_Minimum_edit_distance(source,target): source =source.split(' ') target =target.split(' ') n= len(source) m= len(target) MED_Matrix= np.zeros((n+1,m+1), dtype='int32') for i in range(1,n+1): MED_Matrix[i][0]=MED_Matrix[i-1][0]+del_cost for i in range(1,m+1): MED_Matrix[0][i]=MED_Matrix[0][i-1]+del_cost
for i in range(1,n+1): for j in range(1,m+1): if(source[i-1]==target[j-1]): MED_Matrix[i][j]=min([MED_Matrix[i-1][j]+del_cost,MED_Matrix[i-1][j-1]+0,MED_Matrix[i][j-1]+ins_cost]) else: MED_Matrix[i][j]=min([MED_Matrix[i-1][j]+del_cost,MED_Matrix[i-1][j-1]+sub_cost,MED_Matrix[i][j-1]+ins_cost]) #print(np.matrix(MED_Matrix)) #print(MED_Matrix[n][m]) return MED_Matrix[n][m]
