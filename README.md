# eksisozluk-realtime-processing
## Real-Time Analysis of Trending Topics

This project performs real-time analysis on trending topics from Ekşi Sözlük, processes the data, and visualizes insights. The pipeline includes data crawling, real-time database querying, statistical analysis, and visualization.

## Features
- **Data Crawling**: Uses Selenium to scrape trending topics and their corresponding entries from Ekşi Sözlük.
- **Real-Time Database Querying**: Queries data stored in AWS Athena using PyAthena.
- **Statistical Analysis**:
  - Topic frequency (number of entries per topic).
  - Text length statistics (mean, min, max).
  - Sentiment analysis (average polarity of text).
  - Keyword frequency (most common words).
- **Change Detection**: Saves analysis to a file and checks for updates before creating new files.
- **Data Visualization**: Generates clear and interpretable bar plots for all analyses.

## Technologies Used
- **Python Libraries**:
  - `kafka-python`: Kafka framework.
  - `Selenium`: Web scraping.
  - `PyAthena`: Athena database queries.
  - `TextBlob`: Sentiment analysis.
  - `Matplotlib`: Data visualization.
- **AWS Services**:
  - Athena: Real-time querying.
  - S3: Storing intermediate data.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/mouneszawal/eksisozluk-realtime-processing.git
   cd eksisozluk-realtime-processing
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Ensure you have:
   - AWS credentials set up (`~/.aws/credentials` or environment variables).
   - ChromeDriver installed and compatible with your Chrome browser.

## Output
- **Analysis Files**:
  - Stored in the `analysis_files` directory.
  - Example: `analysis_<hash>.json`.
- **Visualizations**:
  - Topic frequency bar chart.
  - Text length statistics (mean, min, max).
  - Sentiment analysis (average polarity).
  - Most common words.

## How It Works
1. **Data Crawling**:
   - Scrapes the top 10 trending topics and their entries from Ekşi Sözlük.
2. **Database Querying**:
   - Queries AWS Athena for the latest data.
3. **Statistical Analysis**:
   - Computes topic frequency, text length stats, sentiment analysis, and common keywords.
4. **Change Detection**:
   - Compares current analysis with the last saved file.
   - Saves new analysis only if there are updates.
5. **Visualization**:
   - Automatically generates and displays plots.

## Example Visualizations
- **Topic Frequency**: Horizontal bar chart showing the number of entries per topic.
- **Text Length Statistics**: Grouped bar chart for mean, min, and max text lengths per topic.
- **Sentiment Analysis**: Bar chart showing average sentiment polarity per topic.
- **Most Common Words**: Bar chart for the top 10 words.

## Configuration
- Modify `main.py` to adjust:
  - **Crawling Frequency**: Change `sleep(60)` in the main loop to adjust how often data is fetched.
  - **Number of Topics**: Update `top_n` in the `crawl_topics()` function.

## Dependencies
Install the following Python libraries:
- `kafka-python`
- `pandas`
- `selenium`
- `pyathena`
- `textblob`
- `matplotlib`

## Future Improvements
- Add live dashboards for continuous monitoring.
- Implement advanced NLP techniques (e.g., topic modeling).
- Extend to support multiple languages.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

