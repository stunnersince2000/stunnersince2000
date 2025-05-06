- 👋 Hi, I’m @stunnersince2000
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

from transformers import pipeline
import ipywidgets as widgets
from IPython.display import display

generator = pipeline("text-generation", model="gpt2")

input_box = widgets.Text(
    value='Hello!',
    placeholder='Type your message here',
    description='You:',
    disabled=False
)

output_box = widgets.Output()

def on_submit(change):
    user_input = change['new']
    response = generator(user_input, max_length=100, num_return_sequences=1)[0]['generated_text']
    with output_box:
        print(f"You: {user_input}")
        print(f"Bot: {response}\n")

input_box.observe(on_submit, names='value')
display(input_box, output_box)
<!---
stunnersince2000/stunnersince2000 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
