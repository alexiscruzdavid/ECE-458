# ECE-458
ECE 458 Project 




## Deployment strategy:



### Docker Configuration

1. Use separate containers for Django backend, React frontend, and Nginx:
   - Django container running Gunicorn
   - React container to build static files
   - Nginx container as reverse proxy

2. Use Docker Compose to orchestrate the containers:
   - Define services for Django, React, Nginx, and database (e.g. PostgreSQL)
   - Use volumes to persist data and share files between containers

3. Include Nginx in your Docker setup:
   - Nginx container should handle SSL termination
   - Serve static files for React frontend
   - Proxy requests to Django backend

## GitHub Actions Workflow

1. Create a CI/CD pipeline using GitHub Actions:
   - Build Docker images for Django and React
   - Run tests
   - Push images to a container registry (e.g. Docker Hub, GitHub Container Registry)
   - Deploy to production server

2. Use environment secrets in GitHub to store sensitive information:
   - Database credentials
   - API keys
   - Deployment SSH keys

## SSL Certificates

1. Use Let's Encrypt with Certbot for free SSL certificates:
   - Add a Certbot container to your Docker Compose file
   - Use volumes to share certificates with Nginx container

2. Automate certificate renewal:
   - Set up a cron job or scheduled GitHub Action to renew certificates

3. For local development:
   - Use tools like mkcert to generate locally-trusted certificates

## Deployment Best Practices

1. Use a reverse proxy like Nginx:
   - Handle SSL termination
   - Serve static files
   - Load balancing (if using multiple backend instances)

2. Separate development and production configurations:
   - Use different Docker Compose files for dev and prod
   - Override environment variables as needed

3. Use environment variables for configuration:
   - Store sensitive information in .env files (not in version control)
   - Pass environment variables to containers

4. Implement health checks:
   - Add health check endpoints to your Django application
   - Configure Docker health checks

5. Set up monitoring and logging:
   - Use tools like Prometheus and Grafana for monitoring
   - Implement centralized logging (e.g. ELK stack)



Citations:
[1] https://www.reddit.com/r/django/comments/w4zrab/running_django_in_a_github_action_so_that_its/
[2] https://www.youtube.com/watch?v=QHCsaG9dLI4
[3] https://saasitive.com/tutorial/docker-compose-django-react-nginx-let-s-encrypt/
[4] https://www.youtube.com/watch?v=3_ZJWlf25bY
[5] https://www.youtube.com/watch?v=aclMmsconNE
[6] https://testdriven.io/blog/deploying-django-to-linode-with-docker-and-github-actions/
[7] https://testdriven.io/blog/django-lets-encrypt/
[8] https://dev.to/koladev/build-and-deploy-your-django-react-app-authentication-docker-aws-lightsail-github-actions-postgresql-14kl
[9] https://github.com/app-generator/sample-docker-django-react/actions
[10] https://stackoverflow.com/questions/70727887/deploy-a-django-application-on-azure-vm-using-github-actions
[11] https://www.reddit.com/r/reactjs/comments/m9zfzf/i_wrote_a_guide_to_help_you_deploy_a_react_app/
[12] https://betterstack.com/community/guides/scaling-python/dockerize-django/
[13] https://stackoverflow.com/questions/64532293/python-django-project-handling-env-and-secret-key-on-github-actions-kubernete
[14] https://www.linkedin.com/pulse/automate-your-django-deployment-github-actions-docker-muhammad-rashid-9gfif
[15] https://blog.cloudsigma.com/how-to-secure-and-scale-a-django-application-with-docker-nginx-and-lets-encrypt/
[16] https://codeburst.io/serve-react-apps-with-docker-and-ssl-like-a-boss-e2d6d18553b7?gi=b6ea9ec6a8db
[17] https://www.reddit.com/r/nginx/comments/uaer9o/cant_send_http_request_from_react_to_django_using/
[18] https://www.reddit.com/r/django/comments/19f5uep/getting_https_for_django_project_running_in_docker/
[19] https://stackoverflow.com/questions/76578594/how-to-configure-ssl-certificate-inside-my-docker-container
[20] https://www.reddit.com/r/django/comments/jngtys/is_it_possiblerecommended_to_deploy_django_app/
[21] https://www.youtube.com/watch?v=e63EBEFJkH0
[22] https://www.reddit.com/r/django/comments/qmet93/do_i_need_to_use_nginx_when_hosting_django_docker/
[23] https://stackoverflow.com/questions/65141036/deploy-react-and-django-with-nginx-and-docker
[24] https://forums.docker.com/t/react-django-postgres/136637
[25] https://www.reddit.com/r/django/comments/jg5x7k/django_react_project_structure_w_docker/
[26] https://github.com/felipelm/django-nginx-reactjs-docker
[27] https://stackoverflow.com/questions/75806393/ssl-certificate-for-react-app-in-nginx-docker-container
[28] https://saasitive.com/tutorial/docker-compose-django-react-nginx-let-s-encrypt/
[29] https://www.digitalocean.com/community/tutorials/how-to-scale-and-secure-a-django-application-with-docker-nginx-and-let-s-encrypt
[30] https://serverfault.com/questions/981378/how-can-i-add-ssl-certificates-to-nginx-inside-a-docker-container
[31] https://www.tunecrew.com/2019/01/13/https-for-local-development-with-react-django-uwsgi-docker/