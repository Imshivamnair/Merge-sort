# Merge-sort

Merge sort is defined as a sorting algorithm that works by dividing an array into smaller subarrays, sorting each subarray, and then merging the sorted subarrays back together to form the final sorted array.

**How does Merge Sort work?**

Merge sort is a recursive algorithm that continuously splits the array in half until it cannot be further divided i.e., the array has only one element left (an array with one element is always sorted). Then the sorted subarrays are merged into one sorted array.

// JavaScript program for Merge Sort

// Merges two subarrays of arr[].
// First subarray is arr[l..m]
// Second subarray is arr[m+1..r]
function merge(arr, l, m, r)
{
	var n1 = m - l + 1;
	var n2 = r - m;

	// Create temp arrays
	var L = new Array(n1); 
	var R = new Array(n2);

	// Copy data to temp arrays L[] and R[]
	for (var i = 0; i < n1; i++)
		L[i] = arr[l + i];
	for (var j = 0; j < n2; j++)
		R[j] = arr[m + 1 + j];

	// Merge the temp arrays back into arr[l..r]

	// Initial index of first subarray
	var i = 0;

	// Initial index of second subarray
	var j = 0;

	// Initial index of merged subarray
	var k = l;

	while (i < n1 && j < n2) {
		if (L[i] <= R[j]) {
			arr[k] = L[i];
			i++;
		}
		else {
			arr[k] = R[j];
			j++;
		}
		k++;
	}

	// Copy the remaining elements of
	// L[], if there are any
	while (i < n1) {
		arr[k] = L[i];
		i++;
		k++;
	}

	// Copy the remaining elements of
	// R[], if there are any
	while (j < n2) {
		arr[k] = R[j];
		j++;
		k++;
	}
}

// l is for left index and r is
// right index of the sub-array
// of arr to be sorted
function mergeSort(arr,l, r){
	if(l>=r){
		return;
	}
	var m =l+ parseInt((r-l)/2);
	mergeSort(arr,l,m);
	mergeSort(arr,m+1,r);
	merge(arr,l,m,r);
}

// Function to print an array
function printArray( A, size)
{
	for (var i = 0; i < size; i++)
	console.log( A[i] + " ");
}


var arr = [ 12, 11, 13, 5, 6, 7 ];
	var arr_size = arr.length;

	console.log( "Given array is ");
	printArray(arr, arr_size);

	mergeSort(arr, 0, arr_size - 1);

	console.log( "Sorted array is ");
	printArray(arr, arr_size);

// This code is contributed by SoumikMondal


**Output**
Given array is 
12 11 13 5 6 7 
Sorted array is 
5 6 7 11 12 13 

**Complexity Analysis of Merge Sort**
Time Complexity: O(N log(N)),  Merge Sort is a recursive algorithm and time complexity can be expressed as following recurrence relation. 

T(n) = 2T(n/2) + θ(n)

The above recurrence can be solved either using the Recurrence Tree method or the Master method. It falls in case II of the Master Method and the solution of the recurrence is θ(Nlog(N)). The time complexity of Merge Sort isθ(Nlog(N)) in all 3 cases (worst, average, and best) as merge sort always divides the array into two halves and takes linear time to merge two halves.

Auxiliary Space: O(N), In merge sort all elements are copied into an auxiliary array. So N auxiliary space is required for merge sort.

**Applications of Merge Sort:**
-Sorting large datasets: Merge sort is particularly well-suited for sorting large datasets due to its guaranteed worst-case time complexity of O(n log n).
-External sorting: Merge sort is commonly used in external sorting, where the data to be sorted is too large to fit into memory.
-Custom sorting: Merge sort can be adapted to handle different input distributions, such as partially sorted, nearly sorted, or completely unsorted data.
