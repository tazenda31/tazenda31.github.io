# Basic psycholinguistic measures: Type-token frequency
The analysed text was published on Daily Echo website on 27/01/2024.
https://www.dailyecho.co.uk/news/24076400.winchester-armed-police-confront-men-dressed-cowboys-filming-video/

```python

import spacy

text = """Two men dressed as cowboys were confronted by armed police in Winchester city centre for having guns, 
before finding out they were props for a music video. Photos show police with guns surrounding two men 
in Stockbridge Road near the railway station on Wednesday, January 24. An eyewitness told the Chronicle 
they were filming a music video which got out of hand. One of the men, Sol Milson, said in a Facebook comment: 
“We were shooting a music video and someone reported the car for having guns in the back. We got guns 
put to our faces carted off in a police car and taken to Basingstoke police station. They soon realised 
the guns are props. On a plus side music video coming out February 1." Eyewitness Jenny Penfold was in Cafe Røst 
when armed police swarmed the area. She said: “We did see them being put in a police car, yes it was mental. 
“Basically what happened was, I was in Røst, about to leave. Got yelled at by armed police to go back inside. 
Whole load of them swarmed the two cowboys and they put their hands on their heads and had to 
get out from where they were (I think in their car). Police had their guns aimed at them. 
Then they got put in the police vehicle and I went back to work.
“In regards to it being a hoax however one of the cowboys messaged me on Instagram telling me what happened 
and he said they got taken to Basingstoke police station and they were trying to film a music video and it got out of hand!”
Hampshire Constabulary has been contacted for more information."""

def tokenise_and_clean(text):
    # Load the English language model in spaCy
    nlp = spacy.load("en_core_web_sm")
    
    # Process the input text using spaCy
    doc = nlp(text)
    
    # List to store cleaned tokens
    tokens = []
    
    # Iterate over tokens in the processed text
    for token in doc:
        # Check if the token is a punctuation or a space character
        if not token.is_punct and not token.is_space:
            # Convert token to lowercase and append to cleaned_tokens list
            tokens.append(token.text.lower())
    
    return tokens

tokens = tokenise_and_clean(text)
print(tokens)
```
['two', 'men', 'dressed', 'as', 'cowboys', 'were', 'confronted', 'by', 'armed', 'police', 'in', 'winchester', 'city', 'centre', 'for', 'having', 'guns', 'before', 'finding', 'out', 'they', 'were', 'props', 'for', 'a', 'music', 'video', 'photos', 'show', 'police', 'with', 'guns', 'surrounding', 'two', 'men', 'in', 'stockbridge', 'road', 'near', 'the', 'railway', 'station', 'on', 'wednesday', 'january', '24', 'an', 'eyewitness', 'told', 'the', 'chronicle', 'they', 'were', 'filming', 'a', 'music', 'video', 'which', 'got', 'out', 'of', 'hand', 'one', 'of', 'the', 'men', 'sol', 'milson', 'said', 'in', 'a', 'facebook', 'comment', 'we', 'were', 'shooting', 'a', 'music', 'video', 'and', 'someone', 'reported', 'the', 'car', 'for', 'having', 'guns', 'in', 'the', 'back', 'we', 'got', 'guns', 'put', 'to', 'our', 'faces', 'carted', 'off', 'in', 'a', 'police', 'car', 'and', 'taken', 'to', 'basingstoke', 'police', 'station', 'they', 'soon', 'realised', 'the', 'guns', 'are', 'props', 'on', 'a', 'plus', 'side', 'music', 'video', 'coming', 'out', 'february', '1', 'eyewitness', 'jenny', 'penfold', 'was', 'in', 'cafe', 'røst', 'when', 'armed', 'police', 'swarmed', 'the', 'area', 'she', 'said', 'we', 'did', 'see', 'them', 'being', 'put', 'in', 'a', 'police', 'car', 'yes', 'it', 'was', 'mental', 'basically', 'what', 'happened', 'was', 'i', 'was', 'in', 'røst', 'about', 'to', 'leave', 'got', 'yelled', 'at', 'by', 'armed', 'police', 'to', 'go', 'back', 'inside', 'whole', 'load', 'of', 'them', 'swarmed', 'the', 'two', 'cowboys', 'and', 'they', 'put', 'their', 'hands', 'on', 'their', 'heads', 'and', 'had', 'to', 'get', 'out', 'from', 'where', 'they', 'were', 'i', 'think', 'in', 'their', 'car', 'police', 'had', 'their', 'guns', 'aimed', 'at', 'them', 'then', 'they', 'got', 'put', 'in', 'the', 'police', 'vehicle', 'and', 'i', 'went', 'back', 'to', 'work', 'in', 'regards', 'to', 'it', 'being', 'a', 'hoax', 'however', 'one', 'of', 'the', 'cowboys', 'messaged', 'me', 'on', 'instagram', 'telling', 'me', 'what', 'happened', 'and', 'he', 'said', 'they', 'got', 'taken', 'to', 'basingstoke', 'police', 'station', 'and', 'they', 'were', 'trying', 'to', 'film', 'a', 'music', 'video', 'and', 'it', 'got', 'out', 'of', 'hand', 'hampshire', 'constabulary', 'has', 'been', 'contacted', 'for', 'more', 'information']

```python
# Count the total number of tokens (words)
count_tokens = len(tokens)

# Create a set of unique words and count them
types = set(tokens)
count_types = len(types)

# Calculate the type/token ratio
type_token_ratio = count_types / count_tokens

# Print the results
print(f"Total types in the text: {count_types}")
print(f"Total tokens in the text: {count_tokens}")
print(f"Type/Token Ratio: {type_token_ratio:.2f}")
```
Result: 
Total types in the text: 135
Total tokens in the text: 280
Type/Token Ratio: 0.48