# Cryptocurrency Data Mining & Analysis Project

## Project Description

This project demonstrates proficiency in Python for data analysis, web scraping, and exploratory data analysis. By utilizing the CoinMarketCap API, it obtains live cryptocurrency data, automates data collection, cleans the data, and extracts market insights.

## Objective

The main objective of this project is to showcase skills in Python for data analysis by automating the retrieval of cryptocurrency data, processing it, and deriving actionable market insights.

## Features

- Automated API data retrieval and data appending to a DataFrame.
- Data normalization, addition, and editing of columns using pandas.
- Data cleaning and preprocessing.
- Identification of trends and patterns over time using Python functions.
- Efficient data management and code organization with Jupyter Notebook.
- Extraction of actionable insights into the cryptocurrency market.

## Technologies Used

- **Python**: Primary programming language.
- **Pandas**: For data manipulation and analysis.
- **CoinMarketCap API**: To fetch live cryptocurrency data.
- **Jupyter Notebook**: For code development and documentation.

## Installation

To run this project, follow these steps:

1. Clone the repository

2. Navigate to the project directory

3. Create a virtual environment
  
4. Activate the virtual environment
 
5. Install the required dependencies

## Usage

1. Obtain an API key from CoinMarketCap and run data collection script in Jupyter Notebook:
    ```bash
    from requests import Request, Session
    from requests.exceptions import ConnectionError, Timeout, TooManyRedirects
    import json

    def api_runner():
    global df  #declares df as a global variable
    url = 'https://pro-api.coinmarketcap.com/v1/cryptocurrency/listings/latest'
    parameters = {
      'start':'1',
      'limit':'15',
      'convert':'USD'
    }
    headers = {
      'Accepts': 'application/json',
      'X-CMC_PRO_API_KEY': 'your_coinmarketcap_api_key',
    }
    
    session = Session()
    session.headers.update(headers)
    
    try:
      response = session.get(url, params=parameters)
      data = json.loads(response.text)
      # print(data)
    except (ConnectionError, Timeout, TooManyRedirects) as e:
      print(e)
    ```
2. Normalize the data to have it in a table form, add a timestamp column to show the exact time each record was pulled, and add a script to append each record pulled to original table:
    ```bash
     df2 = pd.json_normalize(data['data'])
    df2['Timestamp'] = pd.to_datetime('now')
    df_append = pd.DataFrame(df2)
    df = pd.concat([df,df_append])
    ```
3. Run script to automatically pull records using the API after every specified time:
    ```bash
    import os 
    from time import time
    from time import sleep

    for i in range(333):
        api_runner()
        print('API Runner completed')
        sleep(60) #sleep for 1 minute
    exit()
    ```

4. Use Jupyter Notebook to explore the data and run the analysis:
    ```bash
    jupyter notebook
    ```

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

1. Fork the Project.
2. Create your Feature Branch.
3. Commit your Changes.
4. Push to the Branch.
5. Open a Pull Request.

## Contact Information

For any questions or suggestions, feel free to reach out to:

- Name: James Onyejekwe
- Email: jj.onyejekwe@gmail.com
- GitHub: [jamesmuse02](https://github.com/jamesmuse02)
