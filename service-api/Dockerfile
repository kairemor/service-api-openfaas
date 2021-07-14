# Import the OpenFaaS of-watchdog
FROM openfaas/of-watchdog:0.7.2 as watchdog

# Add a FROM line from your existing image
FROM kairemor/service-api:1.0

# Let's say that the image listens on port 3000 and
# that we can't change that easily
ENV PORT 3000

# Install the watchdog from the base image
COPY --from=watchdog /fwatchdog /usr/bin/

# Now set the watchdog as the start-up process
# Along with the HTTP mode, and an upstream URL to
# where your HTTP server will be running from the original
# image.
ENV mode="http"
ENV upstream_url="http://127.0.0.1:3000"

# Set fprocess to the value you have in your base image
ENV fprocess="node index.js"
CMD ["fwatchdog"]
