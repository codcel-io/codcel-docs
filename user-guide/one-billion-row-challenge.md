<!--
Copyright (c) 2026 Codcel

Licensed under CC BY 4.0 or the Codcel Documentation License.
See LICENSING.md for details.
-->

# The One Billion Row Challenge

## Background

The One Billion Row Challenge (1BRC), created by Gunnar Morling, is a fun exploration of how far modern Java can be pushed for aggregating one billion rows from a text file.

The text file contains temperature values for a range of weather stations. Each row is one measurement in the format `<string: station name>;<double: measurement>`, with the measurement value having exactly one fractional digit. The following shows ten rows as an example:

    Hamburg;12.0
    Bulawayo;8.9
    Palembang;38.8
    St. John's;15.2
    Cracow;12.6
    Bridgetown;26.9
    Istanbul;6.2
    Roseau;34.4
    Conakry;31.2
    Istanbul;23.0

The task is to write a Java program which reads the file, calculates the min, mean, and max temperature value per weather station, and emits the results on stdout like this (i.e. sorted alphabetically by station name, and the result values per station in the format `<min>/<mean>/<max>`, rounded to one fractional digit):

    {Abha=-23.0/18.0/59.2, Abidjan=-16.2/26.0/67.3, Abéché=-10.0/29.4/69.0, Accra=-10.1/26.4/66.4, Addis Ababa=-23.7/16.0/67.0, Adelaide=-27.8/17.3/58.5, ...}

## Codcel

We thought it would be a good idea to test if Codcel could handle such a large table of one billion rows.
There is no reason why it shouldn't, but the proof is in the pudding!

We do not expect Codcel to have the performance of the best competition entries, because we have not written any
specific code just for this example. The Java code writers know the file and the data and can optimise for it, while Codcel is
a generic solution.

## Implementation

It was important that the text file was used as is, without any modifications such as sorting or improving the data to help speed up the processing.

The data in the file is completely mixed, so it is important for us to find out on such data how long it would take to find the min, max, and average for a town.

Some users may not optimise their tables, so this is a great example.

## Setting Up the Challenge in Codcel

1) Clone the repository:

    git clone https://github.com/gunnarmorling/1brc

2) Make sure Java 21 is installed and JAVA_HOME is set correctly.

A Mac with Temurin-21 would use the following JAVA_HOME setting:

    export JAVA_HOME=/Library/Java/JavaVirtualMachines/temurin-21.jdk/Contents/Home

3) Build the project using Apache Maven:

    ./mvnw clean verify

4) Create the measurements file with 1 billion rows:

    ./create_measurements.sh 1000000000

This will take some minutes. The generated file size is approx. 12 GB.

5) Rename the file to T_Measurements.csv and make sure the file is UTF-8.

6) Copy the file "T_Measurements.csv" to the directory "/test-excel-files" to the same location as "one-billion-rows.xlsx".

7) Create the Codcel project:

    ./calc-to-web.sh -p "one-billion-rows" -x "test-excel-files/one-billion-rows.xlsx" -c "test-excel-files/T_Measurements.csv"

8) Go to the generated server code "/generated/one-billion-rows/one-billion-rows-server" and execute:

    cargo run --release

## Testing

To test the application, perform this JSON RESTful POST:

URL:

    http://localhost:3030/combined

Body:

    {
        "town": "Miami"
    }

The response should be:

    {
        "min": -25.7,
        "average": 24.9,
        "max": 75.3
    }

This response took 8 seconds on a MacBook Pro with an M1 Pro processor. The second time it was called, it took 1.5 seconds, because there is caching for five minutes.

## Observations

The data is completely random and in reality it would probably be better to have separate tables for each town.
There are approximately 2.5 million data points for each town.