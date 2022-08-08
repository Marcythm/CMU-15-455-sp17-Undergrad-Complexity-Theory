3SAT to 3COL: construction
TODO: HornSAT is P-complete


================================



hw2
1. proof idea: proof by contradiction
   reduce to another undecidable problem
   L = { <M> : M always halts }

2. a. simple
   b. record every step ? 
      record every state ?
      to produce 2|w|^2 length string on the same tape

3. not hard
4. intuitive idea: within O(sqrt n) time the TM cannot know the exact info about n, so the sqrt n is unrelated w/ n in fact.
   informal descriptive proof: for an input w, TM halts within k=O(sqrt |w|) steps, then it can know at most the first k bits info of w, i.e. it's enough to halt with the first k bits of w. Use w[:k] as new input, then ...

hw3
1. (not even EXP) just apply time hierarchy theorem on t(n) = 2^2^n.
2. (coloring better than brute force) trivial idea of dfs, 2^n to decide each vertex's color, poly(n) to check
3. (CSPs) initialize solution with all 1s, then for each constraint like a_i = 0, assign a_i = 0 and spread 0 around the constraints like a_i >= a_j. If spread to a variable pinned on 1, then not satisfiable.
4. (poly-time can be syntactically checked) use a UTM to simulate M, together with a counter kn^k.

hw4
2. (NP in EXP) for L in NP, exists k s.t. L has a verifier in O(n^k), prove all proof for an instance I of L has length O(|I|^k), then enumerate all possible solutions is in EXP.
3.2 
  1. 一个 clause 里面如果只有一个 literal，那么可以 eliminate 掉，不影响结果，得到每个 clause 都包含多个 literal 的 CNF
  2. 如果一个 literal 所有 occurrences 都是 positive/negative，可以直接取值 T/F，不影响结果，得到每个 literal 都以 positive & negative 的形式出现过的 CNF（如果又出现 unit clause 那么重复 1）
  3. 还剩下的每个 literal 都直接取 F

hw5
0. 需要有一个 f 把所有 satisfiable 的映射成 unsatisfiable, un-xx 的映射成 sat
1. trivial
2. with |Q| * |\Gamma| * 2 's constant factor slowdown
3. (Implicit 4COL in NEXP) exploit all edges in EXP, then nondeterministically solve 4COL. the max length is EXP, N + EXP = NEXP in total
4. (reducing P to 3COL) 不会。

hw6
1. (3-coloring with unary constraints.) denotes all the unary constraints C, forall x, y in C where col(x) \neq col(y), add edge (x, y) in new graph G'.
2. (NP-hard but not NP-complete.) 4COL \leq IMPLICIT-4COL by constructing the circuit corresponding to the graph.
3. (MAX-2SAT.) (a \/ b \/ c) \mapsto (a \/ s) (b \/ s) (c \/ s) (~a \/ ~s) (~b \/ ~s) (~c \/ ~s), k = 5 #clauses
4. forall A in NP, assume A has verifier M_A and complexity f_A(n), thus given a instance <I> of A, nondeterministically choose 1^w where w <= f_A(|I|), then compute <M_A, I, 1^w, 1^f_A(|I|)>.
