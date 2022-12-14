In this project i have built a **Covid19 Dashboard** by applying the concepts i have learned till now. I have developed an app that will fetch data from an internal server using a **class component**, displaying that data, using **component lifecycle** methods, **routing** concepts and adding responsiveness to the website.


### Complete Details

<details>
<summary>Functionality that is added</summary>

The app will have the following functionalities

- Users will be able to navigate to Home, About routes using links in Navbar
- The website will be responsive in mobile view, tablet view as well (Use Media Queries to achieve the responsive website)

- **Home Route**

  - An HTTP GET request should be made to the Home Route API URL
    - **_Loader_** should be displayed while fetching the data
    - After the data is fetched successfully,
      - Stats of **Confirmed**, **Active**, **Recovered**, **Deceased** cases of **India** should be equal to the respective data received from the response
      - List of State/UT should be displayed with corresponding **Confirmed**, **Active**, **Recovered**, **Deceased** cases count
      - When the **Ascending Icon** (**FcGenericSortingAsc** react-icon) is clicked, then the list of State/UT should be sorted with **Ascending Order** based on State/UT name
      - When the **Descending Icon** (**FcGenericSortingDesc** react-icon) is clicked, then the list of State/UT should be sorted with **Descending Order** based on State/UT name
  - Footer should be displayed as shown in the Figma

- **Search Functionality**

  - Search should be case **insensitive**. This means Searching for `AN` or `an` or `An` should give the same search results
  - When the State/UT is searched by using the State/UT name, then the list of State/UT names matched with the search text should be displayed
  - When the Specific State/UT is clicked in the searched State/UT, then the page should be navigated to the Specific State/UT

- **State-Specific Route**

  - An HTTP GET request should be made to the State-Specific Route API URL
    - **_Loader_** should be displayed while fetching the data
    - After the data is fetched successfully,
      - State name and last updated date should be equal to the State name received from the response
      - Stats of **Confirmed**, **Active**, **Recovered**, **Deceased** cases of specific state should be equal to the respective data received from the response
      - Tested count should be equal to the tested count received from the response
      - Initially districts with Descending order of their **Confirmed Cases** should be displayed in the Top Districts
      - When the **Active Cases** card is clicked, then the Top Districts and **Bar Graph** should be changed to **Descending order** by their **Active Cases** count
      - When the **Confirmed Cases** card is clicked, then the Top Districts and **Bar Graph** should be changed to **Descending order** by their **Confirmed Cases** count
      - When the **Recovered Cases** card is clicked, then the Top Districts and **Bar Graph** should be changed to **Descending order** by their **Recovered Cases** count
      - When the **Deceased Cases** card is clicked, then the Top Districts and **Bar Graph** should be changed to **Descending order** by their **Deceased Cases** count
      - **Bar Graph** should be displayed with the last 10 days of Covid19 cases data
      - Initially for Spread Trends, **Daily Data** should be displayed
    - Footer should be displayed as shown in the Figma

- **Not Found Route**

  - When a random path is provided in the URL, then the page should be navigated to the Not Found Route

- **About Route**

  - An HTTP GET request should be made to the About Route API URL
    - **_Loader_** should be displayed while fetching the data
    - After the data is fetched successfully, the response received should be displayed
    - List of **faqs** should be displayed
    - Footer should be displayed as shown in the Figma

- **Header**

  - When the **COVID19INDIA** heading element in the Header is clicked, then the page should be navigated to the Home Route
  - When the **Home** link in the Header is clicked, then the page should be navigated to the Home Route
  - When the **About** link in the Header is clicked, then the page should be navigated to the My About Route

</details>

### Resources

<details>
<summary>Data fetch URLs</summary>

- Home Route:

  - Get stats of confirmed, active, recovered, deceased cases state wise (<u>sum of state wise data will give you national wise data</u>) :

    ```js
    'https://apis.ccbp.in/covid19-state-wise-data'

    ```

- State-Specific Route:

  - Get tested count, last updated date and stats of confirmed, active,recovered, deceased cases in specific states:

    ```js
    'https://apis.ccbp.in/covid19-state-wise-data'
    //(the response contains stats of all the States, you can use a state code (Ex:- "AP") to get specific state stats.)

    ```

  - Get districts (sort to show Top Districts):

    ```js
    'https://apis.ccbp.in/covid19-state-wise-data'
    //(the response contains stats of all the States, you can use a state code (Ex:- "AP") to get specific state stats.)

    ```

  - Sample Response for the API Url `https://apis.ccbp.in/covid19-state-wise-data`:

    ```json
    {
    "AP":{
      "districts":{
         "Anantapur":{
            "total":{
               "confirmed":157823,
               "deceased":1093,
               "recovered":156679,
               "tested":787085,
               "vaccinated1":2659813,
               "vaccinated2":1556657
            }
         }
      },
      "meta":{
         "date":"2021-10-28",
         "last_updated":"2021-10-28T20:20:18+05:30",
         "population":397000,
         "tested":{
            "date":"2021-10-27",
            "source":"https://dhs.andaman.gov.in/NewEvents/847.pdf"
         }
      },
      "total":{
         "confirmed":7651,
         "deceased":129,
         "recovered":7516,
         "tested":592748,
         "vaccinated1":293644,
         "vaccinated2":195689
      }
    }
      {...}
     }
    ```

  - Get timelines to show spread trends (use timelines data for rendering Bar chart, Line chart and other recharts by date-wise):

    ```js
    'https://apis.ccbp.in/covid19-timelines-data/AP'
    //(change state code in URL for other states)

    //(or)

    'https://apis.ccbp.in/covid19-timelines-data'
    //(the response contains stats of all the States, you can use a state code (Ex:- "AP") to get specific state stats.)

    ```

  - Sample Response

    ```json
    {
      "AN": {
        "dates": {
          "2021-09-09": {
            "total": {
              "confirmed": 7577,
              "deceased": 129,
              "recovered": 7441,
              "tested": 508157,
              "vaccinated1": 267126,
              "vaccinated2": 112124
            }
          },
          "2021-09-09": {...}
        }
      }
    }
    ```

- About Route:

  - Get faqs:

    ```js
    'https://apis.ccbp.in/covid19-faqs'

    ```

  - Sample Response

    ```json
    {
      "faq": [
        {
          "answer": "No.",
          "category": "General",
          "qno": "1",
          "question": "Are you official?"
        }
      ]
    }
    ```

    </details>

### Stretch Goals

These are the additional features that can be added.

<details>
<summary>Additional Functionality that can be added</summary>

- Users should be able to see Themes (Light & Dark) in Navbar
- **State-Specific Route**

  - India Map with Specific State should be highlighted

- **Vaccination Details Route**

  - An HTTP GET request should be made to the **Vaccination Details API URL**
    - **_Loader_** should be displayed while fetching the data
    - After the data is fetched successfully, the response received should be displayed
      - Page should contain the dropdowns to select state and district
      - Page should contain the sites Conducting Vaccination, total Registrations, Total Vaccination Doses sections
      - Page should contain the Vaccination Trends for both by **Doses** and **Ages** section

- **Data Fetch URLs**

  - **Vaccination Details Route:**

    - Get states data:

      ```js
      'https://apis.ccbp.in/covid19-state-ids'

      ```

    - Get Districts data (state specific):

      ```js
      'https://apis.ccbp.in/covid19-districts-data/2'
      //(change state id in URL)

      ```

    - Get sites conducting vaccination, total registrations, total vaccination, vaccination trends, vaccination - category, vaccination by age Details:

      ```js
      'https://apis.ccbp.in/covid19-vaccination-data'
      //(change date in URL)

      ```

</details>
