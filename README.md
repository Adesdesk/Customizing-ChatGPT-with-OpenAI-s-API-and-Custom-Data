# Customizing-ChatGPT-with-OpenAI-s-API-and-Custom Data
##### Customizing a Chatbot with OpenAI’s API and Custom Data to include knowledge about custom text a user provides.
###### (OpenAI API key removed from the workbook against vulnerabilities).

With the awareness that chatGPT's knowledge is generally limited to happenings prior to September 2021, I attempted to ask it a question about a more recent development than it knows and as expected, it responded that it has no knowledge of that information. (Screenshot as follows).

![Info_out_of_GPT_knowledge](https://github.com/Adesdesk/Customizing-ChatGPT-with-OpenAI-s-API-and-Star-Trek-Data/assets/101281102/45d5c78d-bd41-43f5-80ed-69c71230ad65)

Then I took a text file containing an article authored by Vusi Thembekwayo, rendered the text in JSON format and saved in a JSON file. This file was uploaded to the file base of this jupyter notebook with code written to read the file content. The program first breaks that text up into chunks containing 600 words (technically called “tokens”), where each chunk overlaps 20 words with the following chunk. It then sends the chunks to OpenAI to obtain their embeddings. 

A question is asked about the text, and the question’s embedding is found. The cosine similarity is used to find the chunk of text that is closest to that question.
A query is then sent to ChatGPT that includes the original question, as well as the chunk of text as context.

A loop is ran over all the chunks, and each one is sent to OpenAI to get back the embedding, and then write a new line to the Dataframe df.

As expected at the end of the whole process, the chatbot was able to correctly answer my query, which ChatGPT on its own couldn't do. (Screenshot as follows.

![Info_successfully_fed_to_GPT](https://github.com/Adesdesk/Customizing-ChatGPT-with-OpenAI-s-API-and-Star-Trek-Data/assets/101281102/418cfe80-6410-4ba4-831f-5a8009874f86)
