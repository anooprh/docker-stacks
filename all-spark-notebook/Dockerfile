# Copyright (c) Jupyter Development Team.
# Distributed under the terms of the Modified BSD License.
FROM jupyter/pyspark-notebook

MAINTAINER Jupyter Project <jupyter@googlegroups.com>

USER root

# RSpark config
ENV R_LIBS_USER $SPARK_HOME/R/lib

# R pre-requisites
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    fonts-dejavu \
    gfortran \
    gcc && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

USER $NB_USER

# R packages
RUN conda install --quiet --yes \
    'r-base=3.3.2' \
    'r-irkernel=0.7*' \
    'r-ggplot2=2.2*' \
    'r-sparklyr=0.5*' \
    'r-rcurl=1.95*' && conda clean -tipsy

# Apache Toree kernel
RUN pip --no-cache-dir install https://dist.apache.org/repos/dist/dev/incubator/toree/0.2.0/snapshots/dev1/toree-pip/toree-0.2.0.dev1.tar.gz
RUN jupyter toree install --sys-prefix

# Spylon-kernel
RUN conda install --quiet --yes 'spylon-kernel=0.4*' && \
    conda clean -tipsy
RUN python -m spylon_kernel install --sys-prefix

# install jupyter extensions
RUN conda install --quiet --yes -c conda-forge jupyter_contrib_nbextensions
RUN conda install --quiet --yes -c conda-forge jupyter_nbextensions_configurator

# Install Python 3 Tensorflow
RUN conda install --quiet --yes 'tensorflow=1.0*'

# Install Python 2 Tensorflow
RUN conda install --quiet --yes -n python2 'tensorflow=1.0*'

# Enable common extensions
RUN jupyter nbextension enable toc2/main
RUN jupyter nbextension enable varInspector/main
RUN jupyter nbextension enable search-replace/main
RUN jupyter nbextension enable navigation-hotkeys/main
RUN jupyter nbextension enable keyboard_shortcut_editor/main
RUN jupyter nbextension enable exercise2/main
RUN jupyter nbextension enable dragdrop/main
RUN jupyter nbextension enable collapsible_headings/main
RUN jupyter nbextension enable autosavetime/main
RUN jupyter nbextension enable latex_envs/latex_envs
RUN jupyter nbextension enable zenmode/main
RUN jupyter nbextension enable table_beautifier/main
RUN jupyter nbextension enable runtools/main
RUN jupyter nbextension enable printview/main
RUN jupyter nbextension enable hinterland/hinterland
RUN jupyter nbextension enable comment-uncomment/main
RUN jupyter nbextension enable autoscroll/main
RUN jupyter nbextension enable addbefore/main
RUN jupyter nbextension enable chrome-clipboard/main
RUN jupyter nbextension enable limit_output/main
RUN jupyter nbextension enable scratchpad/main
RUN jupyter nbextension enable spellchecker/main
RUN jupyter nbextension enable toggle_all_line_numbers/main
RUN jupyter nbextension enable code_font_size/code_font_size
RUN jupyter nbextension enable help_panel/help_panel
RUN jupyter nbextension enable move_selected_cells/main
RUN jupyter nbextension enable rubberband/main
RUN jupyter nbextension enable scroll_down/main
RUN jupyter nbextension enable skip-traceback/main
RUN jupyter nbextension enable splitcell/splitcell
RUN jupyter nbextension enable tree-filter/index
