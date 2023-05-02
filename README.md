# Geocoder Evaluation

This project provides an evaluation framework for geocoding APIs with a focus on [Amazon Location Service](https://aws.amazon.com/location/). Amazon Location Service provides access to high-quality data from multiple data providers, giving you the flexibility to choose the provider with the best data quality for their project. However, selecting the most suitable data provider for a geocoding project can be challenging due to differences in data sources, data quality, and geocoding algorithms.

This project aims to help you select the best data provider for you geocoding project by providing quality metrics such as match rate, accuracy, and similarity to compare the quality of geocoding results by Esri and HERE. You can also use this framework to compare different geocoders using your own data.

## Prerequisites

To run this experiment, you will need access to an AWS account. [Create an AWS account](https://portal.aws.amazon.com/billing/signup?trk=f475171a-6e33-443e-a731-70b296aee356&sc_channel=el) if you do not have one already. Next, [create an IAM user](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-prereqs.html#getting-started-prereqs-iam) with sufficient permissions to call the [SearchPlaceIndexForText API](https://docs.aws.amazon.com/location/latest/APIReference/API_SearchPlaceIndexForText.html). Then, [create an access key ID and secret access key](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-prereqs.html#getting-started-prereqs-keys) for Command Line Interface (CLI) access.

You will also need access to a Jupyter Notebook environment, with Python 3.9, for geocoding addresses and analyzing the results.

Finally, you will need access to [Canada Post APIs](https://www.canadapost-postescanada.ca/ac/support/setup-guides/#create-an-api-key) to get Canada-post verified addresses, which you will use as the baseline for lexical accuracy evaluations.

It is important to note that you need to pay for what you use when calling Amazon Location Service and Canada Post APIs. Visit Amazon Location Service [pricing page](https://aws.amazon.com/location/pricing/) and Canada Post [pricing page](https://www.canadapost-postescanada.ca/ac/pricing/) to estimate the cost of this experiment.

## Create AWS resources

Head to the [Amazon Location Service page](https://console.aws.amazon.com/location/places/home) in the AWS Management Console and create two Amazon Location Service’s place index resources called `esri-geocoder` and `here-geocoder`, with Esri and HERE as data providers.

## Configure

Copy `.env.example` to `.env` and populate environment variables with your AWS access key and secret access key, AWS Region, and Canada Post API key.

## Geocode addresses

Open [collection.ipynb](collection.ipynb) and run the code to geocode the input addresses. Upon completion, the output will consist of nine CSV files that contain the geocoding results across three test scenarios.

## Analyze results

Open [analysis.ipynb](analysis.ipynb) and run the code to analyze the geocoding results. It will evaluate the performance of Esri and HERE geocoders across three test scenarios using match rate, and positional and lexical accuracy and similarity metrics.

## Get help

Have a bug to report? [Open an issue](https://github.com/mepa1363/geocoder-evaluation/issues/new). If possible, include details about your development environment, and an example that shows the issue.

## Licensing

This library is licensed under the MIT License. See [LICENSE](LICENSE).
