# Mysterious learnings

In this case we have a .h5 file, which is the file format used in Tensorflow to save and load keras models. With a bit of research, we can discover some of the main commands used to carve out information about the model:

- `model.summary`
- `model.getConfig()`

We can then retrieve the three base64 encoded pieces of our flag by running the following script using, for example, a Google Colab Notebook:

```python
from tensorflow import keras

model = keras.models.load_model("alien.h5")
 
print(model.summary)
print(model.getConfig())
```

The final string put together is: SFRCe24wdF9zb19oNHJkX3RvX3VuZDNyc3Q0bmR9

## HTB{n0t_so_h4rd_to_und3rst4nd}
