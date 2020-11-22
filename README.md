## Text to Speech Service
A text-to-speech service implementation with predictive,dynamic load balancing

**- Under development -**

### Setup/Requirements
1. Activating the environment

    For the worker nodes

        python3 -m venv workerenv
        source environments/workerenv/bin/activate
        pip install -r worker_requirements.txt

    For the master node
    
        python3 -m venv masterenv
        source environments/masterenv/bin/activate
        pip install -r master_requirements.txt
    to leave an environment, run

        deactivate

2. Nginx

        sudo apt install nginx

To start the master node server, run

    gunicorn --bind 0.0.0.0:5000 master:app


### Testing
To test a request make a POST request to `localhost:5000/getspeech` with POST data as a JSON object looking like this

    {
        "text_message" : "This is text to be converted to speech"
    }
The request should get proxied to one of the worker servers and you can which in the response