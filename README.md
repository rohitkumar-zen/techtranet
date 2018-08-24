package my.practice;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Random;

public class QuickSort {

    public static void main(String... args) {
        Integer[] input = {2, 4, 9, 6, 1, 8, 3, 7, 5, 11, -1};
        int length = input.length;
        Random r = new Random();
        Integer[] resultList = new Integer[input.length];
        divideQuickSort(input, resultList, input.length, new Integer[1]);
        System.out.println("Result Array is :: " + Arrays.asList(resultList));
    }

    /**
     *
     * @param inputList
     */
    private static void divideQuickSort(Integer[] inputList, Integer[] resultList,  int pivot, Integer[] rightArray) {
        System.out.println("pivot = " + pivot );
        if(inputList !=null && inputList.length != 0) {

            int inputLength = inputList.length;
            System.out.println("Input list --- --- " + Arrays.asList(inputList));
            Random r = new Random();
            int rand = r.nextInt(inputLength);
            System.out.println("Random length :: " + rand);
            List<Integer> left = new ArrayList<>();
            List<Integer> right = new ArrayList<>();
            Integer randomInteger = null;
            int leftCounter = 0;
            int rightCounter = 0;
            for (int i = 0; i < inputLength; i++) {
                int random = inputList[rand];
                System.out.println("Random Integer :: " + random + "  --> i " + inputLength);
                randomInteger = random;
                if (inputList[i] < random) {
                    left.add(inputList[i]);
                    leftCounter++;
                } else if (inputList[i] > random) {
                    right.add(inputList[i]);
                    rightCounter++;
                }


            }
            int pivotSelected = left.size();
            resultList[pivotSelected] = inputList[rand];
            divideQuickSort(left.toArray(new Integer[left.size()]), resultList, pivotSelected, right.toArray(new Integer[right.size()]));
            System.out.println("Pivot " + pivot + "  pivot selected " + pivotSelected);
            System.out.println("Intermediate arrays :: " + Arrays.asList(resultList));
        }
           /* if(left != null && !left.isEmpty()) {
                resultList[left.size()] = randomInteger;
            }*/
//                if(left != null && !left.isEmpty())

            int rightValue =0;
            int rightRandom = 0;
            List<Integer> rightLeft = new ArrayList<>();
            List<Integer> rightRight = new ArrayList<>();
            int value = 0;
            if(rightArray != null && rightArray.length > 0) {
                Random r = new Random();
                rightRandom = r.nextInt(rightArray.length);
                rightValue = rightArray[rightValue];
                for(int j : rightArray) {
                    if(j < rightValue) {
                        rightLeft.add(j);
                    } else {
                        rightRight.add(j);

                    }
                }
                resultList[pivot + rightLeft.size()] = inputList[rightValue];
                divideQuickSort(rightLeft.toArray(new Integer[rightLeft.size()]), resultList, rightLeft.size(), rightRight.toArray(new Integer[rightRight.size()]));
            }



            /*if(isLeft) {
                if(data < randomInteger){
                    resultList[pivotSelected] = inputList[rand];
                } *//*else {
                    resultList
                }*//*

            } else if(isRight) {
                resultList[pivot + pivotSelected] = inputList[rand];
            } else if(!isLeft && !isRight) {
                resultList[pivotSelected] = randomInteger;
            }*/

              /*  if(right != null && !right.isEmpty())
                    divideQuickSort(right.toArray(new Integer[right.size()]), resultList, false, true, pivotSelected, inputList[pivotSelected]);*/

        }





    /*public static List<Integer> quickSort(int left, int rand, int right) {

    }*/
}
