# AI-powered Auction Vehicle Damage Evaluator

Source code for post, [Image Identification and Classification with Amazon Bedrock, OpenSearch, and OpenCLIP](https://garystafford.medium.com/image-identification-and-classification-with-amazon-bedrock-opensearch-and-openclip-5442baca1846). Build a generative AI-powered vehicle damage assessment application on AWS using Vector Engine for Amazon OpenSearch Serverless, AI21 Labs Foundation Models, and OpenCLIP. Read the blog post for complete instructions. A video demonstration of the application is available on [YouTube](https://youtu.be/vkouFozFSvE?si=Rot0JVXZ2OMtPN_0).

__NOTE:__ The vehicle image datasets are not included. You will need to download your choice of datasets and create embeddings. The damaged vehicle image database can be found on Roboflow Universe > CarDamagedDetection2 > Car-Damage-Type-Detection-End-Game: [Car-Damage-Type-Detection-End-Game Computer Vision Project](https://universe.roboflow.com/cardamageddetection2/car-damage-type-detection-end-game). The undamaged vehicle image dataset can be downloaded from Kaggle > [Undamaged Vehicle Image Dataset](https://www.kaggle.com/datasets/garystafford/undamaged-vehicle-image-dataset).

## Architecture

![Architecture](diagrams/Architecture_OpenCLIP_v2.png)

## Application Commands

```shell
# create virtual python environment
python3 -m pip install virtualenv
virtualenv car-damage
python3 -m venv car-damage
source car-damage/bin/activate

# install required packages
python3 -m pip install -r requirements.txt -Uq

# set your aws credentials in the terminal if running locally or in sagemaker studio
export AWS_ACCESS_KEY_ID=...
export AWS_SECRET_ACCESS_KEY=...
export AWS_SESSION_TOKEN=...

# start the streamlit app
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

## Example Prompt Template

```json
{
    "prompt": "Write a description of the vehicle in the style of a fast-talking auctioneer using all the following information. DO NOT include the vehicle's condition in the description!\n- Year, make, and model: 2021 BMW 330i\n- Body style: 4-door sedan, hardtop\n- drivetrain: rear-wheel drive\n- Engine-type: 2.00 liter, 4-cylinder, 255 horsepower, gasoline-powered\n- Transmission: 8-speed automatic\n- Additional options: HD Radio, Bluetooth, Satellite Radio, Auxiliary Audio Input, MP3 Player\n- exterior color: gray\n- Exterior color: Gray\n- Mileage: 57,550\n- Initial auction estimate: $34,560\n- Images showing damage: 3 of 3\n- Recommended devaluation due to damage: 93%\n- Adjusted auction estimate: $2,419\n",
    "maxTokens": 500,
    "temperature": 1.0,
    "stopSequences": []
}
```

## Example Generated Vehicle Description

```text
Ladies and gentlemen, we've got a great car for you here today - a 2021 BMW 330i! This 4-door sedan is a hardtop, with rear-wheel drive, a 2.00 liter, 4-cylinder engine with 255 horsepower, and an automatic transmission with 8 speeds. It's got some great options, including HD Radio, Bluetooth, Satellite Radio, Auxiliary Audio Input, and an MP3 player. The exterior is a beautiful gray, and it's got 57,550 miles on the odometer. The initial auction estimate is $34,560, but be sure to take a look at the images of the damage - they're going to recommend a devaluation of 93%, so we're going to adjust that to an auction estimate of $2,419. Happy bidding!
```

## Sample Vehicles

You can use the following vehicle's VIN, color, mileage, and price to try out the application.

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
Dealer link: https://www.mcgovernauto.com/exotic-used/BMW/2021-BMW-3+Series-058a86b80a0e0a945926c74ee94f5183.htm

VIN: 3MW5R7J01L8B16026
Description: Used 2020 BMW 330i xDrive Sedan
Color: Mineral Grey Metallic
Mileage: 26190
Price: USD 33499
Dealer link: https://www.vwpittsfield.com/used/BMW/2020-BMW-330i-b82ca94b0a0e094a74e2589da13cd025.htm
```

---
The contents of this repository represent my viewpoints and not of my past or current employers, including Amazon Web Services (AWS). All third-party libraries, modules, plugins, and SDKs are the property of their respective owners.
