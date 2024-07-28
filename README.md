import java.util.Scanner;
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        scanner.close();
        
        int[] result = nextGreaterElements(nums);
        
        for (int num : result) {
            System.out.print(num + " ");
        }
    }
    
    public static int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        Stack<Integer> stack = new Stack<>();
        
        for (int i = 2 * n - 1; i >= 0; i--) {
            while (!stack.isEmpty() && nums[stack.peek()] <= nums[i % n]) {
                stack.pop();
            }
            if (i < n) {
                result[i] = stack.isEmpty() ? -1 : nums[stack.peek()];
            }
            stack.push(i % n);
        }
        
        return result;
    }
}
