# Equal-Sum-Grid-Partititon-1
leetcode problem No:3546

class Solution {
    public boolean canPartitionGrid(int[][] grid) {
        int m = grid.length, n = grid[0].length;
        
        long total = 0;
        for (int[] row : grid) {
            for (int val : row) {
                total += val;
            }
        }

        // Try horizontal cuts
        long sum = 0;
        for (int i = 0; i < m - 1; i++) { // ensure non-empty bottom
            for (int j = 0; j < n; j++) {
                sum += grid[i][j];
            }
            if (sum == total - sum) return true;
        }

        // Try vertical cuts
        sum = 0;
        for (int j = 0; j < n - 1; j++) { // ensure non-empty right
            for (int i = 0; i < m; i++) {
                sum += grid[i][j];
            }
            if (sum == total - sum) return true;
        }

        return false;
    }
}