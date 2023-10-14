# AI-powered Auction Vehicle Damage Evaluator

Source code for post, [Image Identification and Classification with Amazon Bedrock, OpenSearch, and OpenCLIP](https://garystafford.medium.com/image-identification-and-classification-with-amazon-bedrock-opensearch-and-openclip-5442baca1846). Build a generative AI-powered vehicle damage assessment application on AWS using Vector Engine for Amazon OpenSearch Serverless, AI21 Labs Foundation Models, and OpenCLIP.

## Commands

```shell
python3 -m pip install virtualenv
virtualenv car-damage
python3 -m venv car-damage
source car-damage/bin/activate

python3 -m pip install -r requirements.txt -Uq

# set your aws credentials in the terminal if running locally or sagemaker studio
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
export AWS_SESSION_TOKEN=...

streamlit run app.py \
    --server.runOnSave true \
    --theme.base "light" \
    --theme.backgroundColor "#ffffff" \
    --theme.primaryColor "#1455ba" \
    --theme.secondaryBackgroundColor "#e8e8e8" \
    --theme.font "sans serif"\
    --ui.hideTopBar "true" \
    --client.toolbarMode "minimal"
```

## Sample Vehicle VINs

Using the National Highway Traffic Safety Administration (NHTSA) vPIC API.

```txt
VIN: 3MW5R1J00M8C08095
Description: Used 2021 BMW 3 Series 330i
Color: Mineral White Metallic
Mileage: 42255 miles
Price: USD 27399
Dealer link: https://www.hannaimports.com/used/BMW/2021-BMW-330i-raleigh-nc-c4666a370a0e0a9335458373f144b656.htm

VIN: 3MW5P9J08M8B97822
Description: Used 2021 BMW 3 Series 330e xDrive 2.0L 4-Cylinder 8-Speed Automatic Sport AWD
Color: Mineral Grey Metallic
Mileage: 54001
Price: USD 34433
https://www.mcgovernauto.com/exotic-used/BMW/2021-BMW-3+Series-058a86b80a0e0a945926c74ee94f5183.htm

VIN: 3MW5R7J01L8B16026
Description: Used 2020 BMW 330i xDrive Sedan
Color: Mineral Grey Metallic
Mileage: 26190
Price: USD 33499
Dealer link: https://www.vwpittsfield.com/used/BMW/2020-BMW-330i-b82ca94b0a0e094a74e2589da13cd025.htm
```
