//// TASK 4 ////

// Load the CSV file
import delimited "C:/Users/berisha_shkelqim/Desktop/HotelsDataAnalysis/data/hotels-vienna.csv", clear

* Display the first few rows of the data
list in 1/10


//// TASK 5 ////

// Display data types and check for missing values 

// 1. Check for duplicates and drop them
duplicates report
duplicates drop

// 2. Check for missing values in key variables
misstable summarize hotel_id stars rating price

// Drop observations with missing values in 'stars', 'rating', or 'price'
drop if missing(stars) | missing(rating) | missing(price)

// 3. Fix incorrect data types
// For example, if 'stars' is stored as a string, convert it to numeric
destring stars, replace

// 4. Standardize categories in 'accommodation_type'
// Suppose we find variations in 'accommodation_type', we can standardize them
replace accommodation_type = "Hotel" if inlist(accommodation_type, "hotel", "Hotel", "HOTEL")

// 5. Rename variables for consistency
rename ratingta rating_TA  // Rename 'ratingta' to 'rating_TA' for clarity


//// TASK 6 ////

// 1. Select specific variables for analysis: Keep only relevant variables
keep hotel_id accommodation_type stars rating price

// 2. Create a new variable: For instance, calculate price per star
gen price_per_star = price / stars

// 3. Standardize a categorical variable: Ensure 'accommodation_type' is consistently labeled
replace accommodation_type = "Luxury Hotel" if accommodation_type == "Luxury"
replace accommodation_type = "Budget Hotel" if accommodation_type == "Budget"

// 5. List the first few observations to verify the transformations
list in 1/10

// Optional: Create a summary of the cleaned data
summarize


// Save the cleaned dataset
save "C:/Users/berisha_shkelqim/Desktop/HotelsDataAnalysis/output/cleaned_hotels_data.dta", replace


////  TASK 8 ////

// Generate summary statistics
summarize


////  TASK 9 ////

// Create the bar graph of average price by accommodation type
graph bar (mean) price, over(accommodation_type) ///
    title("Average Price by Accommodation Type") ///
    ytitle("Average Price") ///
    blabel(bar, size(small)) ///
    legend(off)

// Save the graph
graph export "C:/Users/berisha_shkelqim/Desktop/HotelsDataAnalysis/output/average_price_by_accommodation_type.png", replace
