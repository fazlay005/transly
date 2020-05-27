[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
![versions](https://img.shields.io/badge/python-3.above-blue.svg)

## Transly

Transly is a Python library for dealing with transliteration. It currently supports Hindi to English and English to Hindi transliteration.
All the pre-trained models can be found inside trained_models folder. New models can also be trained on custom data.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install transly.

.. code-block:: sh

    pip install transly


## Usage

### Hindi to English
Using the pre-trained model

.. code-block:: python

    import transly as tl

    QUERY = 'नहीं'
    a = tl.load_model(model_path='hi2en')
    a.infer(QUERY)


### English to Hindi
Using the pre-trained model

.. code-block:: python

    import transly as tl

    QUERY = 'NAHI'
    a = tl.load_model(model_path='en2hi')
    a.infer(QUERY)


Training a new model on custom data
Training data file should be a csv with two columns, the input and the output

.. code-block:: python

    from transly.seq2seq.config import SConfig
    from transly.seq2seq.version0 import Seq2Seq

    config = SConfig(training_data_path=training_data_path)
    s2s = Seq2Seq(config)
    s2s.fit()
    s2s.save_model(path_to_model=model_path, model_file_name=model_file_name)
