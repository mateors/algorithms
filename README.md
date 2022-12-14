# Algorithms
Learing algorithms by reading books, watching videos, looking at others code and many more...
The best way of doing this is by coding in practice.

### What is recursion?
> In computer science, recursion is a programming technique using function or algorithm that calls itself one or more times until a specified condition is met at which time the rest of each repetition is processed from the last one called to the first.

### What is Divide and conquer?
> In computer science, divide and conquer is an algorithm design paradigm.
A divide and conquer algorithm is a strategy of solving a large problem by. breaking the problem into smaller sub-problems. solving the sub-problems, and. combining them to get the desired output.

![d&c](https://miro.medium.com/max/1150/1*kPXTT7fBFyeFjEYA0RqwaQ.png)

A divide-and-conquer algorithm recursively breaks down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly.

## [Quicksort algorithm](https://www.enjoyalgorithms.com/blog/quick-sort-algorithm)
> Quicksort is a sorting algorithm. The algorithm picks a pivot element and rearranges the array elements so that all elements smaller than the picked pivot element move to the left side of the pivot, and all greater elements move to the right side. Finally, the algorithm recursively sorts the subarrays on the left and right of the pivot element.

* Using recursion technique
* Divide and conquer technique or strategy

![quicksort](https://cdn-images-1.medium.com/max/600/1*YBBPKTeYJs1eI_4hEhntIg.png)

Steps to implement of quicksort algorithm
* Find the pivot (lets pick it from the first or the last element of an array)
* Now find the elements smaller than the pivot and the elements larger than the pivot.
    #### This is called Partitioning, now we have
    * A sub-array of all the numbers less than the pivot (not sorted yet)
    * The pivot
    * A sub-array of all the numbers greater than the pivot (not sorted yet)

### Quicksort algorithm JS implementation

```js
function quicksort(numbers){

  //base case 1, empty array
  if (numbers.length===0){
    return numbers
  }

  //base case 2, array with one element
  if (numbers.length===1){
    return numbers
  }

  //base case 3, array with two element
  if (numbers.length===3){
    if (numbers[0]<numbers[1]){
        numbers[0]=numbers[1];
        numbers[1]=numbers[0];
    }
    return numbers

  }

  //recursive case
  var pivot=numbers[0];
  var left=[];
  var right=[];

  for(let x of numbers.slice(1)){
    if (x<pivot){
        left.push(x);
    }
    //left.push(pivot);
    if (x>pivot){
        right.push(x);
    }
  }
  return quicksort(left).concat([pivot],quicksort(right));

}
```

## Time Complexity
> O(n log n)

## More precise version

```js
function quicksort(numbers) {

    if (numbers.length < 2) {
        return numbers;

    } else {
        var pivot = numbers[0];
        var left = numbers.slice(1).filter(function(x) {
            return x <= pivot;
        });
        var right = numbers.slice(1).filter(function(x) {
            return x > pivot;
        });
        return quicksort(left).concat([pivot], quicksort(right));
    }
}
```

## Golang version of quicksort

```go

func quicksort(numbers []int) []int {
	if len(numbers) < 2 {
		return numbers
	} else {
		pivot := numbers[0]
		left := []int{}
		right := []int{}
		for _, i := range numbers[1:] {
			if i <= pivot {
				left = append(left, i)
			} else {
				right = append(right, i)
			}
		}
		return append(append(quicksort(left), pivot), quicksort(right)...)
	}
}
```

