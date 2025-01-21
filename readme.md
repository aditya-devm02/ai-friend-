<!-- PROJECT LOGO -->

<div align="center">
    <h1 style="font-weight: 900" align="center">Jim the AI Friend</h3>
    <img src="/assets/readme-header.png" alt="Logo" width="100%">
</div>

---


---

# Running the Application

## To Run Frontend

1. Go into 'frontend/' folder.

   ```sh
   cd frontend/
   ```

2. Make Sure you have <a href="https://nodejs.org/en/" target="_blank">Node.js</a> installed
3. Install NPM Packages
   ```sh
   npm i
   ```
4. To run the project, run:
   ```sh
   npm start
   ```
5. To view the project in the browser, go the the link: 'http://127.0.0.1:3000/' or 'http://localhost:3000/'

## To Run Backend

1. Make Sure you have <a href="https://www.python.org/downloads/" target="_blank">Python</a> installed
2. Created the Python environment by running

   ```sh
   python -m venv venv

   # or

   python3 -m venv venv
   ```

3. Enter the Python environment by running

   - On Windows:

     ```sh
     venv\Scripts\activate.bat
     ```

   - Mac or Linux
     ```sh
     . venv/bin/activate
     ```

4. Install all the pip packages by running
   ```sh
   python -m pip install -r backend/requirements.txt
   ```
5. Now, with our py environment setup, we can go to the backend folder:
   ```sh
    cd backend/
   ```
6. To run the FastAPI Backend Server, run:

   ```sh
     uvicorn app.main:app --reload
   ```

   Uvicorn is a package that runs a python ASGI web server. In other words, its running our python code through the file system. Once the ML Algo is deployed, it will be within this web server instance that it is exposed.

## To Run the Docker File

There are two separate docker files in both the '/backend' folder as well as the '/frontend', and a docker-compose that will combine those to images. A well-needed CaddyFile is used to deploy the frontend and backend way such that the frontend runs on, for example, 'http://localhost:8080', and the backend is served at the '/api' route, or 'http://localhost:8080/api'. I did this to be able to host both the frontend and backend on the same server, as well as to minify the time it takes to get an ML algo response.

To build the docker images, you can run:

```sh
docker-compose build --no-cache
```

To run this build locally, you can do:

```sh
docker-compose up

# or if you don't want to do docker-compose:

docker run  uvicorn app.main:app --root-path /api --proxy-headers --host 0.0.0.0 --port 8000
docker run -v ./Caddyfile:/etc/caddy/Caddyfile -v caddy-data:/data -v caddy-config:/config -p 8080:80
```


Here are some examples of output from the model:
<img src="/assets/output1.png" alt="Logo" width="100%">
<img src="/assets/output2.png" alt="Logo" width="100%">

# **Discussion**

Both the LSTM and attention models performed comparably well, with the LSTM model excelling in capturing long-term dependencies and context, while the attention model effectively highlighted important words and phrases for better understandability. Our MLP and RNN models performed well in text classification whereas the LSTM and Attention models were better at text generation. The LSTM model's ability to capture long-term dependencies and context makes it highly impressive. By stacking more LSTM layers and units and implementing dropout, we significantly improved the performance of the model. Exploring transformer-based models like GPT-3 or BERT, and fine-tuning them with domain-specific data, could enhance their accuracy and coherence in providing emotional support. While the MLP model didn't perform as well as LSTM, it excelled in being concise and grammatically accurate. Involving human experts to review and provide feedback on the chatbot's responses ensures high-quality and safe outputs. Safeguarding user information and addressing biases in the training data are crucial challenges in taking the model to the next level. Incorporating attention mechanisms and providing explanations for the model's reasoning can enhance its understandability and build trust among users.

# **References**

1. Mondal, A. (2023, April 20). _Complete guide to build your AI chatbot with NLP in python_. Analytics Vidhya. Retrieved April 28, 2023, from[https://www.analyticsvidhya.com/blog/2021/10/complete-guide-to-build-your-ai-chatbot-with-nlp-in-python/](https://www.analyticsvidhya.com/blog/2021/10/complete-guide-to-build-your-ai-chatbot-with-nlp-in-python/)
2. Viraj, A. (2020, October 31). _How to build your own chatbot using Deep Learning_. Medium. Retrieved April 28, 2023, from[https://towardsdatascience.com/how-to-build-your-own-chatbot-using-deep-learning-bb41f970e281](https://towardsdatascience.com/how-to-build-your-own-chatbot-using-deep-learning-bb41f970e281)
3. YouTube. (2020, June 11). _Chat bot with Pytorch - NLP and Deep Learning - Python Tutorial (Part 4)_. YouTube. Retrieved April 28, 2023, from[https://www.youtube.com/watch?v=k1SzvvFtl4w](https://www.youtube.com/watch?v=k1SzvvFtl4w)
4. Kaggle. _Counsel Chat Dataset_. Kaggle. Retrieved May 2nd, 2023, from [https://www.kaggle.com/datasets/ssp1411/counsel-chat](https://www.kaggle.com/datasets/ssp1411/counsel-chat).
