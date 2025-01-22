# Use CARLA version 0.9.15
FROM carlasim/carla:0.9.15

# Expose CARLA's default ports for communication
EXPOSE 2000-2002

# Optional: Add a volume mount for persistent data or configs
VOLUME ["/home/carla/config"]

# Default command to start the CARLA server
CMD ["/bin/bash", "/home/carla/CarlaUE4.sh", "-opengl"]