# AI101 Assignment 4 — GitHub Project

## Contents
- `notebooks/Assignment4_Task1_Financial_Data.ipynb` — Task 1: Gemini analysis and stock-price predictions.
- `notebooks/Assignment4a_Task2_Used_Cars.ipynb` — Task 2: same workflow using a different dataset.
- `data/finance_data.csv` — synthetic financial practice dataset.
- `data/used_car_prices.csv` — synthetic used-car practice dataset.

## Model update\nThe assignment handout specifies `gemini-2.0-flash-lite`, which Google shut down on June 1, 2026. These notebooks use the supported `gemini-3.5-flash-lite` model and the current `google-genai` Python SDK so the workflow can run today.\n\n## Important dataset note
Both CSV files in this project are **synthetic datasets generated for this assignment practice**. They are not real stock-market or used-car observations. If your instructor requires the original `finance_data.csv` or the dataset you used in Assignment 2, replace the matching CSV with that required file before submitting.

## How to run in Google Colab
1. Download this repository as a ZIP and extract it.
2. Open each `.ipynb` file in Google Colab.
3. Upload the matching CSV from the `data` folder when the notebook asks for it.
4. Run the cells from top to bottom.
5. Add your own `GEMINI_API_KEY` in Colab's Secrets panel, or enter it in the notebook's hidden prompt when asked. Do not paste your API key into a notebook cell or commit it to GitHub.
6. Save the notebook after it runs. Keep the output cells, including the Gemini analysis and graph, for your submission.

## Task 1 written explanation (adapt after running)
The prediction output is Gemini's estimate of the stock price for each company row. The actual and predicted columns can be compared to see how close the estimates are. The mean absolute error reports the average size of the prediction error in the same units as the stock price. Because Gemini is a language model responding to a prompt, its predictions may vary and should not be treated as verified financial forecasts.

This approach differs from simply asking an AI assistant to write code: in this assignment, the CSV data itself is included in a prompt sent directly to the Gemini model, and Gemini is asked to analyze the data and produce predictions. The Python notebook then converts the text response into a DataFrame and plots the results. The supplied written answers compare the prompt-based workflow with the earlier use of AI to help write code. Adjust this comparison if your own work in Assignments 2 and 3 differed.

## Code explanations
- **Install/import:** installs the Gemini package and imports tools for API access, tables, text cleanup, and plotting.
- **API setup:** reads the API key privately, configures Gemini, and selects `gemini-3.5-flash-lite` through the current Google GenAI SDK.
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
2. **Prediction:** “Predict the target value for every row using the other available columns. Do not use the actual target as an input. Keep each row matched to its identifier. Return only valid CSV data with the row identifier and predicted target columns. In Task 1, include both `company_id` and `date` because each company appears more than once; in Task 2, `car_id` uniquely identifies a row.”

## GitHub submission checklist
- [ ] Confirm whether the instructor requires the original finance CSV and the exact Assignment 2 dataset.
- [ ] Run both notebooks in Colab with your own Gemini API key.
- [ ] Save the completed notebooks with actual Gemini output and graphs.
- [ ] Check that no API key appears in any notebook output or code.
- [ ] Upload the notebooks, CSV datasets, and this README to your GitHub repository.
- [ ] Copy the GitHub repository URL into the assignment submission.
