## Linear Algebra Basic Concepts/Technics
### Group theory 
Insertion:[title](https://www.example.com)
1. Single Operation properties:
   - Group: "Ass+Ive+Ele" Integer addtion, Assoiciative+Inverse element+Identity element.  
       Assiciativity结合:2,3 swap allowed.允许后两项结合.       
   - Abelian(交换) G: with comminitivity交换. i.e. ab=ba.  


2. Duo-Operation properties:(复运算结构)
   - __Ring__: **Abelian addition** + *monoid*(幺半群i.e. **A+E multipy**) multipication+**Distributivity M2A** from mul to addition.
   - __Field__: Ring+**inverse of Mul too**.  Example:(Q,+,\*) & (R,+,\*). !(Z,+,*). **Typically: Field K^m\*n**
  
3. Conclusion: A __Field__ is **Add & Mul with both AIE and Distributivity from Mul to Add. Note that 乘法0元不要求有逆** 


### Terminology of LA
#### Important notations:
- $A_{ij}$ = $(a_{ij})$; Specially: $f(A)_{ij}$ = Bij where B = f(A).
- A下标n, n属于K.表示K阶方阵.
- diag(a,a): 2阶主对角线矩阵，每个元素为a. 通常也用来表示复平面上的实数.
- $\frac {1}{a^2+b^2} *$ *to be fullfilled*
- real part/**complex part**: Re(z),Im(z).实部虚部函数

#### Basic concepts && Important denotations/names:  
- Entry:element~stuff collected in a matrix.//元素 
- Vector:1*2 matrix //向量的矩阵表示,
  - Relevently: 1\*1 matrix took as a scalar/constant.//
  - 标量和向量的矩阵表示(在矩阵运算中，由于一些巧合，默认通用)
  - Generally we take it as whichever is convenient. But more column.无歧义自己分析行或列，更多情况下，一个向量是一个列矩阵。
- i-th row & j-th column (of Matrix A) = **a(i,j)**;
  - m,n 通常用作最大row和column.
- row vector & column vector. trivial.
- Transposed: 转置  
- Square/Quadratic: 方阵  
- Symmatric: 对称.  
- Sparse: One ***denotes*** a matrix with mostly zero entries as a sparse matrix. 稀疏矩阵，0多.  
- Modeling terminologies:  
  - *structurally symmetric* but maybe not *numerically symmetric* ?  
  - *Transition matrix* 转移矩阵，用于描述概率系统的变化。  
- diagonal:对角线  
- diagonal matr: ~
- Diagonal Dominant Matrices: 对角线优势矩阵，对角线上的元素大于其它所有元素的绝对值之和
- positive define: 正定矩阵，A, 对于任何向量x, x^TAx>0.
   - theorem：对角线优势且镜像的矩阵是正定的。
- conjugate transpose: denoted as $A^H$, 对于每一个元素，全取共轭。**共轭转置**
- Hermitian Matrices: A = $A^H$.
- Skew Hermitino Ma.: A = $-A^H$.
- De Moivre’s Theorem: something triangular.
- Fallacy: 谬论
- kernel：核，右乘矩阵得到0的向量的集合。
- Involutory Matrices：合合矩阵? $A^2 = I$.
- Band Matrices: 带状矩阵，可能对称也可能不对称。properties to be fullfilled.


  
##### Complex Numbers
- (C,+)交换/Abelian.
- 定义: 常规定义以及矩阵式定义aI+bi.
- complex conjugate: 共轭复数，denoted as z上面一横.
- magnitude:绝对值|z|
- real part/**complex part**: Re(z),Im(z).
- rotations matrix: cos\~sin \/\/ -sin\~cos的一个2\*2矩阵.**旋转矩阵** 写作A(θ)
  - **复数的矩阵表示可以视作旋转一个角度再扩大绝对值倍数的旋增矩阵,旋转角度恰为复数和x+轴的夹角**这也可以通过旋转矩阵本身的定义，再分解标量单位化来得出。旋转矩阵的形式和复数基本一致(由于实数是退化的，缺少旋转性或旋转性为0度)。
 
  
#### Linear System
- coecient matrix: 系数矩阵
- homogeneous：同伦？同质化？当linear system的系数侧形成的列向量b=0.
- solution: 解的集合
- elementary row operations：基本行变换
- extended coecient matrix：denoted as (A|b)**增广矩阵** **简化表示为A上加一个波浪**
- *Language*: We can easily read off the solutions now.
- row echelon form: 行梯形，元素在右上角。
- reduced row echelon form：简化行梯形：行梯形矩阵的基础上，行首元素为1
- **Gaussian Elimination Algorithm：高斯消元算法**
  1. transform 把增广转换到**简化**行梯形形式
  2. 判定解的数量 by 读有几个非零**leading virable**，例如最下一行的首元素**列index**是否大于增广前总列数。若是则无解。也可以说是观察**rank**
  3. 复杂的formula.
- rank: 级，在简化矩阵中，读取(增广前部分)非零行的数。
  1. 若无非零行，或rank=\~.则成为regular.常规矩阵
  2. 否则，成为singular.(有非零行)
- Theorem: A linear system has a solution if the rank of the coecient matrix equals the
rank of the extended coecient matrix. 这里的solution应该是只有一个？而不是集合的意思。待定
- **Practical Gaussian Elimination:高斯消元法**:
  1.和算法版本几乎一样，但只需化成行梯形矩阵。
  2.判定解的数，通过rank
  3.回代入得到简化方程，快速读出解集合。
- LES(Linear System) with **Complex** number: Split/convert the equation to field R. **由于实部和虚部互不影响**把方程分解成数量翻倍的新方程求解是一个技巧。也可以直接求解。

#### Matrix Factorizations 矩阵分解，用于提高LES中的算法复用性。
- LU Fac.:LU分解. 技术: **令L为下三角矩阵，并且主对角线元素均为1(这是一个很好的构造，但不是必须的)；U为上三角矩阵。** 算法大约是上到下，左到右计算。
- LL^T Fac: 亦称为**Cholesky** Factorization.LL^T分解，对于**symmetric & diagonal domaint matrix可以使用更加简化的算法，在此特里中，对角线的元素恰为根号下原矩阵对角线对应元素的值。**

#### Vector Space
- to be fullfilled

### Operatons
- Addition, when need to be distict with other addtion, use *squeard "+" sign*.  
  - Abelian.   
- scalar: 标量乘法.  
- Mul: non-communitive but all good. **非交换 非交换 非交换**  
  - Duo-Structure: Add & Mul: **Ring/communitive**  
- Inverse: A^-1(默认为右逆元)  
  - Factor: exist Left- and Rigght- Inverse.
- Transpose/transposition: As mentioned, 转置.
- (Upper/Lower)Triangular Ma.:上下三角矩阵. Properties: to be filled.
- 

## Means of Proofs/language style/technic.
 **language**:
 - we have == it holds.
 **Induction**:  
  - :one: Induction Base i.e. The useful situation we have.
  - :two: Assumption: The proposition/equation we want to proof true. Usually constructed as **IfP(n)-->P(n+1/n-1 etc.)**
  - :three: Induction Step?: **right hand side/RHS = LHS** technic. Or by proper language.
  - 💁‍♂️:Construction approaches: ~~~
    




  







  





<p>bandwidth: calculated from the main DA, means how far can you get to the first nonzero entry bu minus 1. Z.B. for any E the bandwidth is zero.</p><br><br>
<p>Upper/lower bandwidth: upper the main diagonal called upper bandwidth(visually), sync to lower. So for an E/identity matrix, upper=lower.</p>
