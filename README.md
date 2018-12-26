package test;

import java.math.BigDecimal;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;


public class Graph {
	
	public static int nDays = 0;

	// method to set number of days
	public static void setNumberOfDays(int days) {
		nDays = days;
		return;
	}

	// method to return number of days
	public static int getNumberOfDays() {
		return nDays;
	}
	
	public static void main(String[] args) {

		// input 5 days of data
        List<Day> days = new ArrayList<Day>(Arrays.asList(
                new Day(1, 9.99),
                new Day(1, 29.99),
                new Day(2, 3.99),
                new Day(3, 5.99),
                new Day(4, 3.99),
                new Day(4, 2.00),
                new Day(4, 5.00),
                new Day(5, 10.00)
        ));

        // group by day and sum values
        Map<Integer, Double> countingByDay = days.stream().collect(
        		Collectors.groupingBy(Day::getDay, Collectors.summingDouble(Day::getPrice))
        );

        // saves number of days
        setNumberOfDays(countingByDay.size());
        
        // prints number of days by calling a method and passing the size value of the Map object
        System.out.println("--------------------------------------------");
        System.out.println("How many days? " + getNumberOfDays());
        System.out.println("--------------------------------------------");
        
        // prints out summed values for each day to be used on the graphic charts
        for(int x = 1; x<=countingByDay.size(); x++) {
        	System.out.println("Day " + x + ": " + countingByDay.get(x));	
        }
        
	}
	
}
