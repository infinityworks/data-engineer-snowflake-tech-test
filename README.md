# Snowflake Data Exercise - Starter Project

Infinity Workers supporting the session can find additional information [here](https://github.com/infinityworks/iw-tech-test-snowflake-simple-warehouse-solution).

### Prerequisites

#### Install Python 3.8.* or later.

See installation instructions at: https://www.python.org/downloads/

Check you have python3 installed:

    python3 --version

### Dependencies and data

#### Creating a virtual environment

Ensure your pip (package manager) is up to date:

    pip3 install --upgrade pip

To check your pip version run:

    pip3 --version


Create the virtual environment in the root of the cloned project:

    python3 -m venv .venv

#### Activating the newly created virtual environment

You always want your virtual environment to be active when working on this project.

    source ./.venv/bin/activate

If you are using Windows, you will need:

    .venv\Scripts\activate.bat

#### Installing Python requirements

This will install some of the packages you might find useful:

    pip3 install -r ./requirements.txt

#### Generating the data

A data generator is included as part of the project in `./input_data_generator/main_data_generator.py`
This allows you to generate a configurable number of months of data.

To run the data generator use:

    python3 ./input_data_generator/main_data_generator.py

This should produce customers, products and transaction data under `./input_data/starter`

#### Getting started

Please save any Snowflake code in `snowflake` as `.sql` files.

The task can be found [here](./TASK.md).
