```java

    public static void test1() {
            int[] numbers = {424327, 25745202, 670140, 617210, 2362043, 5854313, 211684, 1136784, 3447261, 192052,
                    415524, 1555, 30855902, 553145, 1784659, 7411513, 1786989, 471374, 449167, 848654,
                    5336251, 30796782, 1564944, 1136492, 2140506, 883025, 2258889, 29904166, 16237043};

            long totalSum = 0;
            for (int number : numbers) {
                totalSum += number;
            }
            long targetSum = totalSum / 4;

            // 使用贪婪算法分组
            List<List<Integer>> groups = new ArrayList<>();
            for (int i = 0; i < 4; i++) {
                groups.add(new ArrayList<>());
            }
            long[] currentSums = {0, 0, 0, 0};

            // 将数组转换为列表并排序
            List<Integer> numberList = new ArrayList<>();
            for (int number : numbers) {
                numberList.add(number);
            }
            Collections.sort(numberList, Collections.reverseOrder());

            for (int number : numberList) {
                int minIndex = 0;
                for (int i = 1; i < 4; i++) {
                    if (currentSums[i] < currentSums[minIndex]) {
                        minIndex = i;
                    }
                }
                groups.get(minIndex).add(number);
                currentSums[minIndex] += number;
            }

            // 打印结果
            for (int i = 0; i < 4; i++) {
                System.out.println("Group " + (i + 1) + ": " + groups.get(i) + ", Sum: " + currentSums[i]);
            }

            System.out.println("\nTarget Sum: " + targetSum);
            Dict dict = Dict.of();
        }
```
