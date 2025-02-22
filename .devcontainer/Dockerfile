FROM mcr.microsoft.com/devcontainers/anaconda:1-3

# Copy environment.yml (if found) to a temp location so we update the environment. Also
# copy "noop.txt" so the COPY instruction does not fail if no environment.yml exists.
COPY environment.yml* .devcontainer/noop.txt /tmp/conda-tmp/
RUN if [ -f "/tmp/conda-tmp/environment.yml" ]; then umask 0002 && /opt/conda/bin/conda env update -n base -f /tmp/conda-tmp/environment.yml; fi \
    && rm -rf /tmp/conda-tmp

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends openjdk-17-jdk \
    && conda install -y numpy pandas matplotlib seaborn pyspark

# [Optional] Uncomment this section to install XGBoost.
RUN conda install -y xgboost

# [Optional] Uncomment this section to install file sync and jupyter debug kernel.
# RUN conda install -y jupytext ipykernel

# [Optional] Uncomment this section to install minimal latex for PDF export.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends texlive-xetex \
#     texlive-fonts-recommended texlive-plain-generic \
#     && conda install -y nbconvert pandoc