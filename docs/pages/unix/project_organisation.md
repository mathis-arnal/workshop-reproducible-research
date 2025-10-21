## Project organization and management

Most of the the project organization material can be found at <https://software-carpentry.org> and <http://www.datacarpentry.org>

Many thanks to them for existing!

### Structure or architecture of a data science project


Some good practice when you will organise your project directory on the server, on the cloud or any other machine where you will compute:

> Create 3 or 4 different directories within you project directory (use `mkdir`):
>
> `data/` for keeping the raw data
>
> `results/` for all the outputs from the multiple analyses that you will perform
>
> `docs/` for all the notes written about the analyses carried out (ex: `history > 20221114.logs` for the commands executed today)
>
> `scripts/` for all the scripts that you will use to produce the results
>


!!! note
    You should always have the raw data in (at least) one place and not modify them

### More about data structure and metadata

* direct link to the tutorial used fo the lesson: [Shell genomics: project organisation](http://www.datacarpentry.org/shell-genomics/06-organization/)

* good practice for the structure of data and metadata of a genomics project: [Organisation of genomics project](http://www.datacarpentry.org/organization-genomics/)

* Some extra material: [Spreadsheet ecology lesson](http://www.datacarpentry.org/spreadsheet-ecology-lesson/)

## Exercise

This exercise combines the knowledge you have acquired during the [unix](unix) and [project organisation](project_org) lessons.

You have designed an experiment where you are studying the species and weight of animals caught in plots in a study area.
Data was collected by a third party a deposited in [figshare](https://figshare.com/articles/Portal_Project_Teaching_Database/1314459), a public database.

Our goals are to download and exploring the data, while keeping an organised project directory

### Set up

First we go to our working directory for this training and create a project directory

```bash
cd ~/bioinfo_training
mkdir animals
cd animals
```

As we saw during the project organization tutorial, it is good practice to separate data, results and scripts.
Let us create those three directories

```bash
mkdir data results scripts
```

### Downloading the data

First we go to our `data` directory

```bash
cd data
```

then we download our data file and give it a more appropriate name

```bash
wget https://ndownloader.figshare.com/files/2292169
mv 2292169 data_joined.csv
```

Since we'll never modify our raw data file (or at least we *do not want to!*) it is safer to remove the writing permissions

```bash
chmod -w data_joined.csv
ls -l
```

!!! note
    what if my data is really big?
    Usually when you download data that is several gigabytes large, they will usually be compressed.
    You learnt about compression during the [installing software](software) lesson.

Let us look at the first few lines of our file:

```bash
cd ..
head data/data_joined.csv
```

Our data file is a `.csv` file, that is a file where fields are separated by commas `,`.
Each row represent an animal that was caught in a plot, and each column contains information about that animal.

!!! question
    How many animals do we have?

```bash
wc -l data/data_joined.csv
# 34787 data/data_joined.csv
```

It seems that our dataset contains 34787 lines.
Since each line is an animals, we caught a grand total of 34787 animals over the course of our study.

