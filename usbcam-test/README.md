# Testing USB Camera from Docker
This is a simple, no-frills approach to check that Docker has access to your USB camera. It simply loads up the [Motion](https://motion-project.github.io) application, and shows you your camera feed. After running, go to [localhost:8080](http://localhost:8080) or whichever host you are running on. You can also check the `output` folder for images and video files.

## Docker build
```bash
docker build -t usbcam-test .
```

## Docker run
```bash
docker run --rm -it --privileged -v $PWD/motion.conf:/etc/motion/motion.conf  -v /dev/video0:/dev/video0 -v $PWD/output:/var/lib/motion -p 8080:8080 -p 8081:8081 usbcam-test motion -n
```
