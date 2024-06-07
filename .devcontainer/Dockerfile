# Use whatever base image is required for your project
FROM hcp4715/hddm:1.0.1

# Any other setup like setting up your environment, installing tools, etc.
RUN pip install \
    git+https://github.com/ruffgroup/bauer.git@refactor#egg=bauer

    RUN pip install --no-cache-dir notebook ipykernel && \
    python -m ipykernel install --sys-prefix --name python3 --display-name "Python 3"

ENTRYPOINT ["/bin/bash", "-c"]
CMD ["sleep", "infinity"]

USER root

# Create workspace and notebooks directories
RUN mkdir -p /workspace/notebooks && \
    chown $NB_UID:$NB_GID /workspace/notebooks && \
    chmod 777 /workspace/notebooks
RUN mkdir -p /workspace/notebooks && \
    chown $NB_UID:$NB_GID /workspace/notebooks && \
    chmod 777 /workspace/notebooks

# Switch back to the jovyan (or non-root) user if necessary
USER $NB_UID

# Set the working directory to notebooks
WORKDIR /workspace/notebooks