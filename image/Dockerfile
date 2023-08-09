FROM jupyter/tensorflow-notebook:lab-4.0.3

# Add a "USER root" statement followed by RUN statements to install system packages using apt-get,
# change file permissions, etc.
USER root
RUN apt-get update \
  && apt-get -y install tesseract-ocr \
  && rm -rf /var/lib/apt/lists/* \
  fix-permissions "${CONDA_DIR}" && \
  fix-permissions "/home/${NB_USER}"

# If you do switch to root, always be sure to add a "USER $NB_USER" command at the end of the
# file to ensure the image runs as a unprivileged user by default.
USER $NB_USER

# Add RUN statements to install packages as the $NB_USER defined in the base images.
RUN conda install --quiet --yes \
    'opencv-contrib-python' \
    'pytesseract' \
    'Pillow' && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"