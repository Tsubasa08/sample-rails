FROM --platform=linux/x86_64 ruby:3.1.2-slim
RUN apt-get update && \
  apt-get install -y --no-install-suggests --no-install-recommends \
  build-essential \
  libpq-dev \
  libmariadb-dev

WORKDIR /app
COPY . /app
# COPY Gemfile /app/Gemfile
# COPY Gemfile.lock /app/Gemfile.lock
RUN gem update --system && gem install bundler:2.3.4
RUN bundle install

# Add a script to be executed every time the container starts.
COPY docker/rails/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 3000

# Configure the main process to run when running the image
CMD ["rails", "server", "-b", "0.0.0.0"]
