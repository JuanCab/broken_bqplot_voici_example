# Illustration of Broken bqplot in Voici

This repo contains a sample jupyter notebook that illustrates a simple interactive plot generated with bqplot that functions correctly in [Jupyter lab](https://jupyter.org) or [Voila](https://github.com/voila-dashboards/voila), but does not render properly in [Voici](https://github.com/voila-dashboards/voici).

## Setup
You can create (roughly) the same environment I have tested this in using conda and running

`conda env create -f environment.yml`

to create a `test_bqplot_voici` environment.   

## Test notebook in Voila environment

Then to test this notebook in Voila, you can from the command line

```bash
conda activate test_bqplot_voici
voila voici_project/webapp/index.ipynb
```

Your web browser should launch and the test notebook should be running on it.  You will notice you can drag the individual points in the plot and the line connecting them should get updated to continue to connect the points.

## Test notebook in Voici environment

You can test the generation of a Voici static app from this same directory using the following commands on the command line:
```bash
conda activate test_bqplot_voici
cd voici_project/
voici build --contents webapp
```
Once you have generated the `_output` directory, serve it using 
```bash
python -m http.server 8000 --directory _output
```
and open the [http://localhost:8000](http://localhost:8000) site in a web browser.  The `index.ipynb` will run, but you should see that the background line connecting the points does **NOT** update when the scatter points are dragged.