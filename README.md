
# LangChain and Streamlit RAG


## Quickstart

### Setup Python environment

The Python version used when this was developed was 3.10.13


```bash
python -mvenv .venv
source .venv/bin/activate
pip install -U pip
pip install -r requirements.txt
```

If you run into issues related to hnswlib or chroma-hnswlib while installing requirements you may need to install system package for the underlying package.

For example, on Ubuntu 22.04 this was needed before pip install of hnswlib would succeed.

```bash
sudo apt install python3-hnswlib
```

### Setup .env file with API tokens needed.

```
OPENAI_API_KEY="<Put your token here>"
HUGGINGFACEHUB_API_TOKEN="<Put your token here>"
```

### Setup Streamlit app secrets.

#### 1. Set up the .streamlit directory and secrets file.

```bash
mkdir .streamlit
touch .streamlit/secrets.toml
chmod 0600 .streamlit/secrets.toml
```

#### 2. Edit secrets.toml

**Either edit `secrets.toml` in you favorite editor.**

```toml
OPENAI_API_KEY="<Put your token here>"
HUGGINGFACEHUB_API_TOKEN="<Put your token here>"
```

**Or, you can just reuse .env contents from above.**

```bash
cat < .env >> .streamlit/secrets.toml
```

### Verify Environment

1. Check that LangChain dependencies are working.

```bash
python basic_chain.py
```

2. Check that Streamlit and dependencies are working.

```bash
streamlit run streamlit_app.py
```

3. Run Individual Example Programs

The most of the Python source files besides `streamlit_app.py` have a main defined
so that you can execute them directly as an example or test.

For example, the main in `ensemble.py` will use context from an online version of the book [*The Problems of Philosophy* by Bertrand Russell](https://www.gutenberg.org/ebooks/5827.html.images)
to answer "What are the key problems of philosophy according to Russell?"

```bash
python ensemble.py
```

>    Split into 313 chunks
>    According to Russell, the key problems of philosophy include the uncertainty of knowledge, the limitations of metaphysical reasoning, and the inability to provide definite answers to fundamental questions. Philosophy aims to diminish the risk of error, but cannot eliminate it entirely due to human fallibility. The value of philosophy lies in its ability to challenge common sense beliefs and lead to the exploration of complex problems.



## Example Queries for Streamlit App

### Example 1: Metabolic Rate

**Question:**
If I am an 195 lb male, what should my calorie intake be to lose 1 lb a week based on what you know about my basal metabolic rate?

**Answer:**
To calculate the calorie intake for a 195 lb male to lose 1 lb per week based on their basal metabolic rate, we can use the estimated BMR values provided in the context.

For a 190 lb male, the estimated BMR is around 2,280 calories per day. To lose 1 lb per week, a general rule of thumb is to create a calorie deficit of about 500 calories per day.

Therefore, to lose 1 lb per week, a 195 lb male should aim to consume around 1,780 calories per day (2,280 calories - 500 calories). This calorie intake, combined with regular physical activity, can help achieve a sustainable weight loss goal.

### Example 2: Recipes

NOTE: to use this example, copy the `example/us_army_recipes.txt` file into the `data` directory. It is left out by default because it significantly increases the resources used over the other examples.

**Question:**
How do I make salmon croquettes according to the recipes I provided you?

**Answer:**
To make salmon croquettes based on the recipes shared, you can follow these steps:

Ingredients:

- 4 cans of salmon
- 4 pounds of cold boiled potatoes
- 2 eggs
- Salt and pepper to taste
- Cracker dust for coating
- Oil for frying

Instructions:

1. Drain the canned salmon and remove any bones or skin.
2. In a large bowl, mash the salmon and boiled potatoes together.
3. Add the eggs, salt, and pepper to the mixture and combine well.
4. Shape the mixture into small cakes about 2 inches in diameter.
5. In a separate bowl, beat the remaining eggs with a little milk to create an egg batter.
6. Dip each salmon cake into the egg batter, then coat it with cracker dust.
7. Heat oil in a pan for frying.
8. Fry the salmon croquettes in the hot oil until they are golden brown on all sides.
9. Once cooked, remove them from the oil and place them on a paper towel to drain any excess oil.
10. Serve the salmon croquettes hot and enjoy!

I hope these instructions help you make delicious salmon croquettes! Let me know if you need any more assistance.



