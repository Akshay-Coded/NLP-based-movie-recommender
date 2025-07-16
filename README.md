# Movie Recommendation System

## Overview

This project is a **Movie Recommendation System** built using Natural Language Processing (NLP) techniques and machine learning. It recommends movies based on their similarity to a user-selected movie, leveraging data from the TMDB 5000 Movie Dataset. The system processes movie metadata such as genres, keywords, cast, crew, and overviews to generate personalized recommendations.

The application is deployed using **Streamlit** and can be accessed here.
Check out my Movie Recommendation System: [Live Demo](https://movie-recommendation-nlp.streamlit.app/) | [GitHub Repo](https://github.com/your-username/movie-recommendation-system)

## Features

- **Content-Based Filtering**: Recommends movies based on similarity scores computed using movie metadata.
- **NLP Processing**: Utilizes text preprocessing techniques like tokenization, stemming, and vectorization to process movie descriptions.
- **Cosine Similarity**: Employs cosine similarity to measure the similarity between movies based on their combined tags (overview, genres, keywords, cast, and crew).
- **Interactive UI**: Built with Streamlit for an intuitive and user-friendly interface.
- **Data Persistence**: Uses pickle files to store the processed movie data and similarity matrix for efficient recommendations.

## Technologies Used

- **Python**: Core programming language.
- **Pandas**: For data manipulation and analysis.
- **NLTK**: For text preprocessing (stemming).
- **Scikit-learn**: For vectorization (CountVectorizer) and similarity computation (cosine similarity).
- **Streamlit**: For deploying the web application.
- **Pickle**: For serializing and saving the processed data and similarity matrix.

## Dataset

The project uses the **TMDB 5000 Movie Dataset** from Kaggle, which includes:

- **Movies Data**: Contains details like movie title, genres, keywords, overview, budget, revenue, etc.
- **Credits Data**: Includes cast and crew information for each movie.

The datasets are merged and preprocessed to create a consolidated dataset with relevant features for recommendation.

## How It Works

1. **Data Preprocessing**:
   - Merges the movies and credits datasets on the `title` column.
   - Selects relevant columns: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, and `crew`.
   - Processes text data by:
     - Splitting the overview into words.
     - Removing spaces from genres, keywords, cast, and crew to avoid ambiguity in the ML model.
     - Combining all features into a single `tags` column.
     - Applying stemming to normalize words (e.g., "running" → "run").
     - Converting tags to lowercase for consistency.
2. **Feature Extraction**:
   - Uses `CountVectorizer` to convert the `tags` column into a numerical vector representation (max 5000 features, excluding English stop words).
3. **Similarity Calculation**:
   - Computes a cosine similarity matrix for all movies based on their vectorized tags.
4. **Recommendation**:
   - Given a movie title, the system finds its index, retrieves similarity scores, and returns the top 5 most similar movies.
5. **Deployment**:
   - The processed data and similarity matrix are saved as pickle files for quick loading.
   - The Streamlit app allows users to select a movie and view recommendations interactively.

## Installation

To run this project locally, follow these steps:

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-username/movie-recommendation-system.git
   cd movie-recommendation-system
   ```

2. **Install Dependencies**: Ensure you have Python 3.11+ installed. Then, install the required packages:

   ```bash
   pip install -r requirements.txt
   ```

3. **Download the Dataset**:

   - Download the TMDB 5000 Movie Dataset from Kaggle.
   - Place the `tmdb_5000_movies.csv` and `tmdb_5000_credits.csv` files in a `Data` folder in the project directory.

4. **Run the Jupyter Notebook**:

   - Open the `Movie-recommender.ipynb` notebook to preprocess the data and generate the pickle files (`movie_list.pkl` and `similarity.pkl`).
   - Alternatively, use pre-generated pickle files if available.

5. **Run the Streamlit App**:

   ```bash
   streamlit run app.py
   ```

   Replace `app.py` with the name of your Streamlit application file if different.

## File Structure

- `Movie-recommender.ipynb`: Jupyter Notebook containing the data preprocessing and model-building code.
- `Data/`: Directory containing the TMDB dataset (`tmdb_5000_movies.csv` and `tmdb_5000_credits.csv`).
- `artifacts/`: Directory containing the pickle files (`movie_list.pkl` and `similarity.pkl`).
- `app.py`: Streamlit application script for the web interface.
- `requirements.txt`: List of required Python packages.
- `README.md`: This file.

## Usage

1. Access the deployed app here.
2. Select a movie from the dropdown menu.
3. View the top 5 recommended movies based on content similarity.

Alternatively, run the app locally:

- Execute the Jupyter Notebook to preprocess the data and generate pickle files.
- Run the Streamlit app to interact with the recommendation system.

## Example Recommendations

For the movie **Avatar**, the system recommends:

- Aliens vs Predator: Requiem
- Aliens
- Falcon Rising
- Independence Day
- Titan A.E.

For the movie **Hulk**, the system recommends:

- Transformers: Age of Extinction
- Godzilla 2000
- The Incredible Hulk
- Super
- The Island of Dr. Moreau

## Future Improvements

- **Enhanced Features**: Incorporate additional features like user ratings or popularity scores to improve recommendation quality.
- **Collaborative Filtering**: Combine content-based filtering with collaborative filtering for hybrid recommendations.

**Improved UI**: Enhance the Streamlit interface with movie posters and additional metadata.

- **Advanced NLP**: Use more sophisticated NLP techniques like TF-IDF or word embeddings (e.g., Word2Vec, BERT) for better text representation.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue for suggestions, bug reports, or improvements.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

For any inquiries or feedback, please reach out via GitHub Issues.

---

*Built with ❤️ for movie enthusiasts and data science recruiters!*
