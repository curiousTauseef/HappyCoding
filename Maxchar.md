Given a string, find the length of the longest substring without repeating characters. 
  For example, the longest substring without repeating letters for "abcabcbb" is "abc",
        which the length is 3. For "bbbbb" the longest substring is "b", with the length of 1.

Given a string ,return the character that is most commonly used in the string
Example :

//maxChar("abcccccccd") ==="C"
//MaxChar("apple 1231111") === "1".

                or 

What is the most common character in the String .

                or 

Does String A  have the same character as string B ( is it  an anagram) ?


                or

Does the given String have any repeadted character in it.


## 1 

    			package com.khan.vaquar.example;

			import java.util.HashMap;
			import java.util.Iterator;
			import java.util.Set;

			public class MaximumOccurringCharacter {

				public static void findMaximumOccurring(String input) {
					int maxCount = 0;
					HashMap<Character, Integer> map = new HashMap<>();
					char[] chars = input.toCharArray();
					for (int i = 0; i < chars.length; i++) {
						char c = chars[i];
						System.out.println("chars="+c);
						//
						if (map.containsKey(c)) {
							int count = map.get(c);
							count++;
							if (maxCount < count)
								maxCount++;
							map.put(c, count);
						} else {
							map.put(c, 1);
						}
					}

					Set set = map.keySet();
					Iterator<Character> iterator = set.iterator();
					while (iterator.hasNext()) {
						char key = iterator.next();
						// check count
						if (map.get(key) == maxCount) {
							System.out.println("Character: " + key + " has occurred max times:  " + maxCount);
						}
					}
				}

				public static void main(String[] args) {
					String input = "tutorial horizon";
					System.out.println("Input- " + input);
					findMaximumOccurring(input);
					System.out.println("----------------------");
					String input2 = "abcabcdefabcab";
					System.out.println("Input- " + input2);
					findMaximumOccurring(input2);
				}

			}





----------------------------------------------------------------------------------------------------
##2


public class MaxOccuranceOfChar{
   
public static String MaxOccuredChar(String str) {
 
        char[] array = str.toCharArray();
        int maxCount = 1;
        char maxChar = array[0];
 
               for(int i = 0, j = 0; i < str.length() - 1; i = j){
               int count = 1;
                   while (++j < str.length() && array[i] == array[j]) {
                   count++;
                   }
 
           if (count > maxCount) {
                maxCount = count;
                maxChar = array[i];
           }
 
         }
 
           return (maxChar + " = " + maxCount);
       }

            public static void main(String[] args) {
  
                   String str1=MaxOccuredChar("instanceofjava");
                   System.out.println(str1);
 
                   String str2=MaxOccuredChar("aaaabbbccc");
                   System.out.println(str2);
 
                   String str3=MaxOccuredChar("ssssiiinnn");
                   System.out.println(str3);
 
                    String str4=MaxOccuredChar("jaaaavvvvvvvvaaaaaaaaaa");
                    System.out.println(str4);
 
                  }

            }







----------------------------------------------------------------------------------------------------------


# Java Stream word count


- Convert the list as a stream
- Apply flatMap() operation to convert the List<Collection of words> to List<each Word>. we are trying to flatten the collection.
  Convert each word to lower case.
- Use collect() operation to group it based on the word and apply count operation.
- Print the result
- print max 




           List<String> list = new ArrayList<>();
              list.add("There are many places in this world to travel around.");
              list.add("Sikkim is one of the best places in India.");
              list.add("Once has to take atleast 10 days to visit Sikkim and enjoy its scenic beauty.");



					public class StaticReference {
						public static void main(String[] args) {
						list
						  .stream()
						  .flatMap(i -> Arrays.stream(i.split(" ")))
						  .map(i -> i.toLowerCase())
						  .collect(Collectors.groupingBy(i -> i, Collectors.counting()))
						  .forEach((k, v) -> System.out.println(k +" - "+ v));

						}
					}






- https://howtodoinjava.com/java8/stream-max-min-examples/
