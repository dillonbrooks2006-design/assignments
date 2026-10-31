# AI101 Assignment 4 — GitHub Project

## Contents
- `notebooks/Assignment4_Task1_Financial_Data.ipynb` — Task 1: Gemini analysis and stock-price predictions.
- `notebooks/Assignment4a_Task2_Used_Cars.ipynb` — Task 2: same workflow using a different dataset.
- `data/finance_data.csv` — synthetic financial practice dataset.
- `data/used_car_prices.csv` — synthetic used-car practice dataset.

## Important dataset note
Both CSV files in this project are **synthetic datasets generated for this assignment practice**. They are not real stock-market or used-car observations. If your instructor requires the original `finance_data.csv` or the dataset you used in Assignment 2, replace the matching CSV with that required file before submitting.

## How to run in Google Colab
1. Download this repository as a ZIP and extract it.
2. Open each `.ipynb` file in Google Colab.
3. Upload the matching CSV from the `data` folder when the notebook asks for it.
4. Run the cells from top to bottom.
5. Enter your own Gemini API key when prompted. Do not paste your API key into a public notebook or commit it to GitHub.
6. Save the notebook after it runs. Keep the output cells, including the Gemini analysis and graph, for your submission.

## Task 1 written explanation (adapt after running)
The prediction output is Gemini's estimate of the stock price for each company row. The actual and predicted columns can be compared to see how close the estimates are. The mean absolute error reports the average size of the prediction error in the same units as the stock price. Because Gemini is a language model responding to a prompt, its predictions may vary and should not be treated as verified financial forecasts.

This approach differs from simply asking an AI assistant to write code: in this assignment, the CSV data itself is included in a prompt sent directly to the Gemini model, and Gemini is asked to analyze the data and produce predictions. The Python notebook then converts the text response into a DataFrame and plots the results. The handout does not describe the exact methods from Assignments 2 and 3, so add a specific comparison to those assignments based on the work you actually completed there.

## Code explanations
- **Install/import:** installs the Gemini package and imports tools for API access, tables, text cleanup, and plotting.
- **API setup:** reads the API key privately, configures Gemini, and selects the model named in the assignment handout.
- **Load CSV:** uploads and reads the dataset into a pandas DataFrame.
- **Analysis prompt:** sends the CSV string to Gemini and prints its written analysis.
- **Prediction prompt:** asks Gemini for one predicted target value per row in CSV format.
- **Parse response:** removes optional Markdown fences and converts the CSV text into a DataFrame.
- **Merge and compare:** joins predictions to the original rows using the identifier and calculates absolute errors.
- **Plot:** draws actual and predicted values so their differences can be inspected.
- **Save results:** exports the combined results to a CSV file.

## Task 2 written explanation (adapt after running)
Task 2 repeats the same workflow with the used-car dataset. The identifier is `car_id`; the features are year, mileage, engine size, and horsepower; and the target is `price_usd`. Gemini first describes patterns in the dataset and then predicts the price for each car. The notebook parses the response, joins it to the original data, calculates absolute errors, and graphs actual versus predicted prices.

## Prompts documented
1. **Analysis:** “Analyze the following dataset in CSV format. Explain the main trends, important metrics, relationships between columns, and any unusual observations. Use specific examples from the data. Do not claim that correlation proves causation. State that the dataset is synthetic.”
2. **Prediction:** “Predict the target value for every row using the other available columns. Do not use the actual target as an input. Keep each row matched to its identifier. Return only valid CSV data with the identifier and predicted target columns.”

## GitHub submission checklist
- [ ] Confirm whether the instructor requires the original finance CSV and the exact Assignment 2 dataset.
- [ ] Run both notebooks in Colab with your own Gemini API key.
- [ ] Save the completed notebooks with actual Gemini output and graphs.
- [ ] Check that no API key appears in any notebook output or code.
- [ ] Upload the notebooks, CSV datasets, and this README to your GitHub repository.
- [ ] Copy the GitHub repository URL into the assignment submission.
