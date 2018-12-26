# java_groupy_and_sum

//example in java8 on how to group by days and sum its values:

package test;

import java.math.BigDecimal;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class Graph {

	public static void main(String[] args) {

		//3 apple, 2 banana, others 1
        List<Item> items = new ArrayList<Item>(Arrays.asList(
                new Item("apple", 10, new BigDecimal("9.99")),
                new Item("banana", 20, new BigDecimal("19.99")),
                new Item("orang", 10, new BigDecimal("29.99")),
                new Item("watermelon", 10, new BigDecimal("29.99")),
                new Item("papaya", 20, new BigDecimal("9.99")),
                new Item("apple", 10, new BigDecimal("9.99")),
                new Item("banana", 10, new BigDecimal("19.99")),
                new Item("apple", 20, new BigDecimal("9.99"))
        ));

        Map<String, Long> counting = items.stream().collect(
                Collectors.groupingBy(Item::getName, Collectors.counting()));

        System.out.println(counting);

        Map<String, Integer> sum = items.stream().collect(
                Collectors.groupingBy(Item::getName, Collectors.summingInt(Item::getQty)));

        System.out.println(sum);

        
        /// test with days
        List<Day> days = new ArrayList<Day>(Arrays.asList(
                new Day(1, 9.99),
                new Day(1, 29.99),
                new Day(2, 3.99),
                new Day(3, 5.99)
        ));

        // group by day and sum values
        Map<Integer, Double> countingByDay = days.stream().collect(
        		Collectors.groupingBy(Day::getDay, Collectors.summingDouble(Day::getPrice)));

        System.out.println(countingByDay);        
        

	}

}
