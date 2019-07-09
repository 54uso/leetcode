#37 - Sudoku Solver

### Problem
<p>Write a program to solve a Sudoku puzzle by filling the empty cells.</p>

<p>A&nbsp;sudoku solution must satisfy <strong>all of&nbsp;the following rules</strong>:</p>

<ol>
	<li>Each of the digits&nbsp;<code>1-9</code> must occur exactly&nbsp;once in each row.</li>
	<li>Each of the digits&nbsp;<code>1-9</code>&nbsp;must occur&nbsp;exactly once in each column.</li>
	<li>Each of the the digits&nbsp;<code>1-9</code> must occur exactly once in each of the 9 <code>3x3</code> sub-boxes of the grid.</li>
</ol>

<p>Empty cells are indicated by the character <code>&#39;.&#39;</code>.</p>

<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png" style="height:250px; width:250px" /><br />
<small>A sudoku puzzle...</small></p>

<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png" style="height:250px; width:250px" /><br />
<small>...and its solution numbers marked in red.</small></p>

<p><strong>Note:</strong></p>

<ul>
	<li>The given board&nbsp;contain only digits <code>1-9</code> and the character <code>&#39;.&#39;</code>.</li>
	<li>You may assume that the given Sudoku puzzle will have a single unique solution.</li>
	<li>The given board size is always <code>9x9</code>.</li>
</ul>


### Code
```java
public class Solution {
    
    private final static List<Character> chars = Arrays.asList('1', '2', '3', '4', '5', '6', '7', '8', '9');

    private List<Node> nodes;

    private char[][] board;

    private boolean rows[][];

    private boolean cols[][];

    private boolean square[][];

    public void solveSudoku(char[][] board) {
        this.board = board;
        this.rows = new boolean[9][10];
        this.cols = new boolean[9][10];
        this.square = new boolean[9][10];
        this.nodes = new LinkedList<Node>();
        for (int i = 0; i < 9; ++i) {
            for (int j = 0; j < 9; ++j) {
                if (this.board[i][j] != '.') {
                    int val = this.board[i][j] - '0';
                    this.rows[i][val] = true;
                    this.cols[j][val] = true;
                    this.square[i / 3 * 3 + j / 3][val] = true;
                }
            }
        }
        for (int i = 0; i < 9; ++i) {
            for (int j = 0; j < 9; ++j) {
                if (board[i][j] == '.') {
                    Set<Character> set = new HashSet<Character>(chars);
                    Node node = new Node(j, i, i / 3 * 3 + j / 3, set);
                    this.removeNotImpossible(node);
                    this.nodes.add(node);
                }
            }
        }
        Collections.sort(this.nodes, new Comparator<Node>() {
            @Override
            public int compare(Node o1, Node o2) {
                return o1.getSet().size() - o2.getSet().size();
            }
        });
        this.dfs(this.nodes);
    }

    private boolean dfs(List<Node> nodes) {
        if (nodes.isEmpty()) {
            return true;
        }
        Node cur = nodes.remove(0);
        for (char ch : cur.getSet()) {
            int val = ch - '0';
            if (this.check(cur.getX(), cur.getY(), cur.getIndex(), val)) {
                this.board[cur.getY()][cur.getX()] = ch;
                this.rows[cur.getY()][val] = true;
                this.cols[cur.getX()][val] = true;
                this.square[cur.getIndex()][val] = true;
                if (this.dfs(nodes)) {
                    return true;
                }
                this.board[cur.getY()][cur.getX()] = '.';
                this.rows[cur.getY()][val] = false;
                this.cols[cur.getX()][val] = false;
                this.square[cur.getIndex()][val] = false;
            }
        }
        nodes.add(0, cur);
        return false;
    }

    private void removeNotImpossible(Node node) {
        for (int i = 1; i < 10; ++i) {
            if (!this.check(node.getX(), node.getY(), node.getIndex(), i)) {
                node.getSet().remove((char)('0' + i));
            }
        }

    }

    private boolean check(int x, int y, int index, int val) {
        return !this.rows[y][val] && !this.cols[x][val] && !this.square[index][val];
    }

    private class Node {

        private int x;

        private int y;

        private int index;

        private Set<Character> set;

        public Node(int x, int y, int index, Set<Character> set) {
            this.x = x;
            this.y = y;
            this.index = index;
            this.set = set;
        }

        public int getX() {
            return this.x;
        }

        public int getY() {
            return this.y;
        }

        public int getIndex() {
            return this.index;
        }

        public Set<Character> getSet() {
            return this.set;
        }

    }
    
}
```
### Link: [https://leetcode.com/problems/sudoku-solver/](https://leetcode.com/problems/sudoku-solver/)
