# Image analysis templates

Jupyter notebooks for repeatable image-analysis workflows in [napari](https://napari.org/) and [Fiji](https://fiji.sc/). The notebooks are intended to run in the [image-analysis environment](https://github.com/gabnasello/image-analysis-env), which provides Jupyter together with a browser-based Linux desktop for GUI applications.

## Repository layout

- [`napari/`](napari/): notebooks for image analysis with napari and Python.
- [`fiji/`](fiji/): notebooks for image analysis with Fiji/ImageJ.

## Run in the cloud with Binder

The environment can be launched in Binder using its Desktop interface:

[![Launch image-analysis environment in Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/gabnasello/image-analysis-env/main?urlpath=desktop)

1. Open the Binder link and wait for the Jupyter session to start. Startup can take several minutes.
2. In the Jupyter launcher, open the **Desktop** tile. This starts the remote XFCE desktop used by napari and Fiji.
3. Open a Jupyter **Terminal** and clone this repository into the session:

	 ```bash
	 git clone https://github.com/gabnasello/image-analysis-templates.git
	 ```

4. In the Jupyter file browser, navigate to `image-analysis-templates/napari/` or `image-analysis-templates/fiji/`.
5. Right-click a notebook and choose **Open With -> Notebook**.
6. Run the notebook cells from top to bottom. Keep the Desktop tab open when a cell starts napari or another GUI application; the application window will appear there.

The first Desktop connection can occasionally fail. Close the Desktop tab and open the **Desktop** tile again.

## Run locally with Docker

Clone the environment repository and build its image:

```bash
git clone https://github.com/gabnasello/image-analysis-env.git
cd image-analysis_env
docker build -t image-analysis-env .
```

Start the container from the environment repository and mount this repository as a working directory. Replace `/path/to/image-analysis-templates` with the local path to this checkout:

```bash
docker run --rm \
	--security-opt seccomp=unconfined \
	-p 8888:8888 \
	-v /path/to/image-analysis-templates:/home/jovyan/work \
	image-analysis-env
```

Open the Jupyter URL printed in the terminal, select **Desktop**, and use the mounted `work` directory to open the notebooks. The `seccomp=unconfined` option is required by the remote desktop services used by the container.

## Working with the notebooks

- Check each notebook's input paths and parameters before running the analysis.
- Run setup and import cells before analysis cells.
- Use the Jupyter kernel for Python processing and the Desktop tab for napari or Fiji windows.
- Save generated results outside the temporary Binder session when working in the cloud.

## References

- [image-analysis environment](https://github.com/gabnasello/image-analysis-env)
- [Launching Binder with a napari Desktop](https://napari.org/napari-workshop-template/docs/launching_binder.html)
